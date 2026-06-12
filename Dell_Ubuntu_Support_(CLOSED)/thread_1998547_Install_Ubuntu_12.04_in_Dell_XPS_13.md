---
title: "Install Ubuntu 12.04 in Dell XPS 13"
date: 2012-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emagar on 2012-06-06
I just got a Dell XPS 13 (i5, 4GB ram, 128GB solid state drive). My other computers have a dual-boot partition with Ubuntu12.04/Win7. I'd like to install Ubuntu only in this machine.

Has anyone seen a description of the installation process? I've found many threads on fine-tuning the system, but very little on installation step-by-step.

Some issues I'd like to get feedback on include:

(1) Installing from a USB pen drive (I've always installed from a cd-rom, this machine has none)

(2) Partition recommendations for optimal performance (size for swap, for system, for data)

(3) How can the machine be recovered to its original state if so wished? (no recovery cds in this generation of machines)

Thanks in advance,

--emagar

---

### Post by luor_d on 2012-06-17
(1) Installing from a USB pen drive (I've always installed from a cd-rom, this machine has none)
- I installed from an USB drive. It is as easy as from cd-rom.

(2) Partition recommendations for optimal performance (size for swap, for system, for data)
- I installed dual OS, ubuntu and Windows 8.
My partition status here. [http://qing.weibo.com/1613373160/602a1ee833001mvd.html]("http://qing.weibo.com/1613373160/602a1ee833001mvd.html")

(3) How can the machine be recovered to its original state if so wished? (no recovery cds in this generation of machines)
- You need make a USB backup in windows, then Dell's win 7 image can be stored. However, you have to manual create iRST hibernate partition in win7 if you delete all partitions in ubuntu. And recovery partition cannot be recreated after deletion.

---

### Post by emagar on 2012-06-17
Thank you very much, luor_d, for your detailed reply. If I do no erase the win7 recovery partition and use the remainder disk for ubuntu's partitions, a win7 recovery in the future would require two steps: (1) creating manually a NFTS partition for installation and (2) running the recovery procedure. Right?

---

### Post by ohjaypee on 2013-01-31
Hi luor_d,

You said in reply to "(3) How can the machine be recovered to its original state if so wished?": 

"You need make a USB backup in windows, .... However, you have to manual create iRST hibernate partition in win7 if  you delete all partitions in ubuntu. And recovery partition cannot be  recreated after deletion."

However I read on Dell's community site here:
[http://en.community.dell.com/dell-blogs/dellsolves/b/weblog/archive/2012/08/02/restoring-your-computer.aspx](http://en.community.dell.com/dell-blogs/dellsolves/b/weblog/archive/2012/08/02/restoring-your-computer.aspx)

"The USB or DVD will format your hard-drive, create the appropriate  partitions, and restore your computer to its out-of-the-box factory  state."

By "USB" they are referring to the USB recovery device created using the recommended method - the Dell DataSafe program (XPS 13 ships with this app). I believe this is the same USB device you refer to?

I haven't tried it myself - but this says to me that a) it wouldn't be necessary to manually recreate the hibernate partition because the recovery utility will do this for you, and b) it's also possible to restore the "recovery" partition for the same reason. Ie. you can get back to original state using the USB recovery device.

What do you think? Am I understanding this correctly? Regards, Ollie

---

### Post by emagar on 2013-02-05
Thanks OhJayBee. I did create a USB recovery kit several months ago. But the machine runs very smoothly with Ubuntu, so I do not expect to re-install win7 soon.

---

