---
title: "root filesystem check fails"
date: 2006-05-25
forum: Desktop Environments
---

### Post by firecrotch on 2006-05-25
Hello,

When I'm booting into Kubuntu, I get an error during the root filesystem check: Inode 115203 has imagic flag set.

It tells me to run fsck manually, but I can't do anything, since I cannot enter maintainence mode - I have no root password to enter.  Plus, I don't even know what fsck is or what it does.  Anyone have any clue what could be wrong or how to fix it? I'm in Windows right now, and I can't stand it!  Thanks in advance!

---

### Post by [S|G] on 2006-05-25
Fsck is a disk check and repair utility, analog to M$ Scandisk and chkdisk. Your file system has some sort of problem (I don't know exactly what that problem is though) and it is asking you to enter manual mode to fix that.

Root password should be the password you use on "sudo". Chances are that if you're the only user on the system, it'll be your password. After you login as root run 'fsck /dev/hda' (or the device that has problems) and when it finishes reboot and it should be fine.

---

### Post by Mau on 2006-05-26
Not entirely sure about this, but you should NEVER run fsck on a mounted file system.  Boot to the live CD and run it.

---

### Post by hcalsos on 2006-06-24
Hi.
Had the same problem, havent set root password on my installation, so i couldn't run fsck manually when asked to. :???: 
Tried to boot the rescue menu aswell, but got the same result. 
Also i had misplaced my live-cd ](*,) 

What you can do is this :
Boot-up computer 
Press 'Esc' to enter the GRUB menu 
Select the appropriate kernel and press e to edit the commands before booting.
Select for instance kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash, and press 'e' to edit.
Add "rw init=/bin/bash" to the end of the arguments, and press enter.

Press 'b' to boot

That should do the trick :)

---

