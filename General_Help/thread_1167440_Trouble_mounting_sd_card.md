---
title: "Trouble mounting sd card"
date: 2009-05-22
forum: General Help
---

### Post by PhoHammer on 2009-05-22
I have had some trouble with writing to an sd card after using image-creater to put an OS image on it (moblin v2.0)

I repartitioned it with fdisk, but now it won't even mount.

I have attached a screenshot that might help you guys see what is going on.

So how  do I fix this thing?

---

### Post by taurus on 2009-05-22
How about

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by PhoHammer on 2009-05-22
That's over my head so I'll let you look at the screenshot:

---

### Post by taurus on 2009-05-22
Are you able to mount it in windows since it looks like you have windows on the harddrive--dualboot?

---

### Post by PhoHammer on 2009-05-22
That is a remnant of a botched dual-boot (Vista wouldn't defrag "enough", made me mad so I just installed xubuntu anyways) and I am not sure why it is there...

---

