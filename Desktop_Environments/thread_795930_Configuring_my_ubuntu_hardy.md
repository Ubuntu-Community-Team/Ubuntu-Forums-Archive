---
title: "Configuring my ubuntu hardy"
date: 2008-05-15
forum: Desktop Environments
---

### Post by batax_galoenk on 2008-05-15
Hii there, this is my 1st thread.
i'm so confused now.yesterday i was installing the new KDE4 in my ubuntu, but now i can't use my default gnome dislapy manager if i want to login.
how to totally remove the kde4 in my ubuntu hardy and reinstalling my gnome display manager, 'coz i don't want to reformat my laptop.
please help me
i'ma newbie in linux
so, i beg your help , plezzzz

---

### Post by zenwalker on 2008-05-15
Well if u have added Kde via Synaptic/apt-get, then i dont think Gnome would have been removed unless if u have purposfully removed it. 

Any ways, in the login window (GDM), select session and then Choose Gnome.

---

### Post by Ptero-4 on 2008-05-15
You don't need to remove KDE or reinstall at all (this applies to both version 3 and 4 of KDE) all you need to do is from the console type
```
sudo dpkg-reconfigure gdm
```
This will tell apt to reconfigure the gnome display manager which will cause it to ask you which display manager to use, you just select gdm and press enter, and you're good to go.

---

