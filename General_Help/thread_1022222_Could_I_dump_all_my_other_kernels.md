---
title: "Could I dump all my other kernels?"
date: 2008-12-26
forum: General Help
---

### Post by Nu music project on 2008-12-26
I started with 8.04 and wound up with Ubuntu studio 8.10 (2.6.27-11-generic).  However, to make Rosegarden work I need to boot 2.6.27-3-rt.  I need to do that manually which is a nuisance.

Why don't I just delete all the other kernels?  What would I loose?

question 2 is:- how?

---

### Post by jerome1232 on 2008-12-26
Yes you can, to remove them you would

```
sudo apt-get remove linux-image-2.6.(hit tab to list out your installed kernels and remove some you don't want)
```

---

### Post by Nu music project on 2008-12-26
thanks jerome but is there a downside?  I mean, new Kernels are written for a reason no?

---

### Post by jerome1232 on 2008-12-26
2.6.27.3.4-rt is the newest rt kernel though, so if you need the rt kernel and that's the one you will be booting no point in keeping the other's around. right?

---edit---

I meant no point in keeping the standard kernels around if you need the rt for rosegarden (I assume this is some sort of audio app that requires rt), it is always a good practice to keep at least one known good working kernel around.

I have a laptop that can only boot from one kernel despite 3 newer ones that have come out. I just use startup manager to select the old one as default and hope for one that doesn't hard lock that laptop to come out.

---

### Post by Rog-Mahal on 2008-12-26
I've heard that the rt kernel can be buggy sometimes. I haven't used it though, so take my opinion with a grain of salt. I like to keep a stock ubuntu kernel around in case I break something when I custom compile one. If it works it's up to you.

---

### Post by LowSky on 2008-12-26
go into synaptic and type kernel in search, all the install kernels should come up.

My opinion is to keep the best last 3, so if your newest it the RT then try to keep at least 2 of the standard kernels. Once you remove them, it will also upgrade you grub.lst

Also use Start-up manager to manager you grub list if you like, lots of cool setting you can change, but be careful

---

