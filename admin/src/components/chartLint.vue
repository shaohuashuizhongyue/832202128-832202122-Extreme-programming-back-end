<template>
    <div id="echart-line" :style="{width: '100%', height: '100%'}"></div>
</template>

<script>

    import echarts from  "echarts";

    export default {

        methods:{

            initChart(name,xData,yData) {
                let _this = this;

                let getchart = _this.echarts.init(document.getElementById('echart-line'));
                var  option = {
                    tooltip: {
                        trigger: 'axis'
                    },
                    legend: {
                        data: [name],
                        bottom:'0%'
                    },
                    grid: { //调整图表上下左右位置
                        top:'10%',
                        left: '3%',
                        right: '8%',
                        bottom: '11%',
                        containLabel: true
                    },

                    xAxis: {
                        type: 'category',
                        boundaryGap: false,
                        data: xData
                    },
                    yAxis: {
                        type: 'value'
                    },
                    series: [
                        {
                            name: name,
                            type: 'line',
                            stack: '总量',
                            data: yData
                        },
                    ]
                };

                getchart.setOption(option);
                //随着屏幕大小调节图表
                window.addEventListener("resize", () => {
                    getchart.resize();
                });
            },

        }

    }
</script>
