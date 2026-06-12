---
title: "Kubuntu &amp; Compiz Fusion... How?"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by onlineapps on 2007-07-31
Hi,
I'm using Kubuntu Feisty with an ATI Radeon X300 graphics card.  For now, I'm using the fglrx driver.  But I can't install Compiz Fusion on it.  I used Trevino's repos ([http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)).  But Compiz Fusion told me that it couldn't run on my machine.  Funny thing is, Beryl did.

So could someone provide a guide that is for _K_ubuntu?  Thanks!

---

### Post by yuvlevental on 2007-07-31
I think you need to install XGL theres a guide here [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by userundefine on 2007-07-31
Kubuntu's not going to be your hurdle, as I'm running CF right now on kde feisty.  ATi drivers will be the problem.

---

### Post by roaldz on 2007-07-31
> **userundefine said:**
> Kubuntu's not going to be your hurdle, as I'm running CF right now on kde feisty.  ATi drivers will be the problem.

Im also running CF on Kubuntu. Do you experience the same slowness at some effects? I have an nvidia 7600gs 256mb graphics card. Some effects are good and snappy, but some seem to have "lag". I ran CF on gnome and it was just smooth. 

Roald

---

### Post by userundefine on 2007-07-31
Yes I do... responsiveness is reduced using it.  I never experienced this under Gnome either, and I've got the latest nvidia drivers (6600GT).  I really prefer KDE but kinda want to switch back to Gnome until it gets smoother.

---

### Post by roaldz on 2007-08-05
> **userundefine said:**
> Yes I do... responsiveness is reduced using it.  I never experienced this under Gnome either, and I've got the latest nvidia drivers (6600GT).  I really prefer KDE but kinda want to switch back to Gnome until it gets smoother.


I Have the same plans, so now I just installed ubuntu-desktop, and everything is just screwed now.. Loggin in takes 3 minutes or so, and it randomly hangs. If I try to run another GLX app, it crashes too. I think my lappie is ready for a fresh and clean Ubuntu install. 

But then.. Whats the best manner to get Compiz Fusion? I'm running 64Bit Gutsy now, but I think (not shure) I'll get back with Feisty 64Bit. I Haven't had any problems concerning 64bit, so that wont be a problem. Is it smart to compile Compiz Fusion yourself on 64Bit? I really love KDE too, but Compiz Fusion even better:)

Could you guys give me some advise on this? 

I really love these forums, great support!

Roald

---

### Post by userundefine on 2007-08-05
You were probably experiencing gutsy issues more so than conflicts between KDE/Gnome.

You could compile it if there aren't packages for 64bit, but 32bit runs just fine for me on my 64bit proc.

---

### Post by maestrobwh1 on 2007-08-14
> **userundefine said:**
> Kubuntu's not going to be your hurdle, as I'm running CF right now on kde feisty.  ATi drivers will be the problem.

You have to use the native Ubuntu driver (i.e. "radeon") if you want to use compiz with an ati card, or at least that is what I have seen/know. Last I checked, the fglrx driver was not compatible.

I use an ati radeon 7200 agp 64 mb.  Runs compiz-fusion in sort of a "sticky" manner in Feisty for me especially when running firefox, but in Gutsy, there seems to be no big difference in stability with running compiz or not running it.  With Gutsy, that could change in a day:-) with any given update.

I did have to add a few "tweaks" to my xorg.conf file to really get the most out of it... actually, I think I did the tweaks for Beryl, then never deleted the tweaks when I switched to Compiz fusion.

---

