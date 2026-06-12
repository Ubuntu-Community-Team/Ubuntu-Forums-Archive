---
title: "2 x servers with 2 screens"
date: 2012-09-13
forum: Desktop Environments
---

### Post by MacOsX74 on 2012-09-13
Hi!

I am new to Linux with no experience what so ever.
I am going to try Linux instead of Windows due to poor performance.

My setup is this.
Ubuntu Server 11.10
LG TV 47" as monitor 1
Optoma HD82 Projektor as monitor 2
Nvidia GTX560 Graphics Card

What i want is the following:
Run Ubuntu desktop on monitor 1
Run XBMC on monitor 2
This works with seperate x screens but i cant have the function. "match videoresolution to media" in XBMC.

To fix that i have to add a user and start an X server for that user and run XBMC from there.

I have added an User and started another X server. It all works but here is where I need help.

User 1 and monitor 1 on X server 1 = tty7
User 2 and monitor 2 on X server 2 = tty8

How do make this last when i reboot. When i reboot now i have to make settings in Nvidia Settings so the screen setup is right.

I think i have to manually write in the xorg.conf file but i have no idea how.
I also want to have the second user autologin when I boot.

Can someone please help me with this?

Marcus
Sweden

---

### Post by MacOsX74 on 2012-09-21
Bump!

---

