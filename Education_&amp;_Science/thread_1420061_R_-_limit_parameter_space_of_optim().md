---
title: "R - limit parameter space of optim()"
date: 2010-03-02
forum: Education &amp; Science
---

### Post by tommers on 2010-03-02
I would like to know how to impose boundaries on the parameter space which is being search for a maximum likelihood.  The function with which I'm working is:

```

rc.llike <- function(phi,x,n,t){

  #Pull out the parameters  
  pre_lev <- phi[1]
  post_lev <- phi[2]
  peak_lev <- phi[3]
  t0 <- phi[4]
  decay <- phi[5]

  #Find number of bins
  n_bins <- length(x)

  #Compute the log likelihood - for lack of a better method, use a for loop for now
  logl <- vector(mode="numeric",length=n_bins)
  for(j in 1:n_bins){
    logl[j] <- (log(factorial(n[j]))
	- log(factorial(n[j]-x[j]))
	- log(factorial(x[j]))
	+ x[j] * log(pre_lev + (post_lev - pre_lev 
        + ((peak_lev - post_lev) * exp(-(t[j] - t0)/decay))) 
        * Heaviside(t[j],a=t0))
	+ (n[j] - x[j]) * log(1 - pre_lev - (post_lev - pre_lev 
        + ((peak_lev - post_lev) * exp(-(t[j] - t0)/decay))) 
        * Heaviside(t[j],a=t0))
     )
  }
  sum_logl <- sum(logl)
  return(-sum_logl)
}

```

Running the optimizer using some fake data:

```

times <- seq(from=1,to=5,by=1)
counts <- rep(50,5)
corrects <- c(20,20,40,45,47)
out <- optim(c(0.4,0.6,0.8,3,0.5),rc.llike,x=corrects,n=counts,t=times)

```

Using this toy data, I get the following MLE:

```

> out
$par
[1] 0.3999879 0.8800120 0.8216285 2.8348778 0.6301844

```

I would like to impose the following limits:

```

0 <= out$par[1] <= 1
0 <= out$par[2] <= 1
out$par[2] <= out$par[3] <= 1

```

With the toy data, I can easily influence the fit by choosing different starting points.  However, with a full data set of about 50 measurements, I cannot avoid a fit which gives out$par[3]<out$par[2].  There theory behind the model imposes the constraints listed above, but I cannot seem to find a way to include them either when defining the function or calling the optimizer. Any help would be greatly appreciated.

---

### Post by euler_fan on 2010-03-03
The following example is from the optim help page in R:

## 25-dimensional box constrained
optim(rep(3, 25), flb, NULL, "L-BFGS-B",
      lower=rep(2, 25), upper=rep(4, 25)) # par[24] is *not* at boundary

As you can see, simply specify a vector or lower bounds and a vector of upper bounds in the proper order.

---

### Post by tommers on 2010-03-03
> **euler_fan said:**
> As you can see, simply specify a vector or lower bounds and a vector of upper bounds in the proper order.

This works very well if there are absolute values for all of the boundaries.  The problem that I have is setting the value of par[2] as the lower bound of par[3].  Do you have any suggestions on how to accomplish this?

---

### Post by scrogster on 2010-03-04
You could modify the code that specifies the log-likelihood so that is places a big penalty on the likelihood when the constraints are violated. This will force optim() to stay within the bounds you have set.

---

### Post by tommers on 2010-03-04
Works perfectly - thanks scrogster!

---

