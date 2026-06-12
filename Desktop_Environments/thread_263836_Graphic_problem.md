---
title: "Graphic problem"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Whitey_McWhite on 2006-09-23
I'm using Kubuntu, dual boot with it and Winblows. I use winblows a lot more because i'm still learning linux and am familiar with windows so it's just easier for me. The problem I'm having is at start up, I shut down one day and tried to boot into it yesterday but it just kept doing it over and over. When it gets to the login screen, everything is staticy and colored lines. The mouse is just a big square of color, text is vertical black lines. All the graphics are messed up. What happened? How do I fix it? Thanks in advance

---

### Post by croak77 on 2006-09-23
Please don't call windows, winblows. It's juvenile and only plays into the fanboy stereotype.

Do you have a NVIDIA or ATI video card? Did you install any updates before this problem started? You might have to re-install the driver due to a kernel being upgraded. You can run, sudo dpkg-reconfigure xserver-xorg, from the command line. It's a guideed setup of X.

---

