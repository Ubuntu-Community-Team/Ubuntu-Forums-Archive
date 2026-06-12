---
title: "how set new ext3 partitions in fstab"
date: 2005-03-30
forum: Desktop Environments
---

### Post by iomicifikko on 2005-03-30
hi i was wondering  which velues put in options/dump/pass sections, i think something like this:

/dev/hda5 /mnt/folder   ext3   defaults           0         0

is that right?

EDIT: i just want to use them like usual partitions, not particular partitions of the usual linux tree, and i want them to be usable by any user so i thought simply to use default settings without the "nouser" option, like this:

rw, suid, dev, exec, auto, async (i just pasted the "default" option meaning without the "nouser" but i dunno the real meaning of suid/dev/async options, are they useful in a simple storing partition?)

thanks all

byez

---

### Post by lorap on 2005-03-30
hi!
of course friend you've everything done right.
but i propose you the directories represent your new partitions be created in /media directory,so once you go to Computer-->Disks,they'd be present there:-)
that's all!
have a nice day buddy!
pavel

---

### Post by iomicifikko on 2005-03-31
[QUOTE=lorap]hi!
of course friend you've everything done right.
but i propose you the directories represent your new partitions be created in /media directory,so once you go to Computer-->Disks,they'd be present there:-)
that's all!
have a nice day buddy!
pavel[/QUOTE]
 ahh i was just searching the option to get them appear or not there, i will create a link, thanks a lot!

bye

---

### Post by zoqaeski on 2007-12-09
Similar kind of question.

I had a FAT 32 drive for shared Windows-Ubuntu data, and that worked fine. It was set up back with 6.06, I think, so before Ubuntu included NTFS writing capabilities. It was (and indeed, still is) mounted as /mnt/edrive (E: Drive is what Windows called it), and I simply modified /etc/fstab to add the entry.

Now, I've recently realised I had an NTFS partition I don't really need, and I want to change it to an ext3 one for more data space. Repartitioning: No worries. Permanently mounting: Forget it. 
Ubuntu mounts the drive fine, and if I use sudo mount /dev/sda2 /mnt/morespace it works. But I can't get it to permanently mount with fstab (the uuid is something new that seems to have been added in since 6.06), and if I try to enter in the details by selecting Computer->37.12 GB volume (2) -> Properties -> Volume -> Mount Settings it says invalid character in mount point: /.
How can I go about fixing this and setting up /dev/sda2 so it mounts to /mnt/morespace on boot (preferably without a boot script).

---

