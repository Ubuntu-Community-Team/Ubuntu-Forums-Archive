---
title: "Can't format hard drive"
date: 2009-03-25
forum: General Help
---

### Post by rolodoom on 2009-03-25
Hello. I have this problem

I'm trying to format my drive. It was using ext3 and I'm formating it to ext3.

I used gparted, which says that the drive was formated but when I rebooted the machine, and I couldn't see the drive. then I opened gparted again and then I realized that my drive is black and says that it's not formated.

¿How can I check if my drive is still working, find if it has bad sector or something?

Any help would be appreciated. I'm using Intrepid Ibex 64 bits

Thanks

---

### Post by evilaim on 2009-03-25
Well, make sure you have unmounted the drive before you format it, and you have to run the livecd to unmount the drive unless it's a secondary.

So, you put the livecd in, reboot, and say "try ubuntu..."

then use gparted, make sure the primary drive you want is unmounted by right clicking on it and selecting "unmount" then off you go.  Format it.

---

### Post by rolodoom on 2009-03-26
It's unmounted. I disable it from /etc/fstab.

I'm going to try with livecd

---

### Post by evilaim on 2009-03-26
alrighty... it will work.  have fun.

---

### Post by rolodoom on 2009-03-26
Nothing :-(

My disk is seagate. I checked the manufacturer's site and saw that ther is an utility called SeaTool. Is an ISO, I'm downloading it and going to test it.

Ther's also a Linux utility but is only for SCSI not SATA.

So, hope it'll fix it :-)

---

### Post by rolodoom on 2010-10-10
Drive was damage. Use the manufacter's program to fixed it but didn't work.

---

