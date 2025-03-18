# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Simulation Extrapolation Inverse Probability Weighted Generalized Estimating Equations Use gee (swgee) With (In) R Software
install.packages("swgee")
library("swgee")
require(gee)
swgee = read.csv("https://raw.githubusercontent.com/timbulwidodostp/swgee/main/swgee/swgee.csv",sep = ";")
# Estimation Simulation Extrapolation Inverse Probability Weighted Generalized Estimating Equations Use gee (swgee) With (In) R Software
swgee <- swgee
rho <- 0
sigma1 <- 0.5
sigma2 <- 0.5
sigma <- matrix(0,2,2)
sigma[1,1] <- sigma1*sigma1
sigma[1,2] <- rho*sigma1*sigma2
sigma[2,1] <- sigma[1,2]
sigma[2,2] <- sigma2*sigma2
set.seed(1000)
swgee_1 <- gee(bbmi~sbp+chol+age, id = id, data = swgee, family = binomial(link="logit"), corstr = "independence")
summary(swgee_1)
swgee_2 <- swgee(bbmi~sbp+chol+age, data = swgee, id = id, family = binomial(link="logit"),corstr = "independence", 
missingmodel = O~bbmi+sbp+chol+age, SIMEXvariable = c("sbp","chol"), SIMEX.err = sigma, repeated = FALSE, B = 20, lambda = seq(0, 2, 0.5))
summary(swgee_2)
# Simulation Extrapolation Inverse Probability Weighted Generalized Estimating Equations Use gee (swgee) With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished