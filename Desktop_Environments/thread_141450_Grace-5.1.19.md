---
title: "Grace-5.1.19"
date: 2006-03-08
forum: Desktop Environments
---

### Post by yarri on 2006-03-08
Hej!

I found that [Grace]("http://plasma-gate.weizmann.ac.il/Grace/") is a very promising program for making quality graphs and charts. Nevertheless I have a problem. There is an updated version of Grace (5.1.19) with quite important changes in comparision to previous version available in Synaptic. I admit I am not very familiar with compilling from the source but I gave it a try. Unfortunately configuration script is complaining about missing M*tif. I am tring to install different Lesstif packages but so far nothing helps. Was anybody able to compile Grace? What I am doing wrong?
Thanks in advance.

---

### Post by adamkane on 2006-03-08
Try installing grace6
[code]
sudo apt-get remove grace
sudo apt-get install grace6
[/code/

---

### Post by yarri on 2006-03-09
Unfortunately grace6 package contains beta version which is not good for day to day work :(.

---

### Post by adamkane on 2006-03-09
Bug:
[https://launchpad.net/distros/ubuntu/+bug/17855/+editstatus](https://launchpad.net/distros/ubuntu/+bug/17855/+editstatus)

Email for more info:
[email]bddebian@comcast.net[/email]

Looks like you're stuck with 5.1.18 or 5.99.

---

