---
title: "df -h showing 1G more drive usage than du -h?"
date: 2009-03-15
forum: General Help
---

### Post by sgreszcz on 2009-03-15
Hi there,

I'm trying to find out where all my hard drive space has disappeared.  I'm running Ubuntu server 8.10, and /dev/sda1 is a CF (compact flash) drive formatted with ext2.

When I run df -h on my main disk I get:

```
sgreszcz@247:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  2.8G  863M  77% /

```

When I try to find out which directories are holding all the files, I use du (showing only directories on /dev/sda1):

```
sgreszcz@247:/$ sudo du -h -x --max-depth=1
48K	./lost+found
301M	./var
4.0K	./cfsata
4.0K	./data
75M	./etc
8.0K	./media
146M	./lib
915M	./usr
4.6M	./bin
12M	./boot
0	./dev
17M	./home
8.0K	./mnt
0	./proc
56K	./root
7.1M	./sbin
36K	./tmp
0	./sys
4.0K	./srv
4.0K	./initrd
4.0K	./backup
4.0K	./video
1.5G	.

```

The du command shows that I am only using about 1.5 G, but the df command says that I am using about 2.8G.  Where has my other 1G gone?

Thanks in advance...

---

### Post by drs305 on 2009-03-15
Check the link in my signature line about deleted files in the trash bin and how they take up space until you empty trash. There are several trash bins on your ubuntu system so emptying only your user trash may not be enough.

There are some other things to check in the tutorial as well.

---

### Post by heindsight on 2009-03-15
It is normal for df and du to disagree about how much space is being used. For example, I have my /home on a separate partition, df reports that I'm using 410M in /home while du reports only 267M:

```
$ sudo du -hsx /home
267M	/home
$ sudo df -h /home 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.7G  410M  5.9G   7% /home

```

I recall recently reading an excellent article explaining how df and du work and why they often disagree about how much space is being used. Unfortunately I can't seem to find it again now.

---

### Post by heindsight on 2009-03-15
One possible reason for such a large discrepancy is if you have some files in your / partition which are currently hidden from 
```
du -x
```
because another filesystem is mounted over them.

From your du output, it would appear that your /backup is a mount point for some other filesystem. I'll use /backup as an example, but of course any mount point could be the culprit (it might even be more than one).

Let's say, for the sake of this example, that you usually have /dev/sdb1 mounted at /backup. Now suppose that at some point you tried to make a backup to /backup while /dev/sdb1 was not mounted. That would have written a bunch of data (perhaps as much as 1GB) to /backup (but the data would be in the /dev/sda1 partition). Now when you have /dev/sdb1 mounted at /backup then the files from /dev/sda1 in /backup are hidden.

When you run df, it looks in the filesystem metadata and sees how much space in the filesystem is being used -- that includes files that are hidden by having other filesystems mounted over them. When you use du however, it goes and actually computes how much space each file (that it can see) in the filesystem is using -- since du can't see files that have other filesystems mounted over them, it can't include the space they use in the output.

---

