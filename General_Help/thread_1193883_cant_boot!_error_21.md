---
title: "cant boot! error 21"
date: 2009-06-22
forum: General Help
---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2009-06-22
i recenty install ubuntu 9.04 on my computer and has been booting fine ever since but today i started her up and it gave me this message: ERROR 21 and simply wont boot

i am completly stuck and have booted from a live disk to post this please help!:confused:

---

### Post by lindsay7 on 2009-06-22
If you have more than one disk drive, try to change the hard disk boot priority in you bios. (hit the del key or f2) and look for this item.

If this does not work post the output of these commands after entering in the terminal.

Sudo fdisk -l   that is the letter l not the number 1

and 

sudo gedit /boot/grub/menu.lst  again that is the letter l,  be sure not to change anything in this file just copy and paste what you get here.

---

### Post by gradinaruvasile on 2009-06-22
I dont think its the hard drive priority. That should give error 17 or something.
This one is 
"21 : "Unknown boot failure"
This error is returned if the boot attempt did not succeed for reasons which are unknown."

from here:

[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

Can u see/mount/browse your hard drive from the live cd? If u can,
this may help:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by lindsay7 on 2009-06-22
Here is what the grub manual reports as error 21.

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

