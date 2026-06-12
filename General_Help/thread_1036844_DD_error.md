---
title: "DD error"
date: 2009-01-11
forum: General Help
---

### Post by triphazard on 2009-01-11
I have a particular hard disk in my system which had "bad superblock" errors and every now and again the data on that disk wasn't readable (often a reboot fixed).  Unfortunately I wasn't able to fix this by replacing the bad superblock with a backup so I ended up just reformatting the disk.

This was about three weeks ago now and the functionality of the disk is failing again so I figured there must be something wrong with it and ordered a new disk to replace it with.

Before I install the new disk though I want to make sure all data is destroyed on this disk so am attempting to use a combination of DDs to overwrite everything with /dev/zero, then /dev/urandom, and then /dev/zero again (a recommended cycle from somewhere on the internets).

However, my first attempt: -```
sudo dd if=/dev/zero of=/dev/sdc bs=1024 count=488386584
```

Failed with this output: -```
dd: writing `/dev/sdc': Input/output error
20553+0 records in
20552+0 records out
21045248 bytes (21 MB) copied, 39080.1 s, 0.5 kB/s

```

I'm just hoping someone can confirm that this error is likely to be happening because of a physical fault on the disk or, if not, maybe shed some light on it for me.

Thanks

---

### Post by caljohnsmith on 2009-01-11
Are you sure sdc is the drive you want to erase? You can check which are your drives by doing:
```
sudo fdisk -lu
```
Also, I would recommend using the dd command like:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Blue"]<drive>[/COLOR] bs=10M conv=notrunc,[COLOR="Blue"]noerror[/COLOR]
```
The "noerror" option means that dd will skip over bad sectors that it can't write to if I remember correctly. Just make sure to get the drive correct in the above command. :)

---

### Post by triphazard on 2009-01-11
> **caljohnsmith said:**
> Are you sure sdc is the drive you want to erase? You can check which are your drives by doing:
```
sudo fdisk -lu
```
Also, I would recommend using the dd command like:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Blue"]<drive>[/COLOR] bs=10M conv=notrunc,[COLOR="Blue"]noerror[/COLOR]
```
The "noerror" option means that dd will skip over bad sectors that it can't write to if I remember correctly. Just make sure to get the drive correct in the above command. :)

Thanks very much for the reply.  Yes, the drive is definitely /dev/sdc.  Wouldn't want to go wiping the wrong drive.

I'll try it again with the noerror option in a while and see what happens.

But the main thing I was after was whether this error looks to be down to faulty hardware

---

### Post by triphazard on 2009-01-12
Bump

---

