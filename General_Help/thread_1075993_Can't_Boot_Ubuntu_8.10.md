---
title: "Can't Boot Ubuntu 8.10"
date: 2009-02-20
forum: General Help
---

### Post by snachodog on 2009-02-20
Hello, I seemed to have messed up my Ubuntu machine.  Running Intrepid on my Lenovo Thinkpad X61.

I was trying to install blueman and was following the instructions provided by Launchpad to add the repositories to do so.

Everything seemed successful and as I was looking around the Synaptic Package dealie I found that the package Bluez (I believe was how it was spelled) was ready for an upgrade and marked it.

As Synaptic was doing the upgrade/installation I was watching the terminal output (not sure what exactly it's called) and was watching as all sorts of stuff was being deleted (not unusual with libraries, etc) but then I noticed that various things stopped working - the Network/Wireless manager, the icons for the shutdown/user switching disappeared.

I rebooted when it was all done but it doesn't going any further than a text based boot error (I'll have to find it again).  I tried using a LiveCD but I couldn't do anymore than test the memory.

Any help in restoring Ubuntu without losing all my data would be greatly appreciated!

---

### Post by Yellow Pasque on 2009-02-20
Try booting into recovery mode (from the GRUB menu).
If you can get to a root prompt/console, you should: 
```
apt-get remove blueman
apt-get install ubuntu-desktop
```
This should allow you to reboot normally and start reinstalling all the packages you accidentally uninstalled.

---

