# GTAhouseModel

Highlight of the Code

:round_pushpin::round_pushpin::round_pushpin:

```{r, echo = FALSE}
#create a linear model for sale vs. lotsize
mod1 <- lm(sale ~ lotsize, data = updated_dataset)
residual <- rstandard(mod1)
plot(na.omit(updated_dataset$lotsize), residual, 
     main = "Figure 2: Residual Plot of Data - 7813",
     xlab = "Lotsize",
     ylab = "Standardized Residuals")
```


## III. Methods and Model

```{r, include=FALSE}
final.data <- na.omit(updated_dataset)
fullmodel <- lm(sale ~ ., data = final.data)
summary(fullmodel)
```



```{r, include = FALSE}
estimated_coefficients <- c("4.969e+04", "8.294e-01", "2.031e+04", "8.498e+03", "-1.736e+04", "2.139e+01", "8.154e+04", "4.436e-02")
p_value <- c("0.4130", "< 2e-16", "0.1798", "0.5898", "0.0813", "0.0003", "0.0511", "0.9913") 
df4 <- rbind(estimated_coefficients, p_value)
the_data <- data.frame(df4)
rownames(the_data) <- c("estimated", "p-value")
colnames(the_data) <- c("(Intercept)", "list", "bedroom", "bathroom", "parking", "taxes", "location", "lotsize")
the_data
```
```{r,echo = FALSE}
kbl(caption = "estimated coefficients and p-value list - 7813", the_data) %>%
  column_spec(2:9, background = "yellow") %>% kable_styling(latex_options = "hold_position")
```
