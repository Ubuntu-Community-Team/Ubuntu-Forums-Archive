---
title: "disk image"
date: 2019-04-03
forum: Desktop Environments
---

### Post by m.eraj1995 on 2019-04-03
Hi Sir,

i want to create  a disk image of my OS i went to disk app and on the right side bottom clicked to the dotted line option and selected create image , but i am getting below mentioned error sir

```
[SIZE=2]Error unmounting /dev/sda1: target is busy  (udisk-error-quark, 14) [/SIZE]
```

---

### Post by yancek on 2019-04-03
Whatever is on sda1 is mounted and in use and you can't unmount a filesystem in use.  What is on sda1?

---

### Post by Rubi1200 on 2019-04-03
Hi and welcome to the forum m.eraj1995 :-)

I suggest booting with a LiveCD/USB and running the boot repair summary report to post here. Note, please do not do any repairs just the summary report which will tell us what is on your disks.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by m.eraj1995 on 2019-04-04
on my SDA1 is my root and home swap, i installed via the option is erase and install Ubuntu , so i didn't selected a something else option ,

---

### Post by Rubi1200 on 2019-04-04
As mentioned, you cannot unmount a filesystem in use.

Please follow the instructions from my previous post so we can get a better idea of what is going on.

Also, for the sake of clarity what disk app are you trying to use?

---

