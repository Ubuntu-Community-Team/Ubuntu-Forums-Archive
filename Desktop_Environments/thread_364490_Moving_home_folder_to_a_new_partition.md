---
title: "Moving home folder to a new partition"
date: 2007-02-18
forum: Desktop Environments
---

### Post by eeefresh on 2007-02-18
I am currently dual-booting with XP and Ubuntu on a machine with a 320 GB hard drive.  My current partitions look like this:

sda1 - XP partition (40 GB)
sda2 - Ubuntu 6.10 (25 GB, root directory)
sda3 - Linux swap (1 GB)
sda4 - Shared storage space (~ 240 GB, ext3 formatted)

The idea was to store all my data on sda4 and be able to read it with Windows or Linux (I am using the EX2IFS driver in XP and it seems to be working fine so far.)

I like the idea of having the home folder on a separate partition so I can make changes to my root partition without affecting my data.  However, I just noticed that my home partition is still in my root directory (/) and not on sda4 as I had originally intended.  I must have forgotten to designate sda4 as /home when I was setting everything up.

Is there an easy way to move the existing home folder on root over to sda4 without reformatting or reinstalling?

---

### Post by kspringer on 2007-02-18
Yup.  Check out this link:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

k

---

### Post by eeefresh on 2007-02-18
Thanks!  I knew I had seen that somewhere on the forums, but couldn't find it.

---

