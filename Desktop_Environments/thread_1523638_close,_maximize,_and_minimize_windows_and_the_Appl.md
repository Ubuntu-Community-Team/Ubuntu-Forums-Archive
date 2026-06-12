---
title: "close, maximize, and minimize windows and the Application title bar disappear"
date: 2010-07-03
forum: Desktop Environments
---

### Post by ChrisEiffel on 2010-07-03
I am using GNOME Ubuntu 64 bit Lucid Lynx with Cairo Dock, Compiz Fusion, Screenlets


Sometimes when I start up linux the buttons to close, maximize, and minimize windows and the Application title bar disappear. Restarting usually fixes the problem. 

Do you have any ideas why this would happen? Is there a command that will restart gnome without having to restart the computer?

Thanks

---

### Post by vangop on 2010-07-04
Hi!
Depending on what window decoration engine you use, you need to run (Alt+F2):
```
compiz --replace
``` or
```
emerald --replace
```

I don't know why it crashes though.

---

### Post by ChrisEiffel on 2010-07-04
When my computer does it again it'll try the replace command  and post back my results.

Thanks!

---

### Post by yossell on 2010-07-04
if it's happening with compiz then you could fire up the compiz settings manager (ccsm from terminal) and have a look at the window decorations settings under effects.

---

### Post by behzadsh on 2010-07-04
same problem with lucid 32bit. and it will solve by compiz --replace.

but why this happens sometimes? how we can solve this?

---

### Post by ChrisEiffel on 2010-07-06
The compiz --replace worked great thanks!

---

### Post by egervari on 2011-05-11
This works... but why is this a problem even in May of 2011? Was this not fixed? I got this error 4 times in 2 days :(

Sounds like a bug everyone is going to get. I'm using 11.04 64-bit

---

### Post by rabla on 2011-05-16
I get this bug a few times every day. The 11.04 release is very dissapointing. :(

---

### Post by NormanFLinux on 2011-05-16
With the old netbook remix, the bars and panels disappeared in maximus when running a compositing engine.

The workaround was to shut off decorate. After that, everything stayed up.

---

### Post by wildmanne39 on 2011-05-16
> **rabla said:**
> I get this bug a few times every day. The 11.04 release is very dissapointing. :(

Hi, you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all. Compiz was not meant to be used with effects enabled in unity.Also you need to know that this is the first release with changes in the way ubuntu handles things, so it will get better as time goes on.:D

---

### Post by Copper Bezel on 2011-05-16
A lot of old posts getting dredged up today.

wildmanne39, the original post referred to 10.04, not 10.10, when the Mutter Unity was implemented. Now, of course, with Compiz Unity, there's no conflict between Unity and the other Compiz effects.

---

### Post by 2nanfer on 2011-07-12
Hi, just an observation. The problem still persists in Natty to date, I dont know if the effects I use from Compiz that are uncompatible but it is a daily issue. I use keyboard shortcuts and tab+mouse to drag windows.

---

