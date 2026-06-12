---
title: "Please help: Ubuntu will not boot!"
date: 2006-07-21
forum: Desktop Environments
---

### Post by uxohus2b on 2006-07-21
Hi,
I have a Ubuntu-Windows dual boot. I was using both fine, but now if I try to boot Ubuntu, I get this message:

Bootin 'Ubuntu, kernel...'
root (hd0,1)
....

Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/hda2 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#




What should I do? The last thing I did before this happened was try to change my network connection method from static to DHCP. Ubuntu was still processing that change when I decided it wasn't going to work and tried to restart the machine. I didn't force shut anything, however. This is really all I did, and I wasn't even using the terminal. 

Thanks

---

### Post by bviking on 2006-07-24
I had a similar (extremely frustrating!) problem a while back.

From memory, the solution was to login as root in the busybox shell and reset the permissions on the directories . and .. in root (/)

Good luck!

---

### Post by cotcot on 2006-07-24
Supposing you did not shuffle around with your partitions.
It is a matter of checking why /dev/hda2 etc is not found.
I suggest to boot from the installCD and try to mount /dev/hda2 manually. 
If this works I would try to reinstall grub. There are posts about this in this forum.

---

### Post by CameronCalver on 2006-07-26
> **uxohus2b said:**
> Hi,
I have a Ubuntu-Windows dual boot. I was using both fine, but now if I try to boot Ubuntu, I get this message:

Bootin 'Ubuntu, kernel...'
root (hd0,1)
....

Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/hda2 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

Thanks

Hey i have the exact error i would love if i could fix it

---

### Post by uxohus2b on 2006-07-26
Yeah, actually I took the easy way out and just reinstalled Ubuntu. Wasn't much of a problem since I keep my files in a separate partition.

---

