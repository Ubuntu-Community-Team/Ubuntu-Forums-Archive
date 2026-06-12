---
title: "Shifting /dev/sd ??"
date: 2012-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ltenny on 2012-01-18
OK..this is really strange. I have 4 Dell R415's with the H200 controllers, each with 4 2TB disks organized as JBODs. Nothing fancy. I have ubuntu 11.04.  I built these out a few months ago. I had to re-partition and create new file systems on the 3 disks on each machine. The disks are mounted on /ha1 /ha2 and /ha3 from partitions /dev/sdb1 /dev/sdc1 and /dev/sdd1, respectively. Everything looks great. Mounts great. BUT!! When I write a few files to the drives I get tons of I/O errors and when I do a ls -las /dev/sd* I notice that /dev/sdb /dev/sdc and /dev/sdd are gone! I now have /dev/sde /dev/sdf and /dev/sdg  What? No wonder there are lots of errors, the partitions have moved!  

Your first reaction, and mine: bad disks. Really? 12 bad disks in a row?

Things I've tried:
used both fdisk and parted to partition
used lots of different tools to find bad blocks, nothing found
updated the H200 firmware to the latest 1/12/12 release
tried a brand-new, strait from the factory disk, works great

Is there something about a new factory disk?

---

### Post by sisco311 on 2012-01-18
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by ltenny on 2012-01-18
yes..I'm using UUIDs in /etc/fstab...doesn't help.

---

### Post by ltenny on 2012-01-18
And..after I write to /ha1 /ha2 and /ha3 and they "shift" when I do 

sudo blkid

I get the UUIDs that were associated with /dev/sdb /dev/sdc and /dev/sdd now listed for /dev/sde /dev/sdf and /dev/sdg respectively.

---

### Post by ltenny on 2012-01-18
This may be related this bug [https://launchpad.net/+search?field.text=777441]("https://launchpad.net/+search?field.text=777441")


There appears to be a bug in the mptsas driver that re-maps drives from time to time...how nice ;-)

---

