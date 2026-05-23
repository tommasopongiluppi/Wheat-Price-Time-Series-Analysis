A time series study of the global price of wheat (USD per metric ton), using ~34 years of monthly IMF data sourced from FRED, spanning January 1990 to May 2023. The project pairs a historical narrative of the major price drivers — the 2008 financial crisis, the COVID-19 pandemic, and the 2022 Russian invasion of Ukraine (which pushed prices to an all-time high of $444) — with a full Box–Jenkins modeling workflow in R.
The analysis proceeds through:

Stationarity transformation — a logarithmic transform to dampen the upward trend, followed by first-order differencing; the Augmented Dickey-Fuller test confirms stationarity (statistic = −7.598, p < 0.01).
Correlation diagnostics — ACF and PACF plots reveal a dominant autoregressive component alongside a moving-average term, ruling out a pure AR or MA process.
Seasonality assessment — annual (lag 12) and quarterly (lag 4) differences are compared against the monthly difference via standard deviation, range, skewness, and kurtosis; the monthly difference is preferred, and no dominant seasonal component is found.
Model estimation — iterative ARIMA simulations across multiple seeds converge on an ARIMA(2,0,1) specification (φ₁ = −0.7, φ₂ = 0.2, θ = 1), validated by matching ACF/PACF behaviour.
Spectral analysis — Spectral Density Functions (the Fourier transform of the autocovariance) of the observed, differenced, and simulated series are compared in the frequency domain, reinforcing stationarity and revealing concentrated low-frequency variability.
Robustness check — the series is re-examined with the 2008 and 2022 peaks removed, exhibiting stronger stationarity and confirming those events as the main volatility drivers.

Tools: R (tseries, forecast, moments). Co-authored project.
