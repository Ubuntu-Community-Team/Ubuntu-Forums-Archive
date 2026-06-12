---
title: "Issue with soft-raid at boot"
date: 2009-05-22
forum: General Help
---

### Post by germanguy on 2009-05-22
I just upgraded from 8.04 to 9.04. Under 8.04 I ran a soft-raid array without any problems. After the upgrade however, the boot process will quit out with the message "error could not find /dev/md1". I then get dumped into the intramfs console. 
Using the command "mdadm --assemble --scan;exit" I can get the system to boot and run without any problems. I do however have to repeat this step every time I boot up. I was wondering if there was any more permanent solutions to this problem?

---

### Post by GrimRe on 2009-05-22
try this:

```
mdadm -Esb /dev/md1 >> /etc/mdadm/mdadm.conf
```

this is essentially writing the Examine and scan output to the mdadm.conf file.

also make sure md1 is in your /etc/fstab file

---

### Post by germanguy on 2009-05-22
The command mdadm -Esb /dev/md1 gives no output whatsoever. The current contents of my mdadm.conf is: 

DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=76cc6924:fa190e30:75906d73:b88d872
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c394bd77:5c5dd0c8:fa502f57:2c69abd
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=bc8a268b:487aaee6:15f0b3d2:4907685
MAILADDR root

My fstab is also corectly configured. The problem lies in the arrays not assembling properly at boot.

---

### Post by LO Matt on 2009-05-22
Ran into this upgrading as well.

Read this:  [http://ubuntuforums.org/showpost.php?p=7220050&postcount=19](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19)

---

### Post by germanguy on 2009-05-23
All that seems to do is add a duplicate entry to my mdadm.conf, adding exactly the same lines that were already written into it, as a second set.

---

