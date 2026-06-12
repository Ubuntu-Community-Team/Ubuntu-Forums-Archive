---
title: "Home partition: reducing itself?"
date: 2010-11-17
forum: Desktop Environments
---

### Post by morefeo on 2010-11-17
On Lucid I made a separate partition for /home, which was of 10gb.

Then I installed Maverik few days after the release and now, if I check the /home partition properties it says: "4.3gb used, 2.6gb free space". So my question is: where did 3gb go?

Checked as root seems that lost+found folder is empty, I cannot find any file larger than normal...I just don't know where the space went.

Gparted shows 6.2gb is used and 3.11 is free space, 3gb are there, but Ubuntu doesn't show them.

Thanks for the help, if any.

---

### Post by oldfred on 2010-11-17
When you reinstalled did you use the lucid home? Perhaps a new one was created.

Just to confirm:

```
sudo fdisk -l
df

```

---

### Post by morefeo on 2010-11-17
Yep.

> /dev/sda5           60315       60802     3906560   82  Linux swap / Solaris
/dev/sda6           57843       60315    19859456   83  Linux
/dev/sda7           56627       57843     9764864   83  Linux

/dev/sda6             19547420   6229160  12325288  34% /
none                   1951684       296   1951388   1% /dev
none                   1958460      1160   1957300   1% /dev/shm
none                   1958460       212   1958248   1% /var/run
none                   1958460         0   1958460   0% /var/lock
/dev/sda7              9611492   6358608   2764644  70% /home



---

### Post by oldfred on 2010-11-17
df seems to agree with gparted. And looks correct.

I have not tried it as my /home is inside root but did you turn on show hidden files before checking properties? Maybe  it only counts what it sees.

---

### Post by morefeo on 2010-11-17
Event with it checked, shows wrong data :/

Maybe copy/format/paste from live cd would work?

---

### Post by asmoore82 on 2010-11-17
By default linux filesystems have reserved blocks to guarantee
system stability even when the disk becomes full. This is usually
totally unnecessary on a dedicated /home partition.

The command to tweak this setting on ext2/ext3/ext4 is `tune2fs`
```
man tune2fs
```

You'll be looking to run something similar to:
```
sudo tune2fs -m 0 /dev/sda7
```

---

### Post by morefeo on 2010-11-17
> **asmoore82 said:**
>  
```
sudo tune2fs -m 0 /dev/sda7
```

Now 4.3 used, 3.1 free. Still missing 3gb.

---

### Post by asmoore82 on 2010-11-17
Oh I see, you're not missing Free Space, you are missing used space.

I'm the same way - nautilus's calculation is way off.

du is right on though: ```
sudo du -sh /home
```

---

### Post by morefeo on 2010-11-18
Output:

> user@host:~$ sudo du -sh /home
du: no se puede acceder a «/home/user/.gvfs»: Permiso denegado
5,9G	/home


It's spanish, sorry for my english but it says something like...
"du: cannot access «/home/user/.gvfs»: Permission denied."

5,9 looks more realistic but it still miss 1gb, and nautilus is still showing 4,3gb (If you ask, I restarted nautilus by "killall nautilus").

The folder which root user has no access (.gvfs) is empty, and I cannot change its permissions through nautilus.

---

