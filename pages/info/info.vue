<template>
	<view class="content">
		<view class="art-content">
			<rich-text class="richTest" :nodes="strings"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				strings: ''
			}
		},
		onLoad:function(e){
			uni.request({
				url: 'https://news-at.zhihu.com/api/4/news/'+e.id,
				method: 'GET',
				data: {},
				success: res => {
					this.strings = res.data.body;
					this.strings = this.strings.replace(/“/g, '"');
					this.strings = this.strings.replace(/”/g, '"');
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>

</style>
