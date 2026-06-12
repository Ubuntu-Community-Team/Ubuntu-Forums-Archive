---
title: "Need help with raid recovery"
date: 2009-04-30
forum: General Help
---

### Post by dlp21 on 2009-04-30
OK so I know it is late but I am hoping to get some help ASAP.

I need this fixed by friday morning EST.

So I just upgraded from 8.10 to 9.04.  Everything went smoothly except now my RAID is not mounting.

I have a 4 device Raid0 setup with mdadm.  The 4 drives are still flagged as raid however I can not figure out how to mount them.

All help is appreciated.

thanks
Dlp

PS I tried 

mdadm --assemble --force --scan
mdadm: no devices found for /dev/md/0
mdadm: /dev/md/0 assembled from 3 drives - not enough to start the array.

and I got this for

sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb1[1](S)
      488383936 blocks
       
unused devices: <none>

thanks again

---

### Post by fjgaude on 2009-04-30
Your old mdadm.conf file is no longer valid. Try this:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

That should do it, if not come back here and we'll try something else.

---

### Post by dlp21 on 2009-04-30
Tried it and this is what I got?  

```


sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
bash: /etc/mdadm/mdadm.conf: Permission denied


```

---

### Post by dlp21 on 2009-04-30
Ok, I think I got it.  For some reason sudo isn't working for me so I logged in as root and reissued the command and it accepted this time.  I rebooted and it appears that ubuntu is now rebuilding the raid.

Thanks so much...your awesome.

Dlp

---

### Post by dlp21 on 2009-04-30
So Ubuntu completely rebooted now and fcsk (I think) exited with an exit failure 4.

Man I thought that was going to work.  Back to the drawing board.

---

### Post by fjgaude on 2009-05-01
Was fsck checking the /dev/md0 array when it exited?

---

### Post by fjgaude on 2009-05-01
Was **fsck** checking the /dev/md0 array when it exited?

---

