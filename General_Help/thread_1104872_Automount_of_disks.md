---
title: "Automount of disks"
date: 2009-03-24
forum: General Help
---

### Post by hardy2008 on 2009-03-24
Hello to all
I want to auto mount my disk in ubuntu 8.04. Can I do it?
Could someone please help me to do it.

---

### Post by srikkanth87 on 2009-03-24
check for disk manager from the repos  ....

---

### Post by Elfy on 2009-03-24
Can you post the result of

```
sudo fdisk -l
ls -l /dev/disk/by-uuid
```

Which partitions is it that you want to mount?
Do you want them on the desktop?
What do you want to call themm when they are mounted?

The information you need is here if you want to have a go yourself - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

