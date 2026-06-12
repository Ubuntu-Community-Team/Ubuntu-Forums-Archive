---
title: "problem booting"
date: 2011-09-14
forum: Desktop Environments
---

### Post by Corvair on 2011-09-14
Hello everyone.
I have come up with a problem after working on my power supply and 
shutting the computer in a non-conventional way.
when booting up I come up with these two indications:
Missing modules (cat /proc/modules ; 1s /dev)

/dev/disk/by - uuid/daaefff5-46a9-4b44-b444-3301701404f9 does not exist. Dropping to a shell

Then I try to boot from recovery modes:
kernel 2.6.32-33 which is the most current kernel down to version 23.
It keeps on searching and searching without success until one time it booted, but I don't recall which one it was.

After shutting the computer off I tried the same thing again it would not boot this time. 
I went to the help menu from the normal unsuccessful booting procedure and hit the chdir command and it booted which I think was just a fluke.

After a power failure I had to reboot again and I had the same problem.
When trying to reboot from a recover kernel nothing happened until I hit some key from the keyboard and the system booted for some weird reason.

How can I recuperate the two files mentioned earlier and recover my kernel?
I have Ubuntu 10.04(lucid) kernel 2.6.32-33 generic gnome2.30.2.

I try not to shut the computer down in order to prevent the booting problem again.

Anyone can help, please?

Thank you.

---

### Post by agillator on 2011-09-14
I suspect GRUB has become corrupted somehow. However, if yu have managed to boot and have it running, first check /etc/fstab and see if there is a reference to that UUID in the first column of one of the entries.

Then, try reinstalling GRUB2. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for instructions and options.

If that does no good then you may have a problem with your partition table and may have to reinstall.

---

### Post by Corvair on 2011-09-15
Agillator,
Thank you for the quick reply. I will work on your suggestion.

---

### Post by Corvair on 2011-09-15
I have now removed grub and installed grub-pc grub2 and I am going to try and see if it solved the problem. If you don't see me again tonight there is still a problem.

---

### Post by Corvair on 2011-09-16
Agillator,

Problem finely found and resolved.

After loading Ubuntu 11.01 on a new hard disk I had the same problem as with 10.01. The only thing in common is the BIOS.
All my SATA connections were deactivated. I believe I did a load defaults and that caused the problem. After activating the SATA connections I was able to enter in my 10.01 OS.

Thank you.

---

