---
title: "Every kernel update enables &quot;quiet splash&quot; for ALL kernels..."
date: 2006-07-22
forum: Desktop Environments
---

### Post by scotty64 on 2006-07-22
I have compiled my own kernel and installed it with the "nosplash" option, because I would like to see what's going on when the system boots. I do not know why, but whenever the system is installing an update for one of the default Ubuntu kernels on my system it resets my kernel to "quiet splash" as well. This is annoying as the system boots "blindfolded" until kdm starts.
How can I avoid this problem?

---

### Post by JayCnrs on 2006-07-22
Have you tried editing your Grub config file?  You can use your favorite text editor and remove the quiet splash lines from the kernel options:

[B]open /boot/grub/menu.lsts for editting as sudo, eg. sudo pico /boot/grub/menu.lst

Look for the line - kernel /vmlinuz-2.6.15-25-686 root=/dev/hda2 ro quiet splash

Edit the line as this kernel /vmlinuz-2.6.15-25-686 root=/dev/hda2 ro[/B]

Now when you reboot you should see everything the kernel does at the beginning and then as the different services start they should show.

---

### Post by SimonJW on 2006-07-22
This is a feature of debian's "automagic" kernel list.

You can change what gets auto-inserted by editing the line:
```
# defoptions=quiet splash

```
in the /boot/grub/menu.1st file (leaving it commented). This will, however, mean that all of the other kernels will loose these commands too.

I believe (but have not tested) that the alternative would be to put your kernel in the list after:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

```
and then it will be left alone by the auto-updater.

Both of these suggestions will only take effects after running```
sudo update-grub
```
or after an update, which will run this command itself.

---

### Post by scotty64 on 2006-07-23
Thanks for all the help! I was just not aware of the commented lines having a meaning in a debian menu.lst.

---

