---
title: "Deleted /etc/init.d/halt, can I get it back?"
date: 2009-06-21
forum: General Help
---

### Post by Pseudonomous on 2009-06-21
Hello everybody,

As noted above, I've accidentally deleted /etc/init.d/halt and would like to get it back without re-installing if possible;  anybody have any ideas?

I've tried re-installing the "initscripts" packages, as well as the "sysvinit" package; i've also tried "dpkg-reconfigure" and re-installing and reconfigure ubuntu-minimal, and ubuntu-standard, without any luck.

If push comes to shove, maybe someone could just post a Kubuntu /etc/init.d/halt script?

Edit:

Well; I've restored the file from a backup of my /etc folder (I'd forgotten I'd made one); I would still like to know if anybody knows a way to get the script if you don't have a backup.

---

### Post by clonne4crw on 2009-09-28
> **Pseudonomous said:**
> 
Well; I've restored the file from a backup of my /etc folder (I'd forgotten I'd made one); I would still like to know if anybody knows a way to get the script if you don't have a backup.

Boot a Kubuntu LiveCD, copy the file in it to a floppy or flash drive, and then boot back into the hard drive install to copy 'halt' back.

---

