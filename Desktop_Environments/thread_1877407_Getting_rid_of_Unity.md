---
title: "Getting rid of Unity"
date: 2011-11-08
forum: Desktop Environments
---

### Post by Saidear on 2011-11-08
This is not a comment on the aesthetics/pleasantness of the new Unity interface.


I have an older laptop (Toshiba A210) and I recently updated to 11.10 and got Unity.  While I have no doubt that the new interface is great and intuitive, I find that on my laptop it is actually quite slow and sluggish for whatever reason.  Even in 2D mode (menus lag 1-2s when I call them out, and I can't figure out how to make the oversized menu smaller instead of taking up 3/4 of the screen)

I'd much rather use a simpler basic desktop-style theme.  Ideally I'd use Xubuntu or Lubuntu but I've had issues in the past with it's buggy cpu-frequency applet and no way to change the governor easily on the fly.  Gnome has a handy applet for that with *indicator-cpufreq*. So.  Given that I've already installed gnome-shell, how do I go about removing Unity and Unity2D entirely from my laptop?

---

### Post by crazy bird on 2011-11-08
I think this migth help you: [http://www.google.nl/search?q=%22Getting+rid+of+Unity+%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images]("http://www.google.nl/search?q=%22Getting+rid+of+Unity+%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images").

---

### Post by Saidear on 2011-11-08
> **crazy bird said:**
> I think this migth help you: [http://www.google.nl/search?q=%22Getting+rid+of+Unity+%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images]("http://www.google.nl/search?q=%22Getting+rid+of+Unity+%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images").

Pretty much all the same thing I found in my google searches: "Just login as ____"
Two problems:

1) I set autologin as enabled, this laptop doesn't hold any data that I consider sensitive, and anything it could access is on a secured network share.  Which means it logs into Unity whenever I turn it on.  That means to get into a comfortable environment, I need to logout, change the session, and log back in again which defeats the convenience of the feature.

2) Since Unity is not a smooth experience on my laptop, let's just get rid of all the unneeded packages filling up the hard drive entirely by removing it.

---

### Post by crazy bird on 2011-11-08
> Pretty much all the same thing I found in my google searches: "Just login as ____"
 
Select the option ***In cache***. This shows a printable versions.
 
 
What about Xubuntu? It is Ubuntu without the Gnome desktop environment, whithout the Unity desktop environment but with the Xfce desktop environment.

---

### Post by Saidear on 2011-11-08
> **crazy bird said:**
> Select the option ***In cache***. This shows a printable versions.
 
 
What about Xubuntu? It is Ubuntu without the Gnome desktop environment, whithout the Unity desktop environment but with the Xfce desktop environment.
Have they fixed the issue with *xfce4-cpufreq* that wouldn't let you change from "ondemand" ? That and a panel applet to make a simple swap between cpu scaling is all that is stopping me from swapping over.

---

### Post by mörgæs on 2011-11-08
[http://ubuntuforums.org/showthread.php?t=1777887](http://ubuntuforums.org/showthread.php?t=1777887)

---

### Post by Saidear on 2011-11-08
Thanks Mörgæs for the input, wasn't aware of OnDemand being better for power-savings than a manual setting. But like you, I don't think it's necessarily best for this laptop.

I installed Xubuntu over night and it does indeed run better.  I still can't change the CPU scaling beyond "ondemand" with Xfce-cpufreq installed, even if I tell it go on performance.  Any solution to this besides editing the setting with mousepad every time?

---

