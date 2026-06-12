---
title: "windows 7 mbr lost when install ubuntu dual boot"
date: 2010-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hhoyt on 2010-08-15
I have a multi boot env on an older dell and am trying to migrate to a new inspiron 570.

I dont think my problem is hardware but really scratching my head.

I think all is ok with just windows 7 installed.

Problem is, if I install Ubuntu 9.04 or 10.10 and run  grub-install, all SEEMS ok until I bring up windows and then reboot--
MODULE NOT FOUND. I think this is equvalent to OS not found on older systems.
--------
I create an ext4 partition (#4) and restore Ubuntu into it.
I then use Parted Magic from USB to enable grub2:
(already root)
mount /dev/sda5 /mnt
mount --bind /dev/ mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
update-grub
grub-install /dev/sda

___No errors___

I can then boot into Ubuntu ok.
If I boot into windows, it comes up first time, on reboot I get MODULE NOT FOUND.
I can /fixmbr off the windows 7 CD to recover but lose Ubuntu multi boot when I do it.

Any ideas ???

Thanks, Howard

---

### Post by hhoyt on 2010-08-15
appears this is related to launchpad bug 551721. 
I am just not sure how to fix it. 
Might be worth substituting something like gag for grub2.

Howard

---

### Post by hhoyt on 2010-08-15
This is definitely [http://ubuntuforums.org/showthread.php?t=1475646](http://ubuntuforums.org/showthread.php?t=1475646)

Those of us who
a) Use linux
b) need windoze for legacy

are in trouble on new win 7 PC install from Dell.

Dell happily includes a program DATASAFE that happily exploits unused portions of the MBR. Uh, unless you are using grub2 for multiboot. You see where I am going with this ?

Removed DATASAFE from Windows 7 and problem is resolved.
Only problem is no Dell recovery. I need to get the official Dell response on this.

SHAME on Dell.

Howard

---

### Post by wilee-nilee on 2010-08-15
> **hhoyt said:**
> This is definitely [http://ubuntuforums.org/showthread.php?t=1475646](http://ubuntuforums.org/showthread.php?t=1475646)

Those of us who
a) Use linux
b) need windoze for legacy

are in trouble on new win 7 PC install from Dell.

Dell happily includes a program DATASAFE that happily exploits unused portions of the MBR. Uh, unless you are using grub2 for multiboot. You see where I am going with this ?

Removed DATASAFE from Windows 7 and problem is resolved.
Only problem is no Dell recovery. I need to get the official Dell response on this.

SHAME on Dell.

Howard

Glad you figured out the Dell data safe. Generally once you dual boot and change the mbr the recovery sometimes appears in grub and works from there or is not usable.

Just get the recovery discs from Dell they will be the oem and always usable. You may be able to get a straight install disc, I'm not sure about a OEM key on this though.

I doubt if Dell will have a fix for your recovery to work with a 3rd party involved.

---

### Post by hhoyt on 2010-08-16
"I doubt if Dell will have a fix for your recovery to work with a 3rd party involved."

Alas, just so.
Dell recommended i contact Dell Solution Station for a modest fee.

They do not even have this in their Knowledge base altho I requested they do so. No real interest in linux. I really tried to explain it was in Dell's interest to have Datasafe save the MBR on win boot and restore it on exit. ---Or, at least, to document the problem in the Dell Knowledgebase. Deaf ears.

So I suppose it is up to the linux community to put the word out.

Regards, Howard

---

### Post by chitresh4u on 2010-08-22
> **hhoyt said:**
> This is definitely [http://ubuntuforums.org/showthread.php?t=1475646](http://ubuntuforums.org/showthread.php?t=1475646)

Those of us who
a) Use linux
b) need windoze for legacy

are in trouble on new win 7 PC install from Dell.

Dell happily includes a program DATASAFE that happily exploits unused portions of the MBR. Uh, unless you are using grub2 for multiboot. You see where I am going with this ?

Removed DATASAFE from Windows 7 and problem is resolved.
Only problem is no Dell recovery. I need to get the official Dell response on this.

SHAME on Dell.

Howard
Yeah Its annoying and irritating. Btw I have ordered recovery Disks [here]("https://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&l=en&s=gen"). I dont know when they will ship it, if at all they ship it.

---

