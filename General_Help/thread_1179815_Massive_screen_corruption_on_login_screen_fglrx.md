---
title: "Massive screen corruption on login screen fglrx"
date: 2009-06-06
forum: General Help
---

### Post by GrimRe on 2009-06-06
Hi,

I recently downgraded my graphics card from a HD4870 to a X1900. I figured I could just just swap them over but it turns out I can't.

After the system boots the login screen has huge graphical corruption with just lots of different coloured vertical bars all over the screen.

I tried booting in recovery mode and trying the following commands:

```
apt-get remove --purge xorg-driver-flgrx
sudo dpkg-reconfigure -phigh xserver-xorg

```

Then rebooting but still no luck :(

I then booted into the Live CD and just copied the entire /etc/X11 folder from the live cd to my HDD and rebooting, still the same problem!

Driving me nuts! Doesn't make any sense I'm using the xorg.conf that works with the livecd, but when I try and use it on my real system it has the crazy screen corruption!!!

Thanks in advance

---

### Post by GrimRe on 2009-06-08
Managed to fix this with a the brute method:

```
apt-get remove --purge x11* xserver* *xorg* 

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```

talk about overkill lol

---

