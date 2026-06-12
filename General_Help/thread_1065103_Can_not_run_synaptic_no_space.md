---
title: "Can not run synaptic no space"
date: 2009-02-09
forum: General Help
---

### Post by Tom Atkins on 2009-02-09
I get an error message when I try to add an application that there is no disk space. Thae system monitor shows:
dev/sda / ext3 total 13.9 G, free 12.1 avail 0 used 13.8
 the same is shown for /home/tommy1/gvfs-fuse-daemon

What is the problem?

I forgot to say I am running HH with all updates applied

---

### Post by drs305 on 2009-02-09
To get a good idea of disk usage, run this:
```
df-h
```

Have you emptied your trash (and root's) lately? If not, see the link in my signature. It discusses how Trash eats up free space and gives other things you can do if your disk really is full.

---

### Post by Tom Atkins on 2009-02-09
My trash files are empty.

tommy1@tommy1-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   14G     0 100% /
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   48K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             676G   13G  629G   3% /home
overflow              1.0M   32K  992K   4% /tmp
gvfs-fuse-daemon       14G   14G     0 100% /home/tommy1/.gvfs
tommy1@tommy1-desktop:~$ 
```

tommy1@tommy1-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   14G     0 100% /
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   48K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             676G   13G  629G   3% /home
overflow              1.0M   32K  992K   4% /tmp
gvfs-fuse-daemon       14G   14G     0 100% /home/tommy1/.gvfs
tommy1@tommy1-desktop:~$ 

```

---

### Post by drs305 on 2009-02-09
The command verifies that / is full. Most often it is a backup that was made to a mount point rather than to a device that was *supposed* to be mounted (and saved to). Sbackup is often the backup program, although it isn't the apps fault.

You can do a search for large files with the following:
```

sudo find / -size +500M

```

You can also check all your directories to see which ones seem abnormally large:
```

cd / && sudo du / -h --max-depth=1

```

If you haven't emptied your cache of downloaded packages lately, you can also run:
```

sudo apt-get clean

```

---

### Post by Tom Atkins on 2009-02-09
I did run Sbackup. I ran apt-get clean and that seemed to solve the problem. I went ahead and deleted the the backup files as I have made a copy of them

Thanks for your help.

---

