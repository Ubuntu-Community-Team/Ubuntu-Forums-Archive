---
title: "moving install to other harddrive"
date: 2008-12-04
forum: General Help
---

### Post by relaxedcrazyman on 2008-12-04
hello everyone, thanks to a bunch of support from the forums and friends, i really like ubuntu and instead of having ubuntu partitioned on one of my drives i decided to dedicate my 500gb hd to it. i was just wondering if there is any way to basically move all my ubuntu os from a 100gb partition on 1 drive to taking over the other 500gb hd without losing any of my programs or settings and such. the 500gb drive is currently ntfs but i am prepared to move everything and format it (dont know how fyi)


thanks!

---

### Post by bhtek on 2008-12-04
One of the easiest ways I have taken was to follow the instructions from this page :)

[http://www.greenfly.org/tips/filesystem_migration.html](http://www.greenfly.org/tips/filesystem_migration.html)

---

### Post by relaxedcrazyman on 2008-12-04
With all these in mind, the best method I've found for copying the / filesystem is as follows (assuming for the example the new drive is mounted at /mnt/temp):

find / -xdev -print0 | cpio -pa0V /mnt/temp 
[COLOR="Red"]
I dont get this "assuming for the example the new drive is mounted at /mnt/temp"[/COLOR]


After all the filesystems have been copied, you probably won't actually have a bootloader. What I usually do, is go ahead and move the new drive into the place of the old one, and boot up on a Knoppix disc. Then I mount the new drive, say at /mnt/hda1, and then run grub-install --root-directory=/mnt/hda1 /dev/hda to copy my new bootloader to the new hard drive. You could probably do something similar just from your old install.

[COLOR="Red"]
Or that part.

mind you, i am still a uber newbie at all this linux stuff[/COLOR]

---

### Post by bhtek on 2008-12-05
Let's first assume you just want to dump the current entire filesystem to the new drive. And that you will only have one partition on the new drive.

Then, all you need to do is to format the new drive and mount it at /mnt/temp.

As for the bootloader part, errm... follow the instructions from this link [http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

---

