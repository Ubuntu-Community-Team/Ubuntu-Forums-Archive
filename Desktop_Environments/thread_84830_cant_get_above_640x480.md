---
title: "cant get above 640x480"
date: 2005-11-01
forum: Desktop Environments
---

### Post by zappa86 on 2005-11-01
I installed ubuntu on my Dell computer with an onboard 82845 graphics card. Gnome wont go above 640 480. I was looking around and something mentioned the xorg file, but in there I see all the resolutions: 1024x768, 800x600, and 640x480. The driver for the card is "i810". Its really hard to use a computer in 640 480. Thanks.

---

### Post by felix_stegerman on 2005-11-01
Hi,

It might be that your monitor's capabilities are not recognized properly.
Do you know the proper refresh rates?

Try posting your /etc/X11/xorg.conf and /var/log/Xorg.0.log.
That can help figure out what's going on.


Felix

---

### Post by heimo on 2005-11-01
Check these:

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

