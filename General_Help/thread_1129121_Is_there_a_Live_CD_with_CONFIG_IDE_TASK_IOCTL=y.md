---
title: "Is there a Live CD with CONFIG_IDE_TASK_IOCTL=y"
date: 2009-04-18
forum: General Help
---

### Post by steffi on 2009-04-18
I'm trying to wipe my X-25M and the best way to do that is with hdparm however it doesn't look like CONFIG_IDE_TASK_IOCTL=y is defined

I get SECURITY_ERASE: Input/output error 

when I try to --security-erase

---

### Post by danwood76 on 2009-04-18
Not with ubuntu.

DD will surely do the job you are looking for?
Mind you I wouldnt write to the entire SDD as you will shorten its lifespan.

---

### Post by steffi on 2009-04-19
The general idea is to avoid block writers and make use of the drives actual erase mechanism since then you aren't going to shorten the life of the drive.

> **danwood76 said:**
> Not with ubuntu.

DD will surely do the job you are looking for?
Mind you I wouldnt write to the entire SDD as you will shorten its lifespan.

---

### Post by eldragon on 2009-04-19
this thread might prove useful: [http://ubuntuforums.org/showthread.php?p=6024581#post6024581](http://ubuntuforums.org/showthread.php?p=6024581#post6024581)

---

