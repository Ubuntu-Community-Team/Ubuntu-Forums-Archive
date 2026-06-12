---
title: "Warzone 2100 screenshots are in very bad quality"
date: 2011-05-28
forum: Gaming &amp; Leisure
---

### Post by tranduyhung on 2011-05-28
Hi,

The quality of my Warzone 2100's screenshot is very bad. You can see in my attachment. I am using Lubuntu 11.04.

Is there any to make the screenshot better? Thanks!

---

### Post by sffvba[e0rt on 2011-05-28
It isn't the screenshots which are bad, just the quality of the graphics of the game :p

Just kidding, this is still one very awesome RTS game, as for the screenshot problem, I have no idea... Free *bump* :p


404

---

### Post by tranduyhung on 2011-06-07
Any one has solution :( ?

---

### Post by Perfect Storm on 2011-06-07
It may be a driver bug/issue? Which card do you have?

---

### Post by tranduyhung on 2011-06-07
Hi,

This is the result by "lspci | grep VGA":
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

---

### Post by Perfect Storm on 2011-06-07
> **tranduyhung said:**
> Hi,

This is the result by "lspci | grep VGA":
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

It may be a bug in the intel driver. Try search for "ubuntu 11.04 intel bug"

Or

on google: site:ubuntuforums.org ubuntu 11.04 intel bug distortion

For more info on which intel card you have run
```
sudo lshw
```
So you can add your card specific to the search.

---

