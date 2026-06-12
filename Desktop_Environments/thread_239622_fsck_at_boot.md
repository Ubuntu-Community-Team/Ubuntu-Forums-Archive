---
title: "fsck at boot"
date: 2006-08-19
forum: Desktop Environments
---

### Post by janhenderson on 2006-08-19
I remember reading on the forums about setting fsck to check all filesystems on boot. I now read somewhere that this is not needed for journaled filesystems, such as ext3, which I'm using. Is this true? If so how do I cancel the instruction to fsck at boot, I forgot how I set it on, and I can't find the ubuntuforms thread though I searched for it. Thanks.

---

### Post by asplode on 2006-08-19
Well, by default it makes sure all the filesystems are 'clean' before mounting them, and every 30 reboots or so does a re-check of them.  This functionality shouldn't be disabled,e ven for journaled file systems.  30 reboots is quite a while, especially in linuxland, and shouldn't be too much of an inconvience... (twice a year?)  

Or have you changed the frequency and want to change it back?

---

### Post by janhenderson on 2006-08-19
> **asplode said:**
> Well, by default it makes sure all the filesystems are 'clean' before mounting them, and every 30 reboots or so does a re-check of them.  This functionality shouldn't be disabled,e ven for journaled file systems.  30 reboots is quite a while, especially in linuxland, and shouldn't be too much of an inconvience... (twice a year?)  

Or have you changed the frequency and want to change it back?

It's ok. I found out how to change it back. I previously edited the FSCKFIX to FSCKFIX=yes in the /etc/default/rcS file and it'll fsckfix it on every boot. My question was, is this needed to be done on every boot for an ext3 filesystem?

---

