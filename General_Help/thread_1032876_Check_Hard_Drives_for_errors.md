---
title: "Check Hard Drives for errors"
date: 2009-01-06
forum: General Help
---

### Post by jbrown96 on 2009-01-06
I just built a new system, and I wanted to "burn in" the drives. By "burn in" I mean, I run commands like ```
sudo dd if=/dev/urandom of=/dev/sda
``` a few times to make sure that it can write all the drives. I have two identical 640GB Western Digital Drives. I have run the dd command on both of them, but for /dev/sdb, it fails at 13GB both times I tried. The other drive is still chuging away. 

My question is: is there a better way to run these tests? **Are there any tools that can go block-by-block and write something and then try to read it back?** Should I RMA the drive back to Newegg?

I tried a rather cool program, although I don't know exactly what to make of the data, called GSmartControl that montiors the SMART capabilities of disk. For /dev/sdb, The "Attributes" section (contains the statistics), is red and has an value for "Current Pending Sector Count", which indicates an error. Does anyone have any experience with this program, and if so, how normal are these errors?

---

### Post by dcstar on 2009-01-06
> **jbrown96 said:**
> I just built a new system, and I wanted to "burn in" the drives. By "burn in" I mean, I run commands like ```
sudo dd if=/dev/urandom of=/dev/sda
``` a few times to make sure that it can write all the drives. I have two identical 640GB Western Digital Drives. I have run the dd command on both of them, but for /dev/sdb, it fails at 13GB both times I tried. The other drive is still chuging away. 
..........

Modern drives have the (limited) ability to detect bad blocks and remap them to a reserved area so you still have a functional unit - but I think that this process takes time and the dd program may well time-out while it is happening.

I would return the drive as it seems to have problems.

---

