---
title: "root 100% full but can't identify what's filling it !!"
date: 2009-01-11
forum: General Help
---

### Post by neill on 2009-01-11
hi

my server fell over today and i eventually worked out that / was full

```
neill@bowzer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              72G   72G     0 100% /
varrun                760M  220K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M   68K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
/dev/md0              587G  368G  190G  66% /home
/dev/sde1             925G  409G  469G  47% /mnt/backup
overflow              1.0M     0  1.0M   0% /tmp

```
this is a big shock as / is 7% full or something usually, so something's gone horribly wrong somewhere !

so i dig around and bizarrely i get the following

```
neill@bowzer:/$ sudo du -sh * |sort -nr | head
943M	var
550M	usr
409G	mnt
368G	home
212K	dev
150M	lib
36M	boot
20K	root
16K	lost+found
12K	media
```

/mnt is an externally mounted USB drive and /home is on a seperate RAID partition (sde1 and md0 above) so don't count

so why is / full ????

weird (or i'm just thick !)

any of you gurus any ideas ??

/neill

---

### Post by heindsight on 2009-01-11
try doing:
```
du -hx --max-depth=1 /
```
instead. The -x option ensures that du skips subdirectories on other filesystems so it's more useful to see where the space on / is being used.

---

### Post by drs305 on 2009-01-11
Take a look at this - it's about trash and other things that take up space unnecessarily. How to find it and how to get rid of it:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

The normal culprits are trash, large misplaced backup files, and log files.

---

### Post by lswb on 2009-01-11
You might want to try temporarily umounting the external drive and make sure the directory used as the mountpoint is empty. If the external drive was not connected or didn't mount for some reason then files could have gone into the mountpoint directory. Same thing is possible for /home I suppose though it's very likely an unmounted /home would go unnoticed!

---

### Post by neill on 2009-01-11
OK fixed it

/mnt/backup is a 1TB external drive backing up /home from a cron job

for whatever reason the job ran whilst the external drive wasn't mounted, so /mnt/backup was on sda2 and filled very quickly and efficiently with as much of /home as it could squeeze in

when i umounted /mnt/backup the mountpoint should be empty, but it wasn't, so i emptied it and remounted the drive and now

```
neill@bowzer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              72G  1.9G   67G   3% /
varrun                760M  224K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M   68K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
/dev/md0              587G  368G  190G  66% /home
overflow              1.0M     0  1.0M   0% /tmp
/dev/sde1             925G  409G  469G  47% /mnt/backup
```

ta da !!

thanks for the help everyone but especially kudos to lswb for being spot on the money !

/neill

):P

---

