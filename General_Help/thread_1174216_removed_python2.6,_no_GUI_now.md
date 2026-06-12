---
title: "removed python2.6, no GUI now"
date: 2009-05-30
forum: General Help
---

### Post by College_Trained on 2009-05-30
Ok so here's my issue, I decided that the next programming language I want to learn is python. Python2.6 was installed but had no menu option under Applications > Programming so I figured ok I'll just remove it, reboot and reinstall to see if that works. Well now I am stuck with a CLI and can't get my ethernet or my wireless card to get an IP. My question is is there any way of reinstalling python using a live CD or an Ubuntu on another partition?
Any help would be greatly appreciated.
~C_T

---

### Post by Chronon on 2009-05-30
I think ubuntu-desktop depends on that in some way.  I guess removing Python also removed some other packages?  You could try reinstalling:

```
sudo apt-get install ubuntu-desktop
```

I believe this should restore Python and other packages and provide you with a working desktop environment again.

---

### Post by kk0sse54 on 2009-05-30
A lot of sotware written in python haven't been ported to to python 3 yet so removing python2.6 effectively renders much of it useless. Also since a lot of programs have python as a dependency I'm surprised you didn't notice a lot of your system being removed. Again as chronon said reinstalling ubuntu-desktop should bring it back.

 As for wanting to learn python open up a terminal and just type "python" to enter the interactive python prompt. Or press alt + f2 and type "idle" which is the default python IDE. Gedit also has a python plugin for displaying an interactive python prompt towards the bottom of it's window.

---

