---
title: "I have a dilemma - hard drive mounting on boot"
date: 2009-06-22
forum: General Help
---

### Post by rsmseys on 2009-06-22
I have a dilemma... I have 3 hard drives, hard drive 1 is my linux. sda1(ext3),sda2(extended),sda5 (swap). Hard drive 2 is my /home sdb1 (xfs) and hard drive 3 is unpartitioned.

With hard drive 1 & 2 connected everything works fine. When I connect hard drive 3 while linux is running, and trying scanning for it (terminal$ dh -l) and searching for it with gParted, it can't find it at all. But when I reboot with it still plugged in, it says that my /home can't be found, and nothing works.

I think it's mounting hard drive 3 as sdb1 and then mounting my hard drive 2 as sdc1, and then when fstab is like "mount sdb1 as /home" and it does that, and then linux is like "where is all the config files?" 

How can I get it to mount hard drive 3 as sdc1 instead of mounting it sooner? (keeping in mind it can't find it when I plug it in while Ubuntu is running, and after reboot everything's broken). 

PS. I disconnect it and reboot with only HD1 and HD2 connected and it boots fine.

---

### Post by CatKiller on 2009-06-22
You could change the /home partition entry in fstab to use the partition's UUID instead of the device entry. Then it will always pick up the right partition no matter which order the drives are picked up in. You can find the UUID of the partition with ```
sudo vol_id --uuid /dev/sdb1
```

---

### Post by rsmseys on 2009-06-22
Thanks, but... 
```

linux:~$ vol_id --uuid /dev/sdb1
/dev/sdb1: error opening volume
```Edit: It's connected/working. And is picked up in GParted.

Edit 2: TEEHEE... I forgot to sudo. 

^_^ Thanks, I'll try that.

UPDATE: Thanks! It worked perfectly!

---

### Post by CatKiller on 2009-06-22
Glad to hear it. Sorry about the sudo oversight. I shall correct the original post. I didn't need it when I tested it because my user has block access for other reasons.

---

