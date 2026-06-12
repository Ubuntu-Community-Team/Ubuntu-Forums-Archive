---
title: "Problem installing printer network"
date: 2012-08-28
forum: Desktop Environments
---

### Post by thenovelist on 2012-08-28
I have a HP Photosmart 7510 networking printer.  I have tried on several occasions to get Ubuntu 12.04 to install it.  Alas without success, which is not unusual for me and my limited experience with Ubuntu.  How can I get my Ubuntu 12.04 LTS to see my printer?  I have printed out the IP address, subnet mask etc from my printer, hoping it would assist me, but its all gobbledygook.  I therefore have a printer I can't use.  Any help would be grateful - Thank you

---

### Post by nativehound on 2012-08-28
I had a similar problem. The system settings printer manger in 12.04 is useless imho. i had to used the old

```
 system-config-printer
```

to get my network printer recognized.

gl

---

### Post by thenovelist on 2012-08-28
Thanks for your reply.  I found that the HP7510 wasn't listed, so that is also another problem.

---

### Post by thenovelist on 2012-09-05
Ah well, thank god I have my Windows.  It seems I can't rely on linux to do what I would have thought a simple thing.  Alas not simple for me unfortunately as I have not got the experience.  Maybe one day :lolflag:

---

### Post by thenovelist on 2012-09-16
Here's the thing; just loaded Ubuntu onto my wifes laptop this morning and the printer worked.  I used the same method with no problem.  So why can't my 64bit comp work with the printer!  It really is dam frustrating

PLEASE any one have any ideas on how I can proceed

---

### Post by thenovelist on 2012-10-12
PLEASSSEEE could someone assist.  I cannot print anything and have to rely on my wife's laptop which is not acceptable.  I have scoured the web without resolution as to how to resolve this dam problem.  I want to ditch Windows completely but I think in hine sight with problems such as this that would be suicide.  The wife can achieve printing with her Ubuntu 32bit, but I cannot print a dam thing from my 64bit comp.   All the setting are the same on my wifes printer as they are mine, so why can't I print?

---

### Post by kurt18947 on 2012-10-12
I am not well versed with HP printers.  Do you have hplip & hplip-gui installed?  They're in the repositories and can be installed using either Ubuntu software center or (my favorite) Synaptic.  You may find these helpful.

---

### Post by thenovelist on 2012-10-13
You are a STAR!!  It is now working.  I didn't know about the HP apps and its working great.  Shall also put it on my wifes as the software does a lot more than the standard printer links

---

