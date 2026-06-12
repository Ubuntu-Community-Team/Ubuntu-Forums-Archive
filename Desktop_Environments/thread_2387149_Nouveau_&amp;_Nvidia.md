---
title: "Nouveau &amp; Nvidia"
date: 2018-03-15
forum: Desktop Environments
---

### Post by theller on 2018-03-15
Although this question is regarding LTSP clients (Ubuntu 16.04 server and clients) I am posting here because if someone can help me to get this to work on a standalone machine I can get it to work on a client. I need an Ubuntu image that can identify and load the necessary video driver at Boot time. Some clients have video cards and need Nvidia drivers, others use onboard graphics (nouveau). If I use an image with nouveau drivers, everything works but the video cards give me 5 FPS. If I switch to Nvidia I get 124FPS on the computers with graphics cards but the PCs with onboard videos get stuck in a login loop. I could have 2 images and assign with MAC addresses but I love using only one image on many clients.

I tried this page ([http://wiki.tolabaki.gr/w/LTSP_Fat_Client_Setup](http://wiki.tolabaki.gr/w/LTSP_Fat_Client_Setup)) but I couldn't get it to work. 

Even though this is from a gentoo wiki I might try this next ([https://wiki.gentoo.org/wiki/Nouveau_%26_nvidia-drivers_switching](https://wiki.gentoo.org/wiki/Nouveau_%26_nvidia-drivers_switching))

What info or config can I share?
Does anyone have a solution, suggestion, thoughts or questions?

---

### Post by Autodave on 2018-03-15
Hopefully someone else will be able to help, but I know of no way to do it except having 2 images and choosing the correct one.

---

