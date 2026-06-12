---
title: "Chrome browser opens with no top bar in Xubuntu 14.04"
date: 2015-01-30
forum: Desktop Environments
---

### Post by geovino on 2015-01-30
I just installed Xubuntu 14.04 and after installing Google Chrome browser I notice that if I minimize then maximize chrome the whole top part of the browser is gone! all the controls. Then by clicking in the area it will come back in pieces. I've never seen this before. Is this a bug in XFCE? I didn't happen with other desktops, only Xfce with Xubuntu 14.04 and Mint 17.1.

Any fixes? or do I have to use KDE instead since it seems to be a more polished and stable desktop.

---

### Post by kerry_s on 2015-01-30
are you using system title bars & borders?

---

### Post by geovino on 2015-01-30
> **kerry_s said:**
> are you using system title bars & borders?

No, I always uncheck that box in settings. I've never seen this happen before, and it's not every time, but most of the time. It doesn't happen with Firefox, only Google-Chrome which I use most of the time.

And I'm running this on a Lenovo G580 laptop with 8GB RAM and Intel processor.

---

### Post by vasa1 on 2015-01-30
> **geovino said:**
> ... I've never seen this before. Is this a bug in XFCE? I didn't happen with other desktops, only Xfce with Xubuntu 14.04 and Mint 17.1.

Any fixes? or do I have to use KDE instead since it seems to be a more polished and stable desktop.

Don't see any problems on Lubuntu 14.04 Openbox session with Compton as compositor and the latest Chrome.

Have you toggled hardware acceleration in Chrome's advanced settings?

---

### Post by geovino on 2015-01-30
> **vasa1 said:**
> Don't see any problems on Lubuntu 14.04 Openbox session with Compton as compositor and the latest Chrome.

Have you toggled hardware acceleration in Chrome's advanced settings?

I will try that out. Thanks!

---

### Post by geovino on 2015-01-30
I have hardware acceleration checked. Maybe if I try compiz and see if it may help?

---

### Post by startas on 2015-01-31
its xfce problem - xfwm is broken for now, change it to compiz or delete the whole xfce to solve this bug.

---

### Post by geovino on 2015-01-31
Will do. Thanks.

---

