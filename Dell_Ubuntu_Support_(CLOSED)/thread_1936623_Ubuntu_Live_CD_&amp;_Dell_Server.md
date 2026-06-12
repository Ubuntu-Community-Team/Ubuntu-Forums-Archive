---
title: "Ubuntu Live CD &amp; Dell Server"
date: 2012-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by petrose on 2012-03-06
Hi All 
I need a little help, I hope this is the right forum. I'm trying to use Ubuntu Live cd to get some data off a Dell Server that has WIndows 2008 on it. The server has two hard drives in a Hardware based RAID 1 configuration. Ubuntu sees the drives as sda and sdb but I cannot seem to mount the drive. if I use something like mount -t ntfs /dev/sda1 /mnt/media
I get an error that I am mounting a wrong partition. Does anyone know how to mount these drives?

---

### Post by teward on 2012-03-06
The issue is probably the fact your setup is in RAID.  I have a similar problem with the hardware RAID5 in my PowerEdge server, but I dont have a solution to fix that :/

I have narrowed it down, though, that the issue is likely the fact Linux doesnt recognize the RAID array (which is highly possible).  I'm not sure how to make Linux recognize the RAID array, but I wanted to put my input on this issue.

---

