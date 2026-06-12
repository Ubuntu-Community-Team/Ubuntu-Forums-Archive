---
title: "HARDY HERON doesn't load VISTA anymore!"
date: 2008-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anizato on 2008-09-02
I installed UBUNTU onto my dell 1501 amdathlonx2. Vista was obviously on it, and it sucked from day one! 

I reversed the settings within VISTA somehow to load UBUNTU as the main OS. Before this reversal, on startup it would ask me what OS I wanted to boot.

After this reversal, from the poweron, it was all different. It loads great, but when it's time for the prompt to come up. It gives me a glimpse of the screen and it goes directly into UBUNTU. I want to be able to choose between OS's again.:lolflag:

Ok, I typed this into the TERMINAL
sudo gedit /boot/grub/menu.lst

and came up with 

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7AD80341D802FB61 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7AD80341D802FB61 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1

i don't know what most of this means. I understand that my savedefault, has an error loading when i try to boot with vista. is there anything i can change in here in order to get my dualboot screen from skipping?

Can anyone please help me revert what has been done? How can I go back to windows??

Thanks guys! 

AniZaTo:guitar:

UBUNTU RULES...! 

bonne P.L.U.R.

---

### Post by steveneddy on 2008-09-02
**[COLOR="RoyalBlue"]HARDY HERON doesn't load VISTA anymore![/COLOR]**

Finally something goes right!

---

### Post by anizato on 2008-09-02
> **steveneddy said:**
> **[COLOR="RoyalBlue"]HARDY HERON doesn't load VISTA anymore![/COLOR]**

Finally something goes right!

HAHAHA HAHAHA! !!

I KNOW RIGHT?

really the only reason I use VISTA, is because I like to play SIMCITY4. 
It's installed on windows. but i have all the files and .iso files. 

Can the be extracted and installed on ubuntu?? if so, i would permanently delete vista!! ! !

---

### Post by TimDaniels on 2008-09-03
In adding Linux after Vista, you probably put Grub into the MBR, which allowed Grub to be the boot loader.  I assume that is OK with you, but it might also have screwed up the function of the MediaDirect button (which you don't really need, anyway).  How is that button working now?

In shortening your menu.lst file listing, you left out 2 entries which may not have been commented out: default and timeout.  List those as well.

Your "root()" entries look weird by not including a device and partition no. between the parenthises, but if what you have used to boot Ubuntu successfully, I guess I've learned something new.

Get back to us with more information about what's in what partition and the full menu.lst contents.

*TimDaniels*

---

