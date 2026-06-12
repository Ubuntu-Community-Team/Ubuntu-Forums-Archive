---
title: "Soft RAID startup"
date: 2009-05-04
forum: General Help
---

### Post by brettg on 2009-05-04
Hi all

I have a 3 drive raid 5 volume which works ok, don't panic. Well, it mostly works ok anyway.

The teeny tiny problem I have is that ever since something happened that may or not be related to a temporarily borked Jaunty upgrade the raid array won't start properly at boot.

The array is /dev/md0 but for some reason when I restart the system it tries to start up as /dev/md_d0. I think this may be related to a combination of the upgrade and the fact that I also have an external USB drive of the exact same capacity connected to the system.

It appears that /dev/md_d0 is attempting to start using two of the correct raid members plus the external drive.

If I do;

sudo mdadm --stop /dev/md_d0
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

Everything is fine so my question is how do I stop the system from  attempting to assemble the array using the wrong member drives at boot? 

I've checked /etc/mdadm/mdadm.conf but there is nothing interesting there.

As always, any and all advice is welcome and most appreciated.

---

### Post by fjgaude on 2009-05-04
Well, **mdadm** at boot assembles drives into an array that have identical UUIDs. If you run this command after assembling manually your /dev/md0 array and look at the UUID therein and compare to what's in the mdadm.conf file you likely will see something strange:

```
sudo mdadm -D /dev/md0
```

You might examine the USB drive and see its UUID by using this:

```
sudo mdadm -E /dev/USB
```

The /USB is the normal mounted name of the USB drive. If has a UUID identical to the array then you know something is fishy.

---

### Post by brettg on 2009-05-05
Thanks for the reply.

After taking a closer look through mdadm.conf I noticed that there was nothing listed under "definitions of existing arrays"

So, I ran mkconf which generated "ARRAY /dev/md0 level=raid5 num-devices=3 UUID=6c6f3939:0712b5a3:eb88a9ba:2f13f762"

I copied that string into mdadm.conf, restarted and bingo, the raid array came up properly.

Thanks for your help fjgaude

---

### Post by fjgaude on 2009-05-05
Great! Happy to see you got things going again.

---

