---
title: "Xorg gives me ~50% CPU usage"
date: 2005-10-16
forum: Desktop Environments
---

### Post by ola on 2005-10-16
I have upgraded my box from Hoary to Breezy and I am having problems with X eating ~50% of my CPU (according to top).

Anyone else expering the same problem?

Thanks!

---

### Post by aysiu on 2005-10-16
```
8094 root      15   0  105m  23m 3156 S  0.7  5.3   1:54.62 Xorg
``` Nope. It's at only 5.3% of my memory.

---

### Post by Stormy Eyes on 2005-10-16
I haven't had that problem. What sort of video card have you got? I've got a nVidia 5500.

---

### Post by ola on 2005-10-17
I have a Radeon 7500 card with DRI running as it should.

I have also noticed that I can't logout from gnome (the programs closes but it doesn't log me out).

I have removed all my dot-files (settingsfiles).

Any ideas?

---

### Post by Basurero on 2005-10-19
I'm having the same problem; 512 MB RAM and Xorg is using 205 MB. According to the Device Manager I have a "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]".
Another memory eating monster is Mysql, now using 115 MB, I think it didn't use that much before, or did it?

  Cheers,
  Lou

---

### Post by ola on 2005-10-19
I'll use KDE some days & se if it is X-related or Gnome-related.

My idea is that it's something with gnome-session, but thats just a feeling.

I'll come back in some days

---

### Post by kurtkraut on 2005-10-19
I have a NVIDIA card (64mb) and I never had problems with that on Hoary. But on Breezy it goes beyond 50% if CPU usage.

I'm using XFCE.

---

### Post by cowlip on 2005-10-20
Wow I made teh same thread a few days ago: [http://ubuntuforums.org/showthread.php?t=76719&highlight=xorg+cpu](http://ubuntuforums.org/showthread.php?t=76719&highlight=xorg+cpu)

So it's not just us then.  I also have a radeon 7200/Radeon RV100 QD

---

### Post by cowlip on 2005-10-20
Here are a few more threads, do a search for " xorg cpu"

---

### Post by cowlip on 2005-10-23
OK, I've switched to KDE and the issue is gone.  IT must be gnome/gtk/ubuntu-desktop releated

---

