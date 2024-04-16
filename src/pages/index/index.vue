<template>
  <view class="content">
    <uni-section title="出入库查询喽" type="line">
			<uni-card :is-shadow="false">
       <button>今日入库></button> 
			</uni-card>
      <uni-card :is-shadow="false">
        <button>今日出库></button> 
			</uni-card>
		</uni-section>
    <uni-section title="操作" type="line" padding>
			<uni-grid :column="3" :show-border="false" :square="false" @change="change">
				<uni-grid-item v-for="(item ,index) in list" :index="index" :key="index">
					<view class="grid-item-box">
						<image class="image" :src="item.url" mode="aspectFill" />
						<text class="text">{{item.text}}</text>
						<view v-if="item.badge" class="grid-dot">
							<uni-badge :text="item.badge" :type="item.type" />
						</view>
					</view>
				</uni-grid-item>
			</uni-grid>
		</uni-section>
    <view class="text-area">
      <text class="title">{{ title }}</text>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      dynamicList: [],
				list: [{
						url: '/static/logo.png',
						text: 'Grid 1',
						badge: '0',
						type: "primary"
					},
					{
						url: '/static/logo.png',
						text: 'Grid 2',
						badge: '1',
						type: "success"
					},
					{
						url: '/static/logo.png',
						text: 'Grid 3',
						badge: '99',
						type: "warning"
					},
					{
						url: '/static/logo.png',
						text: 'Grid 4',
						badge: '2',
						type: "error"
					},
					{
						url: '/static/logo.png',
						text: 'Grid 5'
					},
					{
						url: '/static/logo.png',
						text: 'Grid 6'
					},
					{
						url: '/static/logo.png',
						text: 'Grid 7'
					},
					{
						url: '/static/logo.png',
						text: 'Grid 8'
					},
					{
						url: '/static/logo.png',
						text: 'Grid 9'
					}
				]

    }
  },
  onLoad() {},
  methods: {
    change(e) {
				let {
					index
				} = e.detail
				this.list[index].badge && this.list[index].badge++

				uni.showToast({
					title: `点击第${index+1}个宫格`,
					icon: 'none'
				})
			},
  },
}
</script>

<style lang="scss">
	.image {
		width: 25px;
		height: 25px;
	}

	.text {
		font-size: 14px;
		margin-top: 5px;
	}

	.grid-dot {
		position: absolute;
		top: 5px;
		right: 15px;
	}

	.swiper {
		height: 420px;
	}

	/* #ifdef H5 */
	@media screen and (min-width: 768px) and (max-width: 1425px) {
		.swiper {
			height: 630px;
		}
	}

	@media screen and (min-width: 1425px) {
		.swiper {
			height: 830px;
		}
	}

	/* #endif */
</style>


