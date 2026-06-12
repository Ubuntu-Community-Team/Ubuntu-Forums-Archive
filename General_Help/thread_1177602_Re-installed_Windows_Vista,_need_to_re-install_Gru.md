---
title: "Re-installed Windows Vista, need to re-install Grub to MBR"
date: 2009-06-03
forum: General Help
---

### Post by allanlewis on 2009-06-03
What is the easiest way of doing this (safely)?

---

### Post by merlinus on 2009-06-03
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by FiggyG on 2009-06-03
I usually boot from the live cd, once I'm in I open a terminal and run grub.

sudo grub

Now that we are in the grub command line, run this to find where your current grub installation is at.

find /boot/grub/stage1

It should say something like (hd0,2) or some such. Use that information for the next command

root (hdx,y)

Now, to install Grub back to the MBR, you have to know what your drive you're booting off of, this is typically (hd0) so we type in

setup (hd0)

You're almost finished, post back if you get any errors and one of us should be able to help you. Now, exit grub and reboot the machine.

quit
sudo reboot

---

