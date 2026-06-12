---
title: "Grub error 15 when ubuntu  installed on 2nd hdd"
date: 2008-12-18
forum: General Help
---

### Post by j.miller565 on 2008-12-18
I'm having trouble with accessing my newly installed ubuntu partition from grub and it gives me  grub error of 15. Windows is on the 1st hdd (sda1) and ubuntu is on the 2nd hdd( sdb1). I really want to start using Linux again but really need to fix this problem first. Ooh yea I have tried the  Super Grub Disk to try and fix the problem but that hasn't worked as well. Help would be greatly appreciated. :KS ps I installed 8.10


Thanks,
J.miller565

---

### Post by dagoth_pie on 2008-12-18
youll need to edit the lines in grub, (e i think) from the boot menu, under root, windows will need (hd0,0) and ubuntu will need (hd1,0) assuming its on the first partition...

---

### Post by j.miller565 on 2008-12-18
Windows is already set as hd(0,0) and the ubuntu partition is already hd(1,0). Thanks anyway.is there anything else I can do?

---

### Post by dagoth_pie on 2008-12-18
yes there is, and just to clarify, you can boot into windows cant you? ill just quickly track down the command

---

### Post by j.miller565 on 2008-12-18
Yea I can still boot into windows through the super grub disk

---

### Post by dagoth_pie on 2008-12-18
can you get into the grub menu installed on the hard drive though?

---

### Post by j.miller565 on 2008-12-18
Yea I have to go through sgd to access the grub menu though I think

---

### Post by dagoth_pie on 2008-12-18
uhuh, check that both hard drives are connected and showing up in the bios, its possible that the reason it cant find the grub config file, is because the hard drive simply isnt attached right, otherwise the sgd should be detecting the ubuntu install, so just check that, if its all connected ill have a go racking my brain...

---

### Post by j.miller565 on 2008-12-18
Yea all hdd are detected in the bios and all of the partitions  are detected in gparted(using live cd). Oh I've made a mistake the freash ubuntu install is on sdb5 not sdb1 soz hope that changes things

---

### Post by dagoth_pie on 2008-12-18
that means that it needs to be trying to boot of (hd1,4), although if its comming up with error 15 before getting to the boot menu of the hard drive installed grub then it needs to be pointed to the right partition...

---

### Post by dagoth_pie on 2008-12-18
you need to get to the grub command line, on the cd should do fine, youll know its the right one if it has 
```
grub>
```
then you will need to enter
```
root (hd1,4)
setup (hd0)
```
that should at least make it bring up the grub menu when you boot, the itll just be a matter of making sure it tries to boot from the right partitions

---

### Post by j.miller565 on 2008-12-18
Do you think I should just wipe the whole 2nd hdd and install it again and see what happens?

---

### Post by dagoth_pie on 2008-12-18
it'd probably work instantly, but thats the windows approach, try using the sgd to get to the minimalist grub command line, then run those commands, they youll probably need to edit the boot lines, so that windows boots from (hd0,0) and ubuntu boots from (hd1,4), then, unless theres something ive missed, they should both boot

---

### Post by j.miller565 on 2008-12-18
Oh ok going to try the commands now see how that goes :)

---

### Post by j.miller565 on 2008-12-18
Didn't work  well going to try installing it again but this time wiping the whole 2nd hdd

---

### Post by j.miller565 on 2008-12-18
New install doesn't work now gives me an error 2

---

### Post by dagoth_pie on 2008-12-18
is that before or after the boot options menu?

---

### Post by j.miller565 on 2008-12-18
That is before

---

### Post by dagoth_pie on 2008-12-19
hmmm, try reinstalling ubuntu, but make a small partition on the end of the first hard drive with the mountpoint /boot when you get to the partitioning part of the installation

---

### Post by j.miller565 on 2008-12-19
Um how big?

---

### Post by dagoth_pie on 2008-12-19
i think 100mb should cover it, my /boot folder is about 65mb

---

### Post by j.miller565 on 2008-12-19
Ok cool going to see what hapens now

---

### Post by j.miller565 on 2008-12-19
Ok installation just finished now I get a grub error 2 the one I got before hmm this is interesting.....

---

### Post by j.miller565 on 2008-12-19
Anyone know how I can solve this now?

---

### Post by j.miller565 on 2008-12-19
Yes it works now after putting the boot partition on the first hdd rather than on the second hdd. Thanks so
Much for the help dagoth pie!


Thanks again,
 j.miller565

---

