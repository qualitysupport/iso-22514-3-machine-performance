# ISO 22514-3 Machine Performance Study App
 
An R Shiny tool for running machine performance studies (Pm / Pmk) following the procedure described in ISO 22514-3:2020 — Statistical methods in process management — Capability and performance — Part 3: Machine performance studies for measured data on discrete parts.
 
Built as course material for teaching AIAG-VDA / ISO 22514 harmonization concepts. Load your own data, or use the built in example dataset (ISO 22514-3:2020, Table 1) to explore how the standard's procedure works end to end.
 
For the full walkthrough, including sample size requirements, the run chart, checking normality, the skewed data problem, and the percentile method fix, see the companion article: [Implementing Successful Machine Performance Studies](https://www.linkedin.com/pulse/implementing-successful-machine-performance-studies-dan-lay-jr--6cyre/) on LinkedIn.
 
## What it does
 
* Pre condition checks (Clause 5): flags sample sizes under 30 (method doesn't apply) or under 100 (below the recommended minimum), plus reminders on holding other variables constant during the study.
* Run chart (Clause 7.2): sequence plot to catch drift, step changes, or instability before you trust the rest of the analysis.
* Histogram (Clause 7.3): with a fitted normal curve and your specification limits overlaid, so you can see visually how the data sits relative to tolerance.
* Probability plot + Shapiro-Wilk test (Clause 7.4): checks whether the normal distribution formulas are appropriate for your data.
* Performance indices (Clause 7.6): Pm, PmkU, PmkL, and Pmk, calculated either from the mean/standard deviation (7.6.2, for normal data) or from the 0.135th/50th/99.865th percentiles (7.6.1, for skewed or bimodal data).
* Confidence intervals (Clause 8.2): approximate intervals for the normal distribution indices, at a confidence level you choose.
* Downloadable report (Clause 8.1): a full study report and the raw data, ready to export.
## Running it
 
Requires R with the following packages:
 
```
install.packages(c("shiny", "ggplot2", "DT"))
```
 
Then:
 
```
shiny::runApp("app.R")
```
 
## A note on skewed and bimodal data
 
The normal distribution formulas (7.6.2) assume your data follows a bell curve. If it doesn't, the standard provides a separate percentile based method (7.6.1) rather than forcing normal distribution math onto data it doesn't fit. This app supports both, selectable from the sidebar. If your data is bimodal because of a machine adjustment partway through the study, or mixed cavities/tools, the better fix per the standard is usually to identify the cause and split the data into separate studies — the percentile method is a documented fallback, not necessarily the first move.
 
## Disclaimer
 
This tool implements calculation methods described in ISO 22514-3:2020 but is not affiliated with, endorsed by, or reviewed by ISO. It does not reproduce the standard itself. For authoritative guidance, consult the official ISO 22514-3:2020 document, available for purchase from [ISO](https://www.iso.org/) or your national standards body.
 
Provided as is, for educational and reference use. Acceptance criteria for Pm/Pmk (e.g. the commonly used 1.67 threshold) are industry convention, not values mandated by the standard itself — ISO 22514-3 Clause 9 leaves minimum acceptable values to be agreed between supplier and customer.
 
## Author
 
Dan Lay Jr. Metrologist | ASQ Certified Calibration Technician | Calibration Support LLC
[www.calibrationsupport.com](https://www.calibrationsupport.com) · [LinkedIn](https://linkedin.com/in/dlayjr)
 
## License
 
MIT — see [LICENSE](https://github.com/qualitysupport/iso-22514-3-machine-performance/blob/main/LICENSE).
