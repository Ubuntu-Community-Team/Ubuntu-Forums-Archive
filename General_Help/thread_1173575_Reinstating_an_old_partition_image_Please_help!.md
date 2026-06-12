---
title: "Reinstating an old partition image? Please help!"
date: 2009-05-29
forum: General Help
---

### Post by Pipps on 2009-05-29
I took a backup of my system a few months ago, using PartImage on the SysRescCD, and saved it to my pendrive.

I have since reinstalled my system several times, and now have an entirely new local disk partition table to that when I originally took the aforementioned backup.

I would now like to reinstate my old Ubuntu backup onto my Ubuntu partition, in order to extract some old files from it.

I understand that if I attempt to reinstate this old partition image, the image is not likely to load. Something about UUIDs? Is this correct?

Please tell me what you think I should do to successfully reinstate my old partition image! Thank you.

---

### Post by Pipps on 2009-05-30
Can anyone help, please? :oops:

---

### Post by louieb on 2009-05-30
Can't think of any reason why it would not work. Are you wanting to boot to the old install or just copy files off of it with the current install? 

If you want to boot the old install you can use a  [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")  to boot it.

---

### Post by dandnsmith on 2009-05-30
The UUID bit is fixable, provided you have the tools (like a LiveCD  of a linux distro, or another linux installation on that PC).
The first thing is to re-instate the image,
then you have a go at the grub file to change the UUID refs to the new values (which you can ascertain: 
ls -l /dev/disk/by-uuid
findfs
blkid
 but I don't remember which would be easiest for you)

HTH

---

### Post by Pipps on 2009-05-30
Thank you for the advice.

I will attempt to use the Super Grub Disc, and I will report back with my findingins.

---

