---
title: "Can't boot X as user only as root"
date: 2007-04-15
forum: Desktop Environments
---

### Post by Candolle on 2007-04-15
Hello,

When I start the computer I get past the splash screen then it goes blank (a grey screen). I have logged in using the fail-safe terminal and have tried startx but all I got was "Couldn't get a file descriptor referring to the console" and that I (the user) did not have the authority. I looked up ls -l .Xauthority .ICEauthority and it seems that the user has authority. I rebooted (sudo shutdown -r now) and it still won't let me on as user. I then tried the sudo dpkg-reconfigure xserver-xorg when through the 15 questions rebooted and the same thing still happens. I have done this several times changing the driver from i810 to vesa but no luck.  For some reason I get in as root (sudo startx) and see the gnome interface.

I have scoured the net for possible answers but have found nothing that has worked :confused: 

Can anyone help?

---

