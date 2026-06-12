---
title: "Booting Problems"
date: 2009-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 2009 on 2009-07-21
I was trying to uninstall ubuntu [i also have windows installed on my computer and i was trying to make more space on my hard drive] but i think i did it wrong. i'm not sure what it was, but when i went to restart the computer [dell inspiron 6000] a screen came up saying
GRUB ERROR 17.
i waited a good 4 hours or so and the screen wouldnt change. i tried going to setup and changing and enabling/disabling different drives and options but nothing has worked yet. does anybody know how to fix GRUB ERROR 17 so i can boot the computer up to windows?

---

### Post by philcamlin on 2009-07-21
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

this is a helpful link

---

### Post by pgiog on 2009-09-08
And if the highly enriched thread [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) does not solve the problem like in my case then have in mind:

If you have installed a newer high capacity disk to an older motherboard/laptop then the bios might not be able to fully support the number of cylinders of the new disk.

Most functions may still work but for sure grub error 17 will not go unless you position the grub files in a partition close to the beginning of the disk (ie cylinder number is low and bios likes it)

_**Lesson Learned:**_
Install grub files at the **FIRST SMALL PARTITION OF THE DISK** (the one to the left of the various partition managers gui) and then try the rest of the editing solutions

---

