---
title: "Need to remove Ubuntu :( How to do it?"
date: 2009-03-29
forum: General Help
---

### Post by Duffking on 2009-03-29
I installed Ubuntu eee today and whilst I enjoyed it, It's messed up big time with the interface going completely haywire and after ages googling I can't even find anything remotely similar symptom wise, so I want to just forget I ever tried Ubuntu for the time being.

I used this method to install:

[http://www.simplehelp.net/2008/08/07/how-to-dual-boot-your-asus-eee-pc-900-with-windows-xp-and-ubuntu-linux/](http://www.simplehelp.net/2008/08/07/how-to-dual-boot-your-asus-eee-pc-900-with-windows-xp-and-ubuntu-linux/)

Before Ubuntu, I was using Windows XP, with a 40GB C drive and a 36 GB D drive. When I installed Ubuntu, I split D in more or less two.

From what I understand, this is what I should do?

- Start XP
- Go to the Computer Management in Control Panel
- Go to Disk Management

For some reason I see 5 partitions, my C and D. Then there's the 16.6GB one and a 784 MB one (No idea what that is, but when I boot to windows from GRUB, Ubuntu is an option for some reason, could that be it?). Both those are listed as 'Unknown (Healthy Partition).' The last is 32MB and is listed as 'EFI System Partition) 

So what goes and what stays?

Once that's gone, I presume I insert my XP disk and select repair? Will that then bring up a command line where I type 'fixmbr' to get rid of GRUB?

Apparantly I'll need the admin password for my disk, is that the password I use for my current windows account?

In fact, would it be better to simply remove grub FIRST then remove the partition?

Thanks all :( Will try again on a new hard disk next time rather than my own laptop :P

---

### Post by bytan on 2009-03-29
You may try "fixmbr" to get rid of Grub

And then, You may use Disk Management tool on windows to reformatting ubuntu's partitions..

---

### Post by Duffking on 2009-03-29
Thanks, MBR is gone :) And now the partition too, although the windows boot still says Ubuntu for some reason :/ Ah well. Will probably try again on a blank disk later this week.

---

### Post by bytan on 2009-03-29
If you have tried wubi before, thats normal to see an ubuntu entry on windows boot..
To fix it, you may check out boot.ini file on windows..

---

