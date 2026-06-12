---
title: "Question about using Dell restore images on dual-boot"
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dodger USMC on 2008-05-10
For those of you that have used the restore images from the Dell-Wiki, I have a question for you!

When you restore with the images, does it erase all partition information, or will it allow you to restore to a specific partition, thus leaving all other partitions intact?

I dual-boot Ubuntu and XP, and after upgrading to Hardy, My Ubuntu is straight BROKE. I want to restore to 7.10 with the Dell image, but I want my XP to remain untouched. Is this possible?

Thanks for any help you Gurus can provide!

---

### Post by gbrainin on 2008-05-12
AFAIK, the *.iso files on the Dell linux wiki are live CDs (or DVDs, as the case may be).  If that is the case, then there should be options during the install process for you to determine which partitions are/aren't mounted where, and which ones are formatted.  So if you know which of your partitions are which and how to ask for the right ones to be part of your Ubuntu install, it shouldn't have an ill effect on your XP install.  If you're not comfortable with that, then get some help, because messing up your partition table is difficult (if not impossible) to recover from.

On the other hand, if it is a restore image, like the restore partition that comes with the preinstalled Dells, then it will repartition and reformat your entire drive to an exact replica of the factory image.  It won't do this without several warnings, however, so I'd go ahead and put the disc in the machine and see what happens.  It should be obvious.

Oh, and it NEVER hurts to back up before you do anything like that.

---

