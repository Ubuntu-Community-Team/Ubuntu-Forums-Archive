---
title: "Why cant I get ubuntu 11.10 to install?"
date: 2011-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KrisDeniseRiley1 on 2011-10-21
[SIZE=3]I have a xps m1330 with windows 7 ultimate. I have tried to install Ubuntu via wubi & the reboot process. Both ways end up with the same result, and thats not coming up with the boot loader screen asking with OS you want to load. What am I doing wrong? Im lost and have spent 7+ hours with this mess. Is it me, or Ubuntu?[/SIZE]

---

### Post by ugm6hr on 2011-10-22
I'm afraid I don't have any experience of Wubi.
But I can try and help with a dual-boot. Have you checked to make sure Ubuntu boots from a CD/USB into "live" mode?
Also - which version of Ubuntu are you using?

---

### Post by cozumel on 2011-10-23
Hi,

Are you trying to create wubi install (Ubuntu running inside Windows) or a dual-boot system (Ubuntu running alongside Windows)?

Either way, have you booted Ubuntu from CD you have created to confirm that everything works ok with your hardware?

Assuming that you are talking about a dual-boot configuration and that you have confirmed your system works with Ubuntu via CD, then have you created a partition into which Ubuntu can be installed?

If you have not created an empty partition for Ubuntu then I recommend that you do this with Windows (to avoid problems) and make it an extended partition. This will require you shrinking current partitions (also via Windows).

Warning! Making changes to Windows Partition risks loss of data and making system unusable. Ensure to backup everything first and defragment your Windows Disk

Thanks & good luck!! :)

Edit: Just realised. You have started two threads in the same Dell sub-forum for identical topics. Please don't do this. I realise you are seeking assistance, but please be patient and you will get an answer. I copied & pasted this post from your other thread to demonstrate how double-posting can waste time as both ugm6hr and myself have both essentially posted the same answers.

Thanks

---

