---
title: "Ubuntu JEOS - custom usplash"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by colo on 2007-11-18
I'm setting up a virtual appliance for vmware server 1.0.x with Ubuntu JEOS, and want to have a custom bootsplash going with it. By following the Guide on [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto) I cam up with the following resulting C-Code:
[http://gnulords.org/~colo/tmp/usplash-artwork.c.gz](http://gnulords.org/~colo/tmp/usplash-artwork.c.gz)
At the end of the file, the usplash-struct contains the values
```
640,
480
```
for width and height, respectively. That seems fine, and corresponds to the dimensions of my source-imahe (640x480x4bit PNG).
I added my custom uplash image to the Debian alternatives, and set the new entry to be used. When my kernel loads, no splash is displayed, and as soon as getty takes over the VTs, usplash displays the message > no usable theme found for 640x480.
My /etc/usplash.conf contains
```
xres=640
yres=480
```

What am I doing wrong?

Setting the framebuffer to vga=785 on kernel bootup makes everything worse, with the VM's screen remaining totally blank after booting up.

The default splash (ubuntu artwork) always displayd fine.

---

### Post by colo on 2007-11-19
I scrapped the whole usplash thing, as it's obviously an absoulte PITA to customize, installed Splashy, and everything is working fine.

---

### Post by Zorael on 2007-11-19
Is it hard to replace the splash screen handler? I'd like to try out fbsplash, but I read someplace that you'd need to compile a new kernel.

---

### Post by colo on 2007-11-20
Kicking out usplash and replacing it with splashy is actually rather trivial; both splash-"engines" work almost entirely in userspace and therefore do not require fiddling around with the kernel. Splashy comes with a really comfortable configuration script that lets you create theme configs (they're XML, also quite easily editable by hand) in a few seconds, literally. You just need to supply PNG images with sane properties to use as graphics for the various states Splaysh may display them.

Splashy's init-script (or default config, I can't recall right now) dynamically extracts runlevel information out of /etc/inittab, which with Ubuntu's sysVinit-replacement "Upstart", does not exist. The package obviously was pulled over from Debian without inspecting it, by running a sed-script on it. You need to replace it with hard-coded values (or adapt it to process Upstart's config) to make Splashy work, but that's the only thing that felt somewhat rocky. Much easier than the nightmare customizing usplash turned out to be.

---

