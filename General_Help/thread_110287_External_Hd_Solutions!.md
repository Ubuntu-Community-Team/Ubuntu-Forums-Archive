---
title: "External Hd Solutions!"
date: 2005-12-30
forum: General Help
---

### Post by yonkman on 2005-12-30
I am a NEWBIE to Linux!

Now that I got that out of the way here is my story.

Installed Ubuntu, didn't like Gnome, installed KDE.

Have a 4port unpowered usb hub (printer,scanner,camera,lLacie External HD 120gb) plugged into a 4port usb switch with 2 laptops and 1 desktop (ubuntu) plugged in.

Ran into many of the same problems found on this site concerning extrenal usb harddrives.

1) started by formatting HD in XPPRO 2 fat, 1 ntfs partitions.
2) had to add lines to /etc/fstab to get BASIC drive recognition (got all the I/O errors
3) finally , using qparted and fdisk, could repartition drive into 1 40gb vfat and 1 exteded reiserfs 80gb.

4) problems on load (had to turn off ext HD for unbuntu to load) and problems havind HD recognized by windows boxes

Solutions that I think made the difference

1) set up two partitions on HDD
1) set up partition vfat as PRIMARY and as Partition #1
2) set up rest of disk as extended THEN format as ReiserFS in qtparted
3) VERY IMPORTANT Assign Volume labels to partitions (especially VFAT) or windows won't recognize it.
4) I ended up using mlabel solution form the link below since I didn't set up Volume Labels originally and qtparted would not add then when I tried to reformat partitions.
[http://www.ubuntuforums.org/showthread.php?t=65830&highlight=label+mlabel](http://www.ubuntuforums.org/showthread.php?t=65830&highlight=label+mlabel)
which made all the difference in the world.

I also believe that I had to (like 2 days ago) plug the ext HD into its own usb port on the desktop to perform the low level operations first then added it back to the hub.

Everything works fine now. and even boots properly
 Ubuntu happy + Winders Happy = Me Happy.

The only annoying thing is that the hotplug was prompting me for a choice of action when I would plug in the USB  ("open in Koncoquer or do nothing")  I think I ended up defaulting th "open to " choice and now it does it without prompting.
I would LOVE to disable this.

Anyone know how????


Most people on this board and in the Linux world can tell me what above I did wrong or if my hypothesis is incorrect but it worked for me so I am posting it in the hope someone else won't spend 3 days like I did!!!

Thanks for all the help and Please search the Forums FIRST (It paid off for me)

---

### Post by ltmon on 2005-12-31
Well done with the external HD... I don't know what all the fuss is about myself -- I just plugged it in (preformatted FAT32) and it worked??? Lucky me I guess....

To adjust your automatic actions on plugging in:

K-Menu -> System Settings -> Storage Media

In that screen you can select your storage type (Mounted Removable Medium should be right) and decide on the actions you want available as the default.

L.

---

