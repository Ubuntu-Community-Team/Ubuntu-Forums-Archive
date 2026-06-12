---
title: "Force Video Card Resolution?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by scaphist on 2007-04-20
I've read a about a few people that have 'forced' their computer to boot up at a standard resolution of their choosing. My questions is...if I'm using an HDTV as a monitor (which runs at a normal looking resolution on Windows XP) can I force Ubuntu to recognize it at a resolution other than the 640xwhatever it currently only lets me choose?

I find it hard to beleive that I have a setup that works better on Windows than Linux. Thanks!

---

### Post by scaphist on 2007-04-21
anyone?

---

### Post by orange2k on 2007-04-21
You can try the following command in the console:

sudo nano /etc/X11/xorg.conf

Scroll down until you find the section "Screen".
All resolutions available to you will be listed so just add the resolutions you want for every
screen depth. At the end save the file with ctrl+o, reboot and you`re done...

Hope this helps

---

### Post by scaphist on 2007-05-07
Nope, I changed the resolutions as needed and im still forced into 640x460

---

