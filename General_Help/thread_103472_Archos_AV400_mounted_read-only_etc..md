---
title: "Archos AV400 mounted read-only etc."
date: 2005-12-14
forum: General Help
---

### Post by Franko30 on 2005-12-14
Hi,

Here's my two cents concerning an **Archos AV400 100 GB** I own:

This one can only be mounted read-only in Ubuntu 5.04 and 5.10, no matter what I tried (even putting entries in fstab, mounting it explicitly read-write and other stuff).


*After re-formatting the whole thing (FAT32) in Ubuntu (GParted) it gets mounted read-write when plugging it in.*

Unfortunately, the player now only works on a Windows 200 machine - but not in Windows XP. The disc manager (correct term? I use a German Win XP) declares the file system as 'FAT32 - unknown'... And, the funny thing is that now I'm stuck with this, as Win 2K and XP only format 32 GB of my 100 GB as FAT32 and I don't have access to an old Win 98 machine. :rolleyes:

[COLOR="Blue"]Any ideas what might be causing this problem? Is it possible that this is because the re-format made a VFAT and not a real FAT32 file system? There seems to be a difference, at least I read that in the german Wikipedia.[/COLOR]

Cheers

Franko30

---

### Post by Franko30 on 2005-12-15
Hi,

[color=blue]I solved the problem - but only with the use of a Windows 98 machine of a friend the BIOS of which doesn't even recognize large discs...[/color]

I used MaxBlast available at

[http://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/popup_adp.php?p_sid=undefined&p_lva=1392&p_li=undefined&p_faqid=426&p_created=984524007&p_sp=undefined]("http://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/popup_adp.php?p_sid=undefined&p_lva=1392&p_li=undefined&p_faqid=426&p_created=984524007&p_sp=undefined")

I installed it on the Windows 98 machine and formatted my Archos with MaxBlast using FAT32.

Now the AV400 is read-write in Ubuntu and it is also recognized in WinXP...

Very very strange. :rolleyes:

**The conclusion: I don't really recommend the Archos AV400 for use in Ubunt. Although it comes pre-formatted with FAT32, it's not usable in Ubuntu 'out of the box' as it only gets mounted read-only... And it can't even play OGG Vorbis. If it only wasn't such a cute little gadget (watching and recording videos, big harddisc)...**

But still I'm wondering, what causes this FAT32 problem: For once the original FAT32 which Ubuntu believes to be read-only - and on the other hand Win XP not recognizibg the device after it was re-formatted FAT32 in Ubuntu.

Maybe some day I'll find somebody who can explain this.

---

