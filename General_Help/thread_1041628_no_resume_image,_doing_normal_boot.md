---
title: "no resume image, doing normal boot"
date: 2009-01-16
forum: General Help
---

### Post by Kristopher on 2009-01-16
I just upgraded to 8.10 and everything is perfect, apart from the loading screen gets halfway and pauses for say 15 seconds then continues. I switched to the terminal to see and it had 

no resume image, doing normal boot...

Is there a way to fix this? as this is adding 15 unwanted seconds to my boots.

Thanks

---

### Post by Kristopher on 2009-01-16
So i now spotted Ubuntu 8.10 booting hangs for a while on "configuring network interfaces", this is only after the update to 8.10.....is this a known bug?

:(

---

### Post by drs305 on 2009-01-16
During boot ubuntu normally looks for a resume image, and if not found, continues to boot fairly quickly. On my computer, it usually pauses for less than a couple of seconds. If ubuntu has problems reading the resume image it could cause the delay you are experiencing.

Run these commands and see if the swap UUID is the same in all the results:
```

sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume 
cat /etc/fstab

```

If the swap UUID is not the same in all three, you can either edit the fstab and resume files to change the UUID to match the blkid result, or you can change the swap UUID using the "mkswap" command with the -U switch. If you need help doing this, post the results of the commands.

---

### Post by Kristopher on 2009-01-19
Here is my results, and yeah any help would be great as I have never done that before.

> kris@SubZero:~$ sudo blkid -c /dev/null
[sudo] password for kris: 
/dev/sda1: UUID="3a92be4a-910d-4ba3-97f6-45a43ce7540e" TYPE="ext3" 
/dev/sda5: UUID="dbd4a5bd-9e56-48c0-9688-e3badac70fd6" TYPE="swap" 
kris@SubZero:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=dbd4a5bd-9e56-48c0-9688-e3badac70fd6
kris@SubZero:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3a92be4a-910d-4ba3-97f6-45a43ce7540e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dbd4a5bd-9e56-48c0-9688-e3badac70fd6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2009-01-19
The swap designations in those files all match, which is good.

You can also check the menu.lst reference to resume:
```

grep "resume" /boot/grub/menu.lst  

```
It should point to /dev/sda5

Another item you can check is the dmesg file. It records the initial boot process. You could look for the last process initiated prior to a 15 second delay:
```

cat /var/log/dmesg

```

---

### Post by Kristopher on 2009-01-20
When i run "grep "resume" /boot/grub/menu.lst" i see the following :

## e.g. defoptions=vga=791 resume=/dev/hda5

not sda5 like you said.

---

### Post by drs305 on 2009-01-20
> **Kristopher said:**
> When i run "grep "resume" /boot/grub/menu.lst" i see the following :

## e.g. defoptions=vga=791 resume=/dev/hda5

not sda5 like you said.

Since that line has double quotes (##), it is a comment in this case. It is an example and can be left as it is. There is probably a line directly below it with a sinqle # which *is* acted upon. Since you didn't mention it, the line probably has "/dev/sda5" if it exists.

Device designations used to be either "hda" or "sda" depending on the type but a few versions ago ubuntu started designating them all as "sda". It generally made things simpler and less subject to change, and even more so as things are changing from "sda" to UUIDs.

---

