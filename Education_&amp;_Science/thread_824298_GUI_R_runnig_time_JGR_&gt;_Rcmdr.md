---
title: "GUI_R runnig time JGR &gt; Rcmdr"
date: 2008-06-09
forum: Education &amp; Science
---

### Post by GreenLinux@R on 2008-06-09
Fro those who may need to consider the running time difference when do you simulation. 

I tried the same simulation code on both JGR and Rcmdr twice and recorded the time using function system.time() and found out that JGR used two time as much as Rcmdr did. here is the results.

JGR

User       system       elapse

342.154   .108          173.021 
371.427    .192         187.469


Rcmdr
 
User       system       elapse
228.528    .104         228.604 
185.30     .070         185.327

I felt it is wired because as what I knew , elapse time should equal the sum of user and system time. Rcmdr looks like doing the way I knew. What did JGR do? 

Any thoughts?  :confused:   could some one try your code to see what is going on?

---

### Post by GreenLinux@R on 2008-06-10
ok, here is a simple comparison

###### Rcmdr 
>  system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.216   0.012   0.228 

>  system.time(rnorm(1000000,0,1))
   user  system elapsed 
  [COLOR="Red"]0.192 [/COLOR]  0.008   0.201 

>  system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.232   0.004   0.238 

### terminal R
> system.time(rnorm(1000000,0,1))
   user  system elapsed 
  [COLOR="Red"]0.192[/COLOR]   0.004   0.195 
> system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.220   0.008   0.229 
> system.time(rnorm(1000000,0,1))
   user  system elapsed 
    0.2     0.0     0.2 
> 

### JGR 

> system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.420   0.004   0.210 

> system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.380   0.004  [COLOR="Red"] 0.192 [/COLOR]
> system.time(rnorm(1000000,0,1))
   user  system elapsed 
  0.444   0.000   0.211 
>

Seems that JGR is using something different to report the time use. It might not be a big problem. but I might put JGR on hold for my use at this moment although I like it very  much.

---

