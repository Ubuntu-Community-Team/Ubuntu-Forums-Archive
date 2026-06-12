---
title: "games don't work"
date: 2007-01-01
forum: Gaming &amp; Leisure
---

### Post by ion one on 2007-01-01
So I tried to launch a game (let's say tremulous) and didn't start. I've tried another game same result. I reinstall nvidia drivers still nothing..Please help! No game is working :confused:](*,) ](*,)

---

### Post by Lord Illidan on 2007-01-01
Launch it from the terminal and give us the output.

---

### Post by ion one on 2007-01-01
yep it goes like:

Egoboo, Copyright (C) 2000 Aaron Bishop
Unable to set video mode: Couldn't find matching GLX visual

---

### Post by Lord Illidan on 2007-01-01
Then your nvidia drivers are not working probably.

Tell us:

1. Your make of card.
2. What drivers did you install? Did you install the nvidia-glx drivers from apt-get or from the nvidia.com website?
3. The output from glxgears -printfps
4. The output from glxinfo
5. Your /etc/X11/xorg.conf file.

---

### Post by ion one on 2007-01-01
problem solved..thanks anyway!eventually beryl crashed the whole xserver and neither the console didn't work so i had to reinstall :)

---

### Post by Lord Illidan on 2007-01-01
> **ion one said:**
> problem solved..thanks anyway!eventually beryl crashed the whole xserver and neither the console didn't work so i had to reinstall :)

Reinstall? Wow...anyway what was your problem?

---

### Post by Sammi on 2007-01-02
What did you reinstall? Your whole Ubuntu installation or just one app?

---

### Post by ion one on 2007-01-02
whole ubuntu...but .... problem got back!!](*,) ](*,) help :D thanks!gives more output this time, like :

Unable to set video mode: Couldn't find matching GLX visual
*** glibc detected *** egoboo: corrupted double-linked list: 0xb7de2158 ***

---

### Post by ion one on 2007-01-02
got it working!here's how for all the rest that can't figure it out why games don't work:

add to your /etc/X11/xorg.conf at the section Device the line :        Option          "AllowGLXWithComposite" "true"

and works like a charm!

---

### Post by Sammi on 2007-01-02
That's a common part of any Nvidia driver howto :D

Glad it worked out for you, though I think that the Ubuntu reinstall was dumbfound and unnecessary.

---

