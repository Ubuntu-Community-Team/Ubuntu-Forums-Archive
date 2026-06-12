---
title: "Using GDM on Kubuntu: No connectivity"
date: 2011-11-10
forum: Desktop Environments
---

### Post by abedayyad on 2011-11-10
Hello All, 

I installed GDM (version 2.3) on top of Kubuntu 10.10. 

I really like the feel of Gnome over KDE and, more importantly, appreciate the much economised resources use (which I kind of need ...that's another story though). 

Anyway, I have noticed that there are serious connectivity issues with GDM, when I try to log in using that at the login screen. For example, iwlist when I use Gnome does not produce any results (and yes, I can see the wireless networks when I use KDE). I believe this might be because I tied the wireless interface to a password in a keyring when I set up Kubuntu, a while back. I am not sure how to ensure that the same password is unlocked when I run GDM. 

Another, probably related question: Sometimes, Gnome just does not launch in normal mode, although it does if I use safe mode. 

I would appreciate any thoughts/ideas, especially if you have experience of using Gnome on Kubuntu. 

Thanks,

---

### Post by abedayyad on 2011-11-12
So it seems the problem is with the graphics card drivers I have installed (in this instance, Radeon 3100), which apparently doesn't work too well with GDM (never had these problems with the KDE). 

I actually managed to find the answer somewhere on this forum, but no bizarrely can't find it again, oh well ... 

Also: didn't realise there was no networking in the safe mode of Ubuntu.

---

