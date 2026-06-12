---
title: "screen resolution problems"
date: 2006-09-25
forum: Desktop Environments
---

### Post by namelessone on 2006-09-25
I recently "upgraded" my video card from an ATI Rage Pro  to an ATI Rage-128 (what an upgrade, huh?). After starting up my computer again, X wouldn't start up, but I soon found the problem: I had placed the "new" card in a different slot. I soon fixed that by editing the xorg.conf file, changing the BusID to "PCI:1:0:0". After this, everything worked fine for the rest of the day...

When I started up my computer this morning I discovered, to my dismay, that the screen resolution was 640x480, and it wouldn't let me change it to what I had before, 1024x768.

It is possible that my changing of video cards has nothing to do with this, but I would really like to know how to get my resolution back to 1024x768. Can anyone help me?

---

### Post by croak77 on 2006-09-25
Try running sudo dpkg-reconfigure xserver-xorg, it's a guided setup of your /etc/X11/xorg.conf. It will ask you about screen resolution.

---

### Post by Gotterdammerung on 2006-09-25
Try eliminating modes you'll not use from xorg.conf. Let's say you want a 1024x768 screen resolution:

> Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "VA721"
DefaultDepth 24
SubSection "Display"
depth 24
virtual 1600 1200
**modes "1024x768@60"**
EndSubSection
EndSection

It may solve your problem.

OBS.: Focus on modes line.

---

### Post by namelessone on 2006-09-25
Hurray! Everything is working now. I ran the sudo dpkg-reconfigure thingy using the options sugested in the /etc/X11/xorg.conf file and now everything is back to normal. Thank you!

---

### Post by Gotterdammerung on 2006-09-26
> **namelessone said:**
> Hurray! Everything is working now. I ran the sudo dpkg-reconfigure thingy using the options sugested in the /etc/X11/xorg.conf file and now everything is back to normal. Thank you!

Great! Now please add [SOLVED] to the subjet of your thread.

---

### Post by namelessone on 2006-09-26
I know this sounds silly, but I don't know how to do that...

---

### Post by bluefuse on 2006-09-26
I have the ATI 9200se 128....my video is 1280x1024 at the worst.......

that card rocks:mrgreen:

---

### Post by Gotterdammerung on 2006-09-26
> **namelessone said:**
> I know this sounds silly, but I don't know how to do that...

It's not silly. Edit the first post and change its subject adding [SOLVED] to it. :)

---

