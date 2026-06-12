---
title: "archive manager permissions"
date: 2008-12-07
forum: General Help
---

### Post by ekolimits on 2008-12-07
archive manager wont let me extract files to my sd card or anywhere else... what can i do... i heard of gksudo nautilus but i want to be able to extract any time i want or copy any time i want like on windows...is that possible? sorry, new to linux

---

### Post by taurus on 2008-12-07
What filesystem is your sd card?

```
sudo fdisk -l
```

---

### Post by ekolimits on 2008-12-07
i partitioned it into a fat16 and ext3 but i only want to access the ext3 through linux thanks for responding so quickly!

---

### Post by ekolimits on 2008-12-07
is it in the system>administration>authorization?
or in system>administration>users and groups?
these are just my guesses where to look

---

### Post by taurus on 2008-12-07
Do you know where the ext3 partition is being mounted?  You can change the ownership of that mount point from root to your login name so you can write to it without using sudo or gksudo.

```
sudo fdisk -l
df -h
```

---

### Post by ekolimits on 2008-12-07
ok i can see it on my desktop... or in my computer... but what is a mount point...

---

### Post by taurus on 2008-12-07
Mount point is where you mount your harddrive or partition to.  Let's say you mount /dev/sdb1 to /media/disk and you need to write stuff to /dev/sdb1.  Technically, you don't write it to /dev/sdb1.  Instead, you copy it to /media/disk.  If you see an icon on your desktop for that partition/drive, then you are looking at the mount point for that partition/drive.

---

### Post by ekolimits on 2008-12-07
ok so now where do i go from there?
would there also be a solution as login as root?

---

### Post by ekolimits on 2008-12-07
ok i went to the properties of the partition on my desktop... i found the mount point. /media/Whiite

---

### Post by taurus on 2008-12-07
If you said it's /media/Whiite, then I assume it is you wouldn't post the outputs of those two commands.  Assuming your login name is limit, you can change the ownership of /media/Whiite from root to your login name, limit.

```
sudo chown limit:limit /media/Whiite
ls -la /media
```

---

### Post by ekolimits on 2008-12-07
sorry, how do i type that in... it gave me a chowm "l" error

---

### Post by taurus on 2008-12-07
Open a terminal, Applications -> Accessories -> Terminal, and type the first line.  Then hit Enter.  Then type in the second line and hit Enter.

---

### Post by ekolimits on 2008-12-07
Thanx i got the code output that tells me i did it correctly... so everything mounts in root always? is there a way to change that... im opening archive manager right now to extract into whiite.

---

### Post by ekolimits on 2008-12-07
ok i got an error saying "null" what kind or error is that? i kept getting the same error... the file is a .tar.bz2 does that have something to do with that?

---

