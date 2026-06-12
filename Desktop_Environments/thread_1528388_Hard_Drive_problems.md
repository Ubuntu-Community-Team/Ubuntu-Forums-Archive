---
title: "Hard Drive problems"
date: 2010-07-10
forum: Desktop Environments
---

### Post by Amy_1990 on 2010-07-10
I have a new western Digital 160 GB hard drive i hook it up but the bios doesn't see it so i downloaded the software e-z wd-drive that was the easy way of installing the drive on my computer but it didn't work.Would anyone know what i'm doing wrong.
the drive is spinning up so i know it's not toast the drive is
a wd 160GB sata drive i'm running ubuntu 10.04

---

### Post by mikewhatever on 2010-07-10
I also have a WD external hdd, which didn't require any installation. It just worked.
Can you connect yours, then open Applications->Accessories->Terminal and post the output of the following command:
```
sudo fdisk -l
```
Edit: Not sure why I assumed it was an external one.

---

### Post by Mr_VeRiTy on 2010-07-10
Maybe the drives jumpers (the 8 pins at the back of it that have little "jumpers" wrapped around select ones) are setting it to "master" and I don't think you can have two masters, if this is the case that remove your hard drive and look at the instructions on the label on the hard drive it should tell you how to set it to "slave"

---

### Post by Amy_1990 on 2010-07-10
Thanks you

The drive is internal not external i forgot to say that in my post i am sorry i ask wd for help but they said they didn't support linux and i didn't know were else to go

and the drive works fine on another windows pc but not on my ubuntu pc

---

### Post by mikewhatever on 2010-07-10
So, is that a SATA or a PATA hdd? In case it is a PATA one, you do have to deal with jumpers.

---

### Post by Amy_1990 on 2010-07-10
it's a SATA pc was bought new back in April.The drive was/is only going to be a storage drive.
[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=only")[IMG]http://www.qtl.co.il/img/trans.png[/IMG]

---

### Post by PRC09 on 2010-07-10
Couple of things to check,try different cables, try a different sata port if there are more than 2,in the bios make sure that the sata port you are plugging into is enabled and try setting to auto detect.

---

### Post by Amy_1990 on 2010-07-10
it is set to auto-detrct but i am not sure about the rest i'll need to check them and again thank you for helping me i'll post back after  i check those out.

---

### Post by NewDisciple on 2010-07-10
**I have had similar problems and it was always the sata cables. Sometimes wiggling the connectors will help and at other times I have had to replace a cable.**

---

### Post by Amy_1990 on 2010-07-11
No luck i even put new cable's on the pc and still had no luck WD says on there website to use E-Z drive 9.10wd to install the drive i don't think that is for my drive but at this point i am willing to try anything.

---

### Post by PRC09 on 2010-07-11
Just to be clear it is the bios (computer) that doesnt recognize it and not Ubuntu itself correct?????

---

### Post by Amy_1990 on 2010-07-11
Yes.I think i have it i entered the drive in the bios manually now i am going to run the wd install cd to format it.The cd is a live cd.I'M hoping anyway.wish me luck.

---

### Post by bruceleejr on 2010-07-11
I've had trouble with those freakn WD HD's too.
 
In bios:
Try an option to choose "Native IDE" "ACHI" "RAID" "SCISI" or "Compatibility" mode
 
I even remember trying to install XP on a SATA WD. Giving me BSOD's n everything, try messing around with the SATA modes, you'll get it

---

