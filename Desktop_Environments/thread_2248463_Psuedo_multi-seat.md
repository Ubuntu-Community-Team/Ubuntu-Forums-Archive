---
title: "Psuedo multi-seat?"
date: 2014-10-15
forum: Desktop Environments
---

### Post by Ranko Kohime on 2014-10-15
This may be more appropriate for hardware, I'm not entirely sure.

I'm attempting to get a psuedo multi-seat setup working on my desktop that has Intel integrated graphics and an Nvidia graphics card.  My intention is that I can access the Nvidia desktop on VT 7, as normal, and the Intel desktop on VT 8, using the same keyboard and mouse.

I've followed, and slightly modified the directions [here](http://brainacle.com/multiseating-with-kde-and-xbmc-like-a-boss.html), with the end result that restarting kdm results in both desktops loading up in their respective users, with the Nvidia desktop accessible with the keyboard and mouse, but switch to any VT other than 7 causes the Intel desktop to black out, (with the backlight still lit), which stays black even after returning to VT 7.

I've also seen [this blog post]("http://www.linuxadvocates.com/2013/03/making-nvidia-and-intel-play-nice.html") but as I don't use LightDM, I'm not sure how much of it is applicable.

I'm running Arch Linux with the KDE desktop, and while I've posted on the Arch forums, no one has had any advice to offer yet.

Any help in getting the last step in this process is much appreciated.  :)

[My xorg.conf](http://pastebin.com/cizXvfj0)
[My kdmrc](http://pastebin.com/2gp33zeP)

---

