---
title: "recovering files from raid 1"
date: 2009-02-14
forum: General Help
---

### Post by bthessel on 2009-02-14
Ok, so my 7.10 server will no longer boot. It had two software Raid 1 setups on it, one pair of IDE drives and one pair of SATA drives. I can boot the computer with a live cd and see all the partitions in gparted but I can't figure out what I need to do to mount them so that I can copy the data off to and external drive. Any suggestions?

---

### Post by hyper_ch on 2009-02-14
you need to install mdma and create the arrarys... don't know it currently by heart how to do that.

---

### Post by bthessel on 2009-02-15
> **hyper_ch said:**
> you need to install mdma and create the arrarys... don't know it currently by heart how to do that.

Won't I lose all the data on the partitions if I do this?

The problem the server has is it gets a "invalid raid superblock magic" error and then drops out to a command prompt on boot.


Also if I pull the drives and use a external case to connect them to another system should I be able to mount the partitions?

---

### Post by hyper_ch on 2009-02-15
well, no clue about that invalid raid superblock... that sounds bad :(

---

### Post by fjgaude on 2009-02-15
I would think you can mount the drives, as drives, in another case and get the data off one or the other, yes!

I take it you are booting off the raid1 array?

Let us know how you are doing.

---

### Post by bthessel on 2009-02-15
Hopefully I will have a sata/ide to usb converter tomorrow and can try connecting one drive from each array to another machine and get the files from it. 

Yes, I had put my boot partition on a raid volume. Won't do that again! :) Next time I will put three partitions in a raid 5 on 3 drives and put my boot partition on a seperate drive.

---

### Post by fjgaude on 2009-02-15
Great and good luck!

---

### Post by bthessel on 2009-02-17
using a sata to USB converter worked and I could mount it on another computer. Thanks for the help.

---

### Post by fjgaude on 2009-02-18
Great... we learn something new each day.

---

