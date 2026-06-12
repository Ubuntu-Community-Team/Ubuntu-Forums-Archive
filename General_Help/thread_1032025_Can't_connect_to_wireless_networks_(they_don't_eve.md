---
title: "Can't connect to wireless networks (they don't even show) on broadcom wireless card *"
date: 2009-01-05
forum: General Help
---

### Post by iPodVision on 2009-01-05
I can't pick up a signal with a broadcom wireless. Yes I'm right next to the router I know I'm going to have to install something. Just did a fresh install of ubuntu 8.04

I need this for school tomorrow and I Must get wireless!!!

---

### Post by orlox on 2009-01-05
Broadcom wireless cards never worked right for me on 8.04, but with intrepid, I simply need to install the b43-fwcutter. The thing is, I need a wired connection to do this! as far as I remember, this doesn't work by default because there are some legal issues with incorporating the firmware directly in ubuntu...

If you have access to a wired connection, you could try to upgrade to intrepid, and installing the b43-fwcutter package. Not a very clean option, but I hope it helps you...

By the way, is the wireless working and not detecting your network?? If you press the button on the notiication area, can you see an empty list under wireless networks (or is the wireless mentioned in any way??)

---

### Post by NoBugs! on 2009-01-06
Yeah, the latest version is a lot better. You should be able to go to system - admin - hardware drivers, and enable the broadcom driver. Then restart, and it should work.

---

### Post by iPodVision on 2009-01-06
> **orlox said:**
> Broadcom wireless cards never worked right for me on 8.04, but with intrepid, I simply need to install the b43-fwcutter. The thing is, I need a wired connection to do this! as far as I remember, this doesn't work by default because there are some legal issues with incorporating the firmware directly in ubuntu...

If you have access to a wired connection, you could try to upgrade to intrepid, and installing the b43-fwcutter package. Not a very clean option, but I hope it helps you...

By the way, is the wireless working and not detecting your network?? If you press the button on the notiication area, can you see an empty list under wireless networks (or is the wireless mentioned in any way??)

I can see wireless, just there's nothing under it. I heard interpid was horribly unstable so I plan to stay on 8.04, if it must be a last resort so be it.

---

### Post by orlox on 2009-01-06
I think I had the same problem on hardy. If you really don-t want to use intrepid, then recompile ndiswrapper as mentioned here>

[http://www.blog.highub.com/linux/ubuntu-hardy-broadcom-wireless-setup/](http://www.blog.highub.com/linux/ubuntu-hardy-broadcom-wireless-setup/)

---

