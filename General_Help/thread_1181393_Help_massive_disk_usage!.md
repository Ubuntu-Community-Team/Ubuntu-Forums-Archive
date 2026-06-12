---
title: "Help massive disk usage!"
date: 2009-06-07
forum: General Help
---

### Post by hellzkeeper1216 on 2009-06-07
I ran an Free disk space cleaner on my Vista partition... It guess that it ran over to my ubuntu partition. the real problem is now that i had abour 20 gbs free now i have 4 kilobytes free. anyway anyone can help?

---

### Post by jerome1232 on 2009-06-07
Are you having a free space issue under Vista or under Ubuntu?

Nothing you ran while in vista *should* have had an impact on Ubuntu's free space. If the issue is no free space in Ubuntu can you post the output of a couple commands they might help figure out what is takeing up so much space and where.

df -h shows disk usage by partition and mount point in a readable form

du estimates disk usage and will print out a list of top level directories and show how much space they are using. This should tell you where the space is getting used at.

```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by hellzkeeper1216 on 2009-06-07
when i ran the code this is what i got

0	/tmp
12K	/mnt
72K	/media
13M	/root
245M	/lib
16M	/6d1de917960edfab18fb9ca8d8fb
0	/sys
du: cannot access `/home/jon/.gvfs': Permission denied
60G	/home
7.4M	/sbin
4.0K	/initrd
0	/proc
6.1M	/bin
30M	/boot
60K	/.Trash-0
3.7G	/usr
365M	/var
8.0K	/1914a0b2ff3053e11bf2
4.0K	/srv
4.0K	/selinux
26M	/opt
18M	/etc
8.0K	/b0435bbec64cbeebef
16K	/lost+found
0	/dev
9.3M	/e339e58fcef61b56551f1a33
92G	/


and for du -h
:~$ sudo df -h
[sudo] password for: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              97G   93G  827M 100% /
tmpfs                1009M     0 1009M   0% /lib/init/rw
varrun               1009M  120K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M  112K 1009M   1% /dev
tmpfs                1009M  348K 1009M   1% /dev/shm
lrm                  1009M   39M  971M   4% /lib/modules/2.6.24-20-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda2              83G   55G   29G  66% /media/disk

---

### Post by hellzkeeper1216 on 2009-06-08
*bumps* anyone? please?

---

### Post by jerome1232 on 2009-06-11
It appears to me that you have about 18GB worth of files just sitting in your root directory?

Check out your root directory are there some large archives or something just sitting there?

To open nautilus there from a command line you would do this

```
gsku nautilus /
```

Be very careful when you do that you have permission to delete any file on your system and you can destroy things easily if you go about changing system files willy nilly.

---

### Post by drs305 on 2009-06-11
If you find the offending files in / , remember these are owned by *root*. If you delete them from within nautilus you will need to use SHIFT-DEL to delete the files. Otherwise they will end up in root Trash bin, where they will continue to take up space.

Be careful on what you delete as SHIFT-DEL is not reversible.

You can read the guide on Recovering Lost Disk Space for ways to find out what is taking up the space. It is linked to in my signature line.

---

