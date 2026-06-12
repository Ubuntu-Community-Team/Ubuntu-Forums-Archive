---
title: "I just installed Ubuntu on a dual boot. How do I make XP boot by default?"
date: 2009-01-24
forum: General Help
---

### Post by princerameses on 2009-01-24
sudo gedit /boot/grub/menu.lst

Is the command I used to bring up the boot thing in gedit, but what do I change?

Thanks.

---

### Post by dcstar on 2009-01-24
> **princerameses said:**
> sudo gedit /boot/grub/menu.lst

Is the command I used to bring up the boot thing in gedit, but what do I change?

Thanks.

You have to set the "default" option near the top of the file.

---

### Post by AlexBellisBrown on 2009-01-24
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0


**You mean that? So therefore you should change this;**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

**to this**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**And the ubuntu entry from this;**


title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=847a1504-bae2-409d-9315-d42716453b19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

**to this;**


title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=847a1504-bae2-409d-9315-d42716453b19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

**I think thats right, but im no expert. Id be happier if i had confirmation before you tried that....**

---

### Post by kaurman on 2009-01-24
The second post is the one to follow....

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

Change 0 to another number depending on the position of windows in the menu. 0 means that the first entry is used by default... 1 is probably the recovery mode etc... See the end of the file for the list.

NB... The third post seems very suspicious you should not mess with it if you want to maintain the ability to boot at all

---

