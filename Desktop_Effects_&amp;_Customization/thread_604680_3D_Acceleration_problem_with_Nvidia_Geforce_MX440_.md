---
title: "3D Acceleration problem with Nvidia Geforce MX440 8x"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Zelofun on 2007-11-06
Hello Everybody!
direct rendering: No (direct rendering: No (
I recently installed Ubuntu 7.10 (fresh copy, not upgrade) and all devices seems to work OK, except my graphics card (Geforce MX440 8x). The problems I have are the following:

1) Downloading and installing all available drivers for Nvidia when I glxinfo i get: direct rendering: No

2) All the above actions won't let me change my screen resolution from 800x600@73 except when I install "nv driver" that let me change my resolution to 1280x1024@60Hz but again 3D acceleration is dead!

3) Every time I install a new driver Ubuntu will not run properly, but will come up with a "Unix looking dialog box (low graphics mode)" and will ask me to define my monitor and my graphics card (even I have tried it with installed Nvidia dinary xorg driver, Nvidia dinary xord driver "new", generic and restricted driver).

4) I also tried to:  sudo dpkg-reconfigure xserver-xorg  . I configured driver via terminal, but the problem till there!

5) I also tried to modify xorg.cofig by setting up mu graphics card and my monitors (LG L1919S, 19") modes. Nothing....

... I tried basically every possible driver combination and command lines  I found on forums and people suggested me and still this bloody graphics card will not work correctly! My next step after this post's replies (If still have no results I will go to by a new Graphics card for this reason!...but I not that sure that new graphics card will be OK!!!)

Can someone suggest me a driver and a configuration scheme for this problem?

Thanks people!

---

### Post by Zelofun on 2007-11-08
I finally fount the solution to this problem after 20 days! Bought another graphics card for 35 euros and problem solved! ;)

---

