<template>
	<a-layout id="components-layout-demo-top" class="layout">
		<a-layout-header>
			<a-row>
				<a-col :span="2" :offset="4">
					<div class="logo"></div>
				</a-col>
				<a-col :span="8">
					<a-menu
							theme="dark"
							mode="horizontal"
							v-model:selectedKeys="selectedKeys"
							:style="{ lineHeight: '64px' }"
					>
						<a-menu-item key="value.key" v-for="value in list">
							{{value.name}}
						</a-menu-item>
					</a-menu>
				</a-col>
				<a-col :span="3">
					<a-input-search
							v-model:keyword="keyword"
							placeholder="搜索关键字"
							style="min-width: 120px"
							@search="onSearch"
					/>
				</a-col>
				<a-col :span="2" :offset="1">
					<a-space size="middle" align="center">
						<a-button type="primary">
							Primary
						</a-button>
						<a-button type="danger">
							danger
						</a-button>
					</a-space>
				</a-col>
			</a-row>
		</a-layout-header>
		<a-row>
			<a-col :span="10" :offset="4">
				<a-layout-content style="padding: 10px 5px">
					<div :style="{ background: '#fff', padding: '16px', minHeight: '800px' }">
						Content
					</div>
				</a-layout-content>
			</a-col>
			<a-col :span="6">
				<a-layout-content style="padding: 10px 5px">
					<div :style="{ background: '#fff', padding: '16px', minHeight: '800px' }">
						Content
					</div>
				</a-layout-content>
			</a-col>
		</a-row>
		<a-layout-footer style="text-align: center">
			Ant Design ©2018 Created by Ant UED
		</a-layout-footer>
	</a-layout>
</template>
<script>
    import {reactive, toRefs, ref} from "vue"

    export default {
        setup() {
            const selectedKeys = ['1']
            const menuList = reactive({
                list: handleList()
            })
			const keyword = ref(0)
			function onSearch(){
                return [keyword]
			}
            return {
                ...toRefs(menuList),
                selectedKeys,
                menuList,
				keyword,
				onSearch
            }

            function handleList() {
                const list = ['主题', '文章', '项目', '资源', '图书', 'go周刊', '下载', '官方文档']
                let arrayList = []
                for (const index in list) {
                    arrayList.push({
                        key: index.toString(),
                        name: list[index]
                    })
                }
                return arrayList
            }
        },
    };
</script>
<style scoped>
	#components-layout-demo-top .logo {
		width: 120px;
		height: 31px;
		background-image: url('./assets/logo.png');
		margin: 16px 24px 16px 0;
		float: left;
	}
</style>
