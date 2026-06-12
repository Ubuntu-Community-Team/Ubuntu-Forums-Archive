---
title: "Inspiron 17R 5720 - Which distro to use?"
date: 2012-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NilPointer on 2012-10-14
I bought a Dell Inspiron 17R 5720 today. It came with Ubuntu 11.10 preinstalled. I tried it out, but it's something terrible. First of all, it's pure Unity without gnome 2 or even gnome 3 (only Unity/Unity 2D). I was unable to find synaptic, but somehow opened a terminal and tried to install ubuntu-desktop and xubuntu-desktop, but first is installed already and second is not found. I could've installed Ubuntu 10.04 on it (I use it on my desktop), but probably not all hardware will work properly. So I wonder if I should keep it (somehow install gnome 2, perhaps?) or move to another distro. Currently, I'm considering Mint 13 with MATE. Any advices?

---

### Post by Sonsum on 2012-10-14
If you want synaptic

```
sudo apt-get install synaptic
``` should do it.

I would recommend gnome-shell or gnome-session-fallback (which is pretty much gnome classic) on 12.04. In my opinion, gnome-session-fallback is a very good gnome 2 replacement. It really doesn't change that much.

These two can be installed from synaptic, or with ```
sudo apt-get install gnome-shell gnome-session-fallback
```

Once they're installed, you can select which one to use from the login screen.

---

### Post by NilPointer on 2012-10-14
Well, that worked. But gnome classic looks awful, nothing like gnome 2. However, I managed to install xfce (i forgot to do apt-get update, so it didn't find it at first :) ).

---

### Post by NilPointer on 2012-10-15
I've installed Linux Mint 13 but just like I thought, not all devices are working and there is no proprietary drivers available (while on preinstalled Ubuntu 11.10 there were 4). So, is there a PPA with Dell drivers?

---

