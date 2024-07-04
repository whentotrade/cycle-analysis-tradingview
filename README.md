# cycle-analysis-tradingview
This is a abstract and framework proposal for the deep integration of state-of-the art cycle analysis in TradingView.
> For discussion in TV telegram channels.

## Personal background
I am Lars von Thienen, residing in Hamburg, Germany. Since earning my economics and engineering degree in 1997, I have focused on developing digital signal processing analysis frameworks for financial time series. Over the past 20 years, I have worked with and coded for numerous charting platforms. I have deep expertise in cycle analysis, cycle detection, and cycle forecasting for financial time series. In 2010, I wrote two books on cycle analysis and developed my own charting application with integrated cycle analysis capabilities. In 2019, I transferred my cycle algorithms into a highly scalable, cloud-based API engine. Currently, I am a board member of the non-profit Foundation for the Study of Cycles, which now provides these analytical tools.

## Why I am writing this?
All charting applications have their limitations when it comes to coding and visualization. Cycle analysis requires specific calculations that cannot be easily integrated into any script language, including Pine. Additionally, before you can utilize cycles, you need specialized visualizations, which can be challenging to implement with basic scripts. To address these challenges, I have divided my cycle analysis architecture into two components: 1) The cycle analysis engine, which leverages fully API-based technology and offers lightning-fast response times of under 20 milliseconds per call. 2) The front-end, where users can select a financial asset, apply the API in the backend, and make decisions based on cycle predictions displayed on the price chart. For both of these reasons, I have selected a combination of a lightweight charting library for publishing and an advanced private charting library. This architecture serves as the foundation for the Foundation for the Study of Cycles and its members (www.cycles.org). However, given that TradingView is the best available charting engine and user interface, instead of building this separately using the TradingView libraries, the optimal approach would be to have direct integration with the TradingView frontend. Consequently, I will work on developing a framework and ideas to facilitate this integration. If there is interest, we can move forward with this collaborative effort.

Let me give a quick intro about how our current implementation looks and works:

## Background and quick start

The first step is to run our sophisticated cycle analysis algorithms on a price series. The interface displays the dataset in the upper-left corner. We utilize a public "lightweight" charting library and have added numerous features to allow selecting the start and end points on the chart for the analysis. The results from the cycle analysis are presented as a spectrum plot at the bottom and a table on the left.
<img width="1256" alt="image" src="https://github.com/whentotrade/cycle-analysis-tradingview/assets/30272473/8056e489-ab46-435e-a317-ba5397046738">

The screenshot displays the user selecting two cycles, which are then combined into a composite cycle model and plotted as an overlay on the chart. This composite cycle plot also includes a prediction curve extending into the future. Once the user is satisfied with the selected cycle model, it is saved as a new data series in the database. The user then switches to the advanced private charting library, where they can pull up the price series and the newly created composite model to overlay on the same chart. This allows access to the charting library's full range of features.

The following illustration demonstrates the use of the private advanced charting library. We incorporate the previously created composite cycle model as a separate data series and overlay it on the S&P 500 daily data. This allows us to leverage additional specialized indicators and basic charting functions.
<img width="1262" alt="image" src="https://github.com/whentotrade/cycle-analysis-tradingview/assets/30272473/251ef6e8-fc35-47b0-8e7b-cd956678fb61">

If there is more interest, I am happy to share more information on the use cases and can also record a video to showcase the details. I am happy to give everyone access to this cycle analysis platform if you want to elaborate how to better integrate this with TV directly. Just let me know (via TV discord channels)

## Current issues and challanges
1) The complex digital signal processing algorithms used in the cycle analysis cannot be easily implemented in Pine Script. They require more advanced coding.

2) Running the cycle analysis functions on a cloud-based API allows for independent scaling and execution of the cycle analysis without interfering with the charting functionality. Additionally, it helps secure the intellectual property by keeping the source code separate, rather than exposing it directly on the TradingView platform.

3) The results of the cycle analysis need to be presented to the user in a dedicated visualization, such as a spectrum plot with additional information per cycle. This specialized visualization is not currently available within the TradingView/Pine environment.

4) The key output of the cycle analysis is the identification and selection of the dominant cycle, which is then used to create a forecasting and prediction model. This model is then saved as a new data series, but there is currently no way to directly load and use this custom data series within TradingView.

5) The ability to plot into the future is limited in TradingView/Pine, and the workarounds using "shifting" are not satisfactory. A more robust solution is needed to plot the cycle or cycle composite model into the future on the chart.

These are just some first limitations and challanges which would require attention and solution propisals to have a better integration of cycle analysis into TradingView.

## Possible solutions & architecture proposals

A) The existing Pine v5 environment does not provide the capability to implement the sophisticated digital signal processing algorithms required for comprehensive cycle analysis. A potential solution would be to enable the integration of cloud-based API endpoints that can execute the cycle calculations and return the results directly to the TradingView/Pine platform. Alternatively, a "certified" Pine library could be developed to facilitate the interaction with validated cycle analysis API endpoints.

B) Effectively visualizing the output of the cycle analysis, such as the spectrum plot and the cycles table, presents a challenge. The cycles table could potentially be displayed using Pine-based table functions, while the spectrum plot may require workarounds, such as plotting it as an indicator. However, to accurately present these visualizations, the cycle analysis results must first be obtained from the API endpoints.

C) The selection and plotting of the composite cycle model, including the forecasting component, also poses difficulties. While the calculation of the composite model could be performed within Pine, once the cycle-related information (amplitude, phase, and length) is retrieved from the API, the ability to plot the model into the future remains limited. Relying on simple "shifting" techniques is not a satisfactory solution, as it introduces additional issues.

D) An alternative approach could be for the Foundation for the Study of Cycles to provide pre-built composite cycle models for various financial assets and timeframes. This would require integrating these cycle models as separate data series within the TradingView platform, potentially with the assistance of the PineSeeds project or by establishing the Foundation as a "data provider" partner. This could offer a more streamlined solution for users to access and leverage the validated cycle models developed by the Foundation.




### Links and references:
FSC, Foundation for the Study of Cycles - www.cycles.org
Currently running our own UI to analyze financial assets on cycles on plot into the future. Using the public and private charting libraries provided by TradingView. It is a non-profit organization with a large membership.

Lars von Thienen, www.whentotrade.com
Two books on cycles available on Amazon, coding the backend cycle analysis engine https://api.cycle.tools/specs -> used from the front-end libraries to run the cycle analysis - this is written because not possible in pine

### Current pine scripts:
**Cycle Swing Momentum**
https://www.tradingview.com/script/b7o7GmWT-Cycle-Swing-Momentum/

**Cyclic Smoothed RSI**
https://www.tradingview.com/script/TmqiR1jp-RSI-cyclic-smoothed-v2/

**MTF cyclic smoothed RSI**
https://www.tradingview.com/script/xoFw4Q2F-Cyclic-Smoothed-RSI-MTF/


> For discussion in TV telegram channels.
