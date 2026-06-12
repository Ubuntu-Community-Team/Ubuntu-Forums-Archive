---
title: "Windows keeps overwriting boot files, when I try to multiboot"
date: 2009-02-01
forum: General Help
---

### Post by whazzzzzup17 on 2009-02-01
Okay I been reformatting however, every time I try and multiboot, my windows overwrites the previous boot menu for that Operating System.

I installed my operating systems with 3 primary and 2 logical, however I installed Windows Xp first, and ubuntu last. I tried to hide the each partition on installation with Norton Partition Magic, however it never lets me install on it when there hidden.

Any advice on how I can fix this for future multiboots? I have to multiboot my laptop today so any help I'll greatly appreciate it.

---

### Post by lavinog on 2009-02-06
The problem might be that you need to install grub to the mbr.
I used to have a problem where booting into windows would prevent the grub menu from booting in subsequent boots.
[http://ubuntuforums.org/showthread.php?t=1042849](http://ubuntuforums.org/showthread.php?t=1042849)
This assumes you have one hd or want to boot only from the first hd:
To fix it:
boot into a live cd
open a terminal
```
grub
```
from there you should see a prompt: grub>
```

root(hd0,0)
setup(hd0)
quit

```
reboot and see if fixed

---

### Post by bumanie on 2009-02-06
Installing windows followed by ubuntu should allow everything to work properly, as in grub will recognize windows and add it to the grub list in a chainloading configuration. If you only have one windows installation, you should not need to hide partitions etc. Boot the live ubuntu cd, go to terminal and post the output of > sudo fdisk -lu so that we can see your present partition setup. If you are wanting a partition editor it would be best to use gparted, either off the ubuntu live cd or download the dedicated garted live cd from [here]("http://gparted.sourceforge.net/download.php"). I'm not sure how well partition magic deals with ext3 filesystems - that could be an issue.

---

