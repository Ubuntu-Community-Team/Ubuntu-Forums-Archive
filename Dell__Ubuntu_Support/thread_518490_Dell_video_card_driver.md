---
title: "Dell video card driver"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by jimhce on 2007-08-05
Hi,

I got a couple of problems while was installing Ubunto 7,04 on Dell Inspiron 8000 laptop. 

1. The screen was splitted in to two duplicated half Desktop, I guess that was due to the problem of the horizontal frequency. How can I set up to boot from text mode and to start x window manually, so I can edit xorg.conf in command line?

2. Where can I find video card driver for Ubuntu? The installation window is too big to see the buttons on the bottom. I tried to reduce the window size, but it could not be resized by mouse (strange!!). I guess the only thing I can do is to install the video card driver first and to change the screen to high resolution.

Thank you.

Jim

---

### Post by Nunslaughter on 2007-08-06
you can boot in recovery mode from grub, then type sudo dpkg-reconfigure xserver-xorg to edit...

which videocard do you have?

---

### Post by pbcartwright on 2007-08-06
to get to a text mode, you hut CTRL-ALT-F1
this gets you to the login prompt and you can login as your user and sudo vi your xorg.conf from there.
CTRL-ALT-backspace will restart X, or from the command line you can just run the command gdm or kdm, whichever you are using..

---

### Post by jimhce on 2007-08-06
It is ATI Mobility 3, where can I download driver from Ubuntu?

Thank you.

Jim

---

### Post by stingx on 2007-08-06
You can download ATI drivers from the official ATI site. I have ATI x1400 on Inspiron 9400 and those proprietary drivers works well for me.

---

### Post by jimhce on 2007-08-06
To correct my previous post, it is actually an ATI Mobility 128 4X. I tried ATI linux driver download site, but could not find ATI 128??

Thanks.

Jim

---

