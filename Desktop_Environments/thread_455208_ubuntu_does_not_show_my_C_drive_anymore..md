---
title: "ubuntu does not show my C drive anymore."
date: 2007-05-26
forum: Desktop Environments
---

### Post by legolas_w on 2007-05-26
Hi
thank you for reading my post
Ubuntu does not show my Drive C anymore.
Once it showed an error about dirty and ... and it does not show it.
I installed ntfs-3g-config (some thing like that) and its menu item appeard in applications? menu.

I can see other drives but not drive C, does any one know what should i do?

Thanks

---

### Post by taurus on 2007-05-26
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by init1 on 2007-05-26
Linux does not manages devices with letters. Your C drive could be on hda, sda, sdb, or something entirely different.

---

### Post by greeneemer on 2007-05-26
ntfs-3g will not show C: if you switched OS by just going into hibernation from Windows. This is to protect the hibernation file from being read/altered.

So,* if you haven't already*, go into Windows and shut it down properly by either rebooting or shutting down your computer and restart it again (the first should suffice).

---

### Post by legolas_w on 2007-05-26
hi
Thank you for reply.
I restart go to windows several times and it does not affect the problem.

here is output of

```

 sudo fdisk -li

```


```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       24792   147942585    5  Extended
/dev/sda5            6375       19122   102398278+   7  HPFS/NTFS
/dev/sda6           19123       24792    45544243+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   f  W95 Ext'd (LBA)
/dev/sdb3           15299       15492     1558305   82  Linux swap / Solaris
/dev/sdb4           15493       24321    70918942+  83  Linux
/dev/sdb5            7650       15043    59392273+   7  HPFS/NTFS
/dev/sdb6           15044       15298     2048256    7  HPFS/NTFS


```

meanwhile i have 5 NTFS partition in places and i am sure that at least first partition of first hard disk is not show and i want it to be there.


Thanks

---

### Post by taurus on 2007-05-26
Is /dev/sda1 your C: drive?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sd1
df -h
```

---

### Post by Ubivetz on 2007-05-26
Edit your /etc/fstab and type something like this (create /media/sda1 first)

/dev/sda1 /media/sda1 ntfs-3g umask=0,sync,defaults 0 0

---

### Post by legolas_w on 2007-05-26
Hi
Thank you for reply.


here is output of your command

```

sudo mount -t ntfs-3g /dev/sda1 /media/sd1

```


```

legolas@legolasPC:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sd1
Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume Windows and turned it 
off properly, so mounting could be done safely.


```

but i am sure that my drive is not hibernated, what can i do?

Thanks

---

### Post by taurus on 2007-05-26
You need to boot into Windows and shut it down properly first.  Then, see if you can mount it from Ubuntu now.

---

### Post by melbBoy on 2007-06-06
> **taurus said:**
> You need to boot into Windows and shut it down properly first.  Then, see if you can mount it from Ubuntu now.


Hi there,
I have a similar problem with the TS (thread starter). I try your method and thank God it's working!!

Cheers mate, I register to this forum only want to say thanks for this simple and yet very helpful for a newbie like me.

---

