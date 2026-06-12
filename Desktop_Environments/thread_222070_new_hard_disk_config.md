---
title: "new hard disk config"
date: 2006-07-24
forum: Desktop Environments
---

### Post by uantuzri on 2006-07-24
Hello,

I've just installed a a new hard disk. I format it using gparted with one partition using fat32, and I followed the instructions on [this guide]("http://www.tuxfiles.org/linuxhelp/fstab.html") about fstab. The problem is that linux is not able to write on it, even though I set the option to read and write.

The line I added to /etc/fstab is the following:
```

/dev/hdb1	/mnt/bigone 	vfat	auto,user,exec,rw,iocharset=utf8,umask=000 0	0
```

Can anybody help me with this? ](*,) 

Thanks

---

### Post by gerbman on 2006-07-24
> **uantuzri said:**
> Hello,

I've just installed a a new hard disk. I format it using gparted with one partition using fat32, and I followed the instructions on [this guide]("http://www.tuxfiles.org/linuxhelp/fstab.html") about fstab. The problem is that linux is not able to write on it, even though I set the option to read and write.

The line I added to /etc/fstab is the following:
```

/dev/hdb1	/mnt/bigone 	vfat	auto,user,exec,rw,iocharset=utf8,umask=000 0	0
```

Can anybody help me with this? ](*,) 

ThanksTry replacing your options list with the following:```
defaults,uid=username
```where username is your account name.

---

### Post by uantuzri on 2006-07-24
I found that the problem is not that it mounts the hard disk as read only: Initially, it is read and write available, but after some time, it 'turns into' read only... Strange

I try your config, gerbman, butit does'nt solve the problem.

The hard disk is physically mounted in the first IDE channel as slave, it has 250 GB and formatted as fat32 with a single partition. Any ideas?? :S

---

### Post by aysiu on 2006-07-24
I've seen this happen in two kinds of situations:

1. The FAT32 partition had something weird done to it by Windows--a read-only file or directory that screwed everything else up.

2. The partition is mounted to /mnt or /media

It looks as if it might be category #2. Try mounting it to /bigone instead of /mnt/bigone. See if that makes a difference.

---

### Post by wyohermit on 2006-07-25
> **uantuzri said:**
> The hard disk is physically mounted in the first IDE channel as slave, it has 250 GB and formatted as fat32 with a single partition. Any ideas?? :S


I'm probably showing my totla ignorance here as I have never used XP.  But I seem to remember reading something about a limit of 32g on a fat32 partition.  Is it possible that this is somehow involved.  If I am way offf base here feel free to enlighten me.

Ken

---

### Post by uantuzri on 2006-07-25
> **wyohermit said:**
> I'm probably showing my totla ignorance here as I have never used XP.  But I seem to remember reading something about a limit of 32g on a fat32 partition.  Is it possible that this is somehow involved.  If I am way offf base here feel free to enlighten me.

Ken

It might have something to do with this. I tryed the solution that aysiu proposed, and it worked  for some hours, but then it became again read only. 

I took a look in the wikipedia [about fat32]("http://en.wikipedia.org/wiki/Fat32#FAT32")  and I found this: 
The max size of a volume are 2 terabytes.
Windows limits the size of a fat32 volume to 32gb or 125 gb, not sure (when I tryed to format it in windows, it just recognized 125gb)... but to avoid that I did it in Ubuntu. Maybe it didn't work :(
The max filesize is 4gb.

The problem started when I began to use aMule, but the files it completes are'nt bigger to 4gb. Maybe the ones that are in progress.. Dont' know.:-k 

I used fat32 because I wanted to use this hard drive from both windows and Ubuntu, but if there's no solution to the problem  using fat32 and there's another way to do it, please, tell me. :confused: 

Thnakyou for your ideas.

---

### Post by aysiu on 2006-07-25
You can share off Ext3 and use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write it from Windows.

---

### Post by uantuzri on 2006-10-17
It happened again. The hard disk became read only after months. The problem came as it went. I think that I know what caused the problem: incoherences or bad sectors on the disk. I also think it was Windows the one that caused it, but that dicsussion is not for this thread. 

Anyway, I solved it by running on windows the following command

```
chkdsk /R F:
```

It took some time, but using the option on the hard drive properties panel didn't work.

I hope that thins might be useful for someone.

---

