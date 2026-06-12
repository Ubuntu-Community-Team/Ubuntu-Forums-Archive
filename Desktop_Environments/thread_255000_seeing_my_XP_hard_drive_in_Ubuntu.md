---
title: "seeing my XP hard drive in Ubuntu"
date: 2006-09-10
forum: Desktop Environments
---

### Post by howardepgco on 2006-09-10
I just renewed my install of Ubuntu on my computer.On my old install I could see my XP hard drive on the Ubuntu desktop.This time I don't see it.Any ideas what is different?

---

### Post by varean on 2006-09-10
Try this:

```
$(root) fdisk -l
```
To see your partitions, find the one windows is on(ex: /dev/hdc1)

Then,
```
$ mount /dev/hdc1 /mnt
```
Replace /dev/hdc1 with your windows partition and tell me if you can read the drive.

---

### Post by howardepgco on 2006-09-11
ok I tried that and it seems it might work.I get this error however.I think it has to do with something else.Some root thing.

howardepgco@desktop:~$ mount /dev/sda /mntsda
mount: only root can do that

I bet if I solve this I can probably get it to work.
I sign in as sudo and give my password and I still get this error.

---

### Post by zachalekos on 2006-09-13
> **varean said:**
> Try this:

```
$(root) fdisk -l
```
To see your partitions, find the one windows is on(ex: /dev/hdc1)

Then,
```
$ mount /dev/hdc1 /mnt
```
Replace /dev/hdc1 with your windows partition and tell me if you can read the drive.

Tried thiss, but it doesn't do anything, or change anything.:-k

---

### Post by howardepgco on 2006-09-14
Thanks for the suggestions.I found this site that explained how to do it [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html). I did what was written and voila now I can see the Windows hard drive and listen to my windows mp3's with Ubuntu.Now just a few more things to get working then bye bye Windows!!:grin:

---

