---
title: "Need to experiment with my desktop X server configuration"
date: 2007-12-14
forum: Desktop Environments
---

### Post by leefw on 2007-12-14
Hi

I'm running KDE 7.10.

My X server crashed the other day without warning and I can't seem to get things right. This might the result of my PC being left on for days and days and updating software packages in the meantime without reboot, but I can't be sure. I only got it working againg by using "sudo dpkg-reconfigure -phigh xserver-xorg"

Two questions for you:
[LIST]
[*]The first thing is I can get the restricted NVidia driver to work so I think I need to experiment. At the moment I have the open source NV driver working with the correct screen resolution, but text is blurry and I want to get the restricted NVidia driver working. How can I backup my current settings (which files) and how can I restore them if my experimenting fails? 

[*]Second, the Kubuntu "boot logo" is gone and has been replaced with the old style console output, i.e "Initializing 'service' - [OK]" . I'm not sure how I fix this so I'd be grateful if someone could shed some light.
[/LIST]

Regards
Lee Francis

---

### Post by leefw on 2007-12-15
I didn't think this was a difficult question, but alas I seem to be mistaken. So it seems the xorg.conf files (and related) are a mystery to everyone?

---

### Post by leefw on 2007-12-16
Well - from what I can see it seems to be Xen that is the culprit. I installed Xen packages some time ago to see what it was all about, but never got the time. This was probably my first reboot since. Xen installed a boot image on my system and changed my GRUB settings (making it the default). I used the Adept repository manager to install... 

I still have some minor issues with a wrong screen resolution (on my graphical boot screen) that need correcting, but apart from that things are more or less back to normal.

Still... I am very uncertain on configuring X. If anyone has any references to a good tutorial or similar to learn the fundamentals then I would be grateful. I've been reading the man pages for xorg.conf, but it's a "hard read".

---

