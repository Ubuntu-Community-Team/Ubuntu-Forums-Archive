---
title: "how can I see if my video card is working"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by mhanraha on 2007-04-28
I recently switched from suse to ubuntu, and I was attempting to use the desktop effects when the screen just went white.  I was wondering if there was a way to see if my video is enabled? thanks mark

---

### Post by denver on 2007-04-29
try using:

```
glxgears
```
and
```
glxinfo | grep direct
```

The first should give you 2 pinning sprockets and the second should output something like:

```
gaby@denver:~$ glxinfo | grep direct
direct rendering: Yes
```

if direct renderng is "no" then you do not have 3D enabled.

---

### Post by the8thstar on 2007-04-29
If you don't have 3D enabled, how do you enable it?

---

### Post by stmiller on 2007-04-29
Do you know if you have an nvidia or ATI card?

Either apt-get install nvidia-glx-new

or

apt-get install xserver-xorg-video-ati

---

### Post by the8thstar on 2007-04-29
I have an Intel 945M onboard, so which one should I use?

---

### Post by denver on 2007-04-30
Try this

```
apt-get install xserver-xorg-video-intel
```
```
/etc/init.d/gdm restart
```

If still no joy...try:
```
dpkg-reconfigure xserver-xorg
```

and follow the instructions

---

