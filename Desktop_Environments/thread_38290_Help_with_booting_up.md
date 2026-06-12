---
title: "Help with booting up"
date: 2005-05-30
forum: Desktop Environments
---

### Post by JC4P on 2005-05-30
Ubuntu has been working greatfor me so far. but now each time i boot up today, it dosent work.
it work even go past "Starting Ubuntu" in ordinary boot up.
And in Recovery mode, it gives me either block errors, or journal errors, and it just freezes. i've done memtest's and it still wont work. any help?
P.S. I installed Point2Play / Cedega yesterday does that have to do with anything?

---

### Post by thrift on 2005-05-30
Looks like the file system is messed up.  Probably has nothing to do with your latest software installs.  Did the machine get cold powered off?  Try to boot up off of a Linux cd where you have a command prompt and try something like:

fsck.ext3 -p /dev/hdx1

with hdx being your root partition 

(primary master first partition hda1, 
primary slave first partition hdb1, 
secondary master first partition hdc1, 
seconday slave first partition hdd1)

It's also possible your disk could have died.  If you haven't had your power go out, this is likely.  You'll have to do your own testing to figure that out.

---

