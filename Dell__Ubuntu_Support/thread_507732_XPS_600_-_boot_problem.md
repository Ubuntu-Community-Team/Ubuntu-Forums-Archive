---
title: "XPS 600 - boot problem"
date: 2007-07-23
forum: Dell  Ubuntu Support
---

### Post by 1uniquegeek06 on 2007-07-23
Hi,

I have an Dell XPS 600. I'm try to install Ubuntu onto my XPS system but I can't even boot an ISO cd-rom of Ubuntu 7.04 that I've download. I've tried my ways as in setting up my BIOS to boot from my CD-ROM first, it failed so I try to boot it from my SATA HDD (but then I'm not sure if I suppose to be doing that because I have Windows XP 64 bit installed there), last I've tried to boot it from a USB flash drive. All failed it just doesn't detected the source, I have 3 cd-rom drives, I've installed many programs fine but when it comes to installing another OS I've help issues. I'm even thinking of installing it to my Powerbook G4 labtop. Any suggestion or advice please advise. Thanks anything would be appreciated.

Nicky

---

### Post by Ek0nomik on 2007-07-23
Are you using the Ubuntu 7.04 Live CD?

Are you even able to see anything in regards to Ubuntu when you are booting?  From my experience (five computers from Dell) booting into a CD from the BIOS should be easy.  When you first turn on your computer, you will usually see a DELL logo loading screen.  On this screen you push F12 to change your BIOS options.  You then should be able to select to boot from your CD-ROM.  Make sure the Ubuntu CD is in the correct drive that you chose, and it should starting loading and present you with a few options (Live CD, Safe Mode, etc).

Just make sure you are selecting the correct CD drive and make sure Ubuntu is in the correct drive.

If it still won't detect it, trying out the Alternate CD may be worth a shot.  I installed two of my systems with Ubuntu via the Alternate CD.  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  (There is a checkbox below the green Start Download button to grab the Alternate installer)

---

### Post by 1uniquegeek06 on 2007-07-23
> Are you even able to see anything in regards to Ubuntu when you are booting?

I don't see anything regards to Ubuntu when I booted. I'll try the Live CD see if it works. I'll come back to post if it works or no work. The file that I download was the  7.04 for PC Edition, is that the Live CD? I'm not sure but I did download the Alternative one too.

Ek0nomik, Thanks for your help. :)

---

### Post by 1uniquegeek06 on 2007-07-24
I got home, I played around with the BIOS setting again ... I just change the booting sequences to CD-ROM as 1 and disable my SATA drive for now. It start booting from the CD ... YAHH!

I have another issue. I might go search for it on the forum. Maybe someone will answer me. I installed Ubuntu on another hdd because I got XP on my local C: drive. I want to dual-boot XP and Ubuntu but in the GRUB I don't see the option of choosing which OS to use. I check my C: drive I still see my files and document from XP. Is there something wrong, do I need to re-install XP?

Thanks.

---

### Post by Ek0nomik on 2007-07-25
> **1uniquegeek06 said:**
> I got home, I played around with the BIOS setting again ... I just change the booting sequences to CD-ROM as 1 and disable my SATA drive for now. It start booting from the CD ... YAHH!

I have another issue. I might go search for it on the forum. Maybe someone will answer me. I installed Ubuntu on another hdd because I got XP on my local C: drive. I want to dual-boot XP and Ubuntu but in the GRUB I don't see the option of choosing which OS to use. I check my C: drive I still see my files and document from XP. Is there something wrong, do I need to re-install XP?

Thanks.

How did you lay out your partitions?  GRUB should automatically allow you to boot into both OS's.

From the terminal you can run:

```
gksudo gparted
```

to view your partitions.

---

### Post by 1uniquegeek06 on 2007-07-25
HmMm ... when I got to partitions. It just listed my hdd I have and ask me to select which hdds I want to install Ubuntu. I selected my other second SATA hdd to installed it. :-k

I got it running ... no XP option in the GRUB. I'll view my partitions once I get home.

---

