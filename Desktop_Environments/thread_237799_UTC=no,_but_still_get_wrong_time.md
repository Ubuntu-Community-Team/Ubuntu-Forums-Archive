---
title: "UTC=no, but still get wrong time"
date: 2006-08-16
forum: Desktop Environments
---

### Post by registering on 2006-08-16
Hello. I dual-boot XP and Ubuntu. My Windows date/time is always correct, my Ubuntu time is always wrong. I can sync to an ntp server and it's correct, but as soon as I reboot it's wrong again, and I don't want to rely on a NW connection to gaurantee correct date/time. I have UTC=no in /etc/defaults/rcS already. Any ideas? I'd prefer to not set the BIOS for timezone.

---

### Post by cprise on 2006-08-19
I have the same problem, only in my case its Xandros Linux and SUSE that always get the time right. Kubuntu always gets it wrong. I am in USA ET and Kubuntu puts the time four hours earlier than it should be.

Rebooting the system with the incorrect time like this has already cause a processing task that I keep running in the background to catastrophically fail. The backup I had was 5 days old, so that's five whole days of processing time lost.

Does anyone have a fix for this before I give up on this distro???

---

### Post by Dar on 2006-08-28
I also get the wrong time but have no idea where to start. I have just installed Ubuntu but I find that if I want to set the time in Ubuntu to the correct time it screws up my Windows time by 10 hours (and vice versa if I set the time in Windows). I live on the Eastern side of Australia so the GMT time offset is +10 hours. 

Anyone find a fix yet?

Edit: I am running Ubuntu on a SATA HDD and Windows XP on an IDE drive. I have BIOS set to boot SATA first, where the grubloader is installed and I can choose which OS to boot.

Edit 2: Found solutions here: [http://www.ubuntuforums.org/showthread.php?t=219340&page=2](http://www.ubuntuforums.org/showthread.php?t=219340&page=2) (last post)
and here:
[http://www.ubuntuforums.org/showpost.php?p=971060&postcount=6](http://www.ubuntuforums.org/showpost.php?p=971060&postcount=6)

---

### Post by Jott on 2006-08-28
I had the same problem, and fixed it by editing etc/defaults/rcS to say utc=no, and then unchecking the 'set time automaticly' box in the adjust date/time dialouge.  I'm not really sure, but I suppose that it's also possible that you might have some kind of time syncronization software running in windows that keeps screwing you up.

good luck!

---

### Post by Dar on 2006-08-28
> **Jott said:**
> I had the same problem, and fixed it by editing etc/defaults/rcS to say utc=no, and then unchecking the 'set time automaticly' box in the adjust date/time dialouge.  I'm not really sure, but I suppose that it's also possible that you might have some kind of time syncronization software running in windows that keeps screwing you up.

good luck!

Cheers dude :) That seems like the fix then, time to boot up Ubuntu :D

---

### Post by viejogringoso on 2007-03-13
Already posted this to "System clock stuck in UTC"

Had the same problem on dapper.
Turned out the symbolic link /etc/localtime was missing.
Did the following from console:

sudo ln -s -f /usr/share/zoneinfo/America/New_York /etc/localtime

All better now.

Note that the -f forces an overwrite in case /etc/localtime does exist.
Also note that the command is case sensitive.

Of course you will have to replace /America/New_York
by selecting your time zone from those provided in /usr/share/zoneinfo/.

Adios

---

