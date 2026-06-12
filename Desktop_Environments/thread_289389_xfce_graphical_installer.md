---
title: "xfce graphical installer"
date: 2006-10-30
forum: Desktop Environments
---

### Post by eilu on 2006-10-30
I'm thinking of trying xfce out, but the 50Mb I need to download is going to take forever on my dia-up. What I'm thinking of doing is getting the graphical installer in school (where we have DSL) and transfering it to my system via flash drive.

Has anyone tried the graphical installer? Does it have everything I need to try xfce out? Are there other dependencies I have to get first? Thanks.

---

### Post by aysiu on 2006-10-31
The Desktop CD does, in fact, have everything you need to try out XFCE.

If, however, you have under 256 MB of RAM, you might not be able to run the live session and installer at the same time; in which case, you should get the Alternate CD.

---

### Post by chavo on 2006-10-31
No the graphical installer for xfce does not contain all of the dependencies. It just contains the source code and tries to build each package one at a time. So you will have to install a compiler and all of the build-deps for xfce anyway. The compiler is on the CD and you can install it with this command -> sudo apt-get install build-essentials. Then a sudo apt-get build-dep xfce4 - should get you the dependencies you need. It shouldn't be too big of a download.
You can also download all of the debs you need to install xfce, while your at school. There is a script or command that will give you a list of the files you need. Then you can take the list to school and grab the debs. I can't remember exactly how to do it, so maybe someone else will chime in or I'll recall it soon.
Another option is to just start the apt-get install xfce4 right before you go to bed. Then in the morning you will wake up to a nice new install of xfce. This is how I downloaded big things when I was on dialup.

---

### Post by eilu on 2006-10-31
> **aysiu said:**
> The Desktop CD does, in fact, have everything you need to try out XFCE.

I suppose you mean the Xubuntu CD? Can I use that to just install XFCE (since I already have Ubuntu)?

---

### Post by aysiu on 2006-10-31
> **eilu said:**
> I suppose you mean the Xubuntu CD? Can I use that to just install XFCE (since I already have Ubuntu)?
Only if it's the Alternate CD--then you can install Xubuntu **in addition to** your current Ubuntu.

If it's the Desktop CD, you can install Xubuntu **over** your current Ubuntu.

---

### Post by eilu on 2006-10-31
oh, I see. I'll get that then. Thanks!

---

