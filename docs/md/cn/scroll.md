## Scroll 无限滚动

### 概述
常用于滚动至底部时，触发加载更多数据。
### 底部触发
当滚动至底部时，触发加载更多。 需返回 Promise。

```
<template>
    <Scroll :on-reach-bottom="handleReachBottom">
        <Card dis-hover v-for="(item, index) in list1" :key="index" style="margin: 32px 0">
            Content {{ item }}
        </Card>
    </Scroll>
</template>
<script>
    export default {
        data () {
            return {
                list1: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
            }
        },
        methods: {
            handleReachBottom () {
                return new Promise(resolve => {
                    setTimeout(() => {
                        const last = this.list1[this.list1.length - 1];
                        for (let i = 1; i < 11; i++) {
                            this.list1.push(last + i);
                        }
                        resolve();
                    }, 2000);
                });
            }
        }
    }
</script>

```


<!--divider-->
### 顶部触发
当滚动至顶部时，触发加载更多。 需返回 Promise。

```
<template>
    <Scroll :on-reach-top="handleReachTop">
        <Card dis-hover v-for="(item, index) in list2" :key="index" style="margin: 32px 0">
            Content {{ item }}
        </Card>
    </Scroll>
</template>
<script>
    export default {
        data () {
            return {
                list2: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
            }
        },
        methods: {
            handleReachTop () {
                return new Promise(resolve => {
                    setTimeout(() => {
                        const first = this.list2[0];
                        for (let i = 1; i < 11; i++) {
                            this.list2.unshift(first - i);
                        }
                        resolve();
                    }, 2000);
                });
            }
        }
    }
</script>

```


<!--divider-->
### 边缘触发
当滚动至底部或顶部时，触发加载更多。 需返回 Promise。

```
<template>
    <Scroll :on-reach-edge="handleReachEdge">
        <Card dis-hover v-for="(item, index) in list3" :key="index" style="margin: 32px 0">
            Content {{ item }}
        </Card>
    </Scroll>
</template>
<script>
    export default {
        data () {
            return {
                list3: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
            }
        },
        methods: {
            handleReachEdge (dir) {
                return new Promise(resolve => {
                    setTimeout(() => {
                        if (dir > 0) {
                            const first = this.list3[0];
                            for (let i = 1; i < 11; i++) {
                                this.list3.unshift(first - i);
                            }
                        } else {
                            const last = this.list3[this.list3.length - 1];
                            for (let i = 1; i < 11; i++) {
                                this.list3.push(last + i);
                            }
                        }
                        resolve();
                    }, 2000);
                });
            }
        }
    }
</script>

```


<!--divider-->

### API



### Scroll props
<!--table-->
| 属性               | 说明                                       | 类型       | 默认值    |
| :--------------- | :--------------------------------------- | :------- | :----- |
| height           | 滚动区域的高度，单位像素                             | String   | Number |
| loading-text     | 加载中的文案                                   | String   | 加载中    |
| on-reach-top     | 滚动至顶部时触发，需返回 Promise                     | Function | -      |
| on-reach-bottom  | 滚动至底部时触发，需返回 Promise                     | Function | -      |
| on-reach-edge    | 滚动至顶部或底部时触发，需返回 Promise                  | Function | -      |
| distance-to-edge | 从边缘到触发回调的距离。如果是负的，回调将在到达边缘之前触发。值最好在 24 以下。 | Number   | Array  |
<!--table-->
<!--divider-->
