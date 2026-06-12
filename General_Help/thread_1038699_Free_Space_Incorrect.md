---
title: "Free Space Incorrect"
date: 2009-01-13
forum: General Help
---

### Post by gnelson on 2009-01-13
Ubuntu Server 8.10 running with gnome desktop installed.

Recently I had trouble logging into the desktop and realized that the 40GB hard disk showed full.  There doesn't appear to be a reason for this, as there is a second, 200GB drive that holds all of my data.  The 40GB is for the OS and home directory.

I deleted a few files so I could log in.

I've used the df command, which shows the disk 99% full.
I've used the du command which shows no directory that should account for anywhere near that space.
I did a reboot with fsck.

Any ideas, or any other information that I can provide to help?

---

### Post by whoop on 2009-01-13
It could still be that, well, your disk is full. As you have installed a window manager you could try and run Applications-->accessories->disk usage analyzer (Baobab) and see what is taking up all that space. 
Might be log files going berserk or whatever.

---

### Post by drs305 on 2009-01-13
You could have user trash or root trash that hasn't been removed and is taking up space. Here is a link about finding and deleting it. Of special interest would be #2 and #8 if it isn't a trash problem. They deal with other common factors and how to free up space.

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

If I had to guess I'd venture either a large delete or a backup to the wrong partition are most likely, but there are others as well.

---

### Post by gnelson on 2009-01-14
Thanks for the suggestions, but I'm still stuck.

1.  I emptied my trash and root's trash.
2.  I did the apt-get commands to recover space.
3.  I searched for large files (none over 500M).
4.  Log files looked okay.

Here's a screenshot of the baobob.

Note that "Total filesystem capacity" shows 33.3GB with 32.6GB used, while the graphical portion shows the root using 100% of available space with only 4.2GB used?!

---

### Post by drs305 on 2009-01-14
I find baobob (Disk Usage Analyzer) to be confusing in it's presentation. The top level will always show 100%, so it doesn't mean your system is necessarily full. 

Secondly, if it reports your system as much larger than it actually is, it may be reporting the 'virtual' contents of the .gvfs folder. If this is happening you may be able to turn it off by editing Preferences.  

A good command to review system disk usage is:
```
sudo df -h
```

---

### Post by gnelson on 2009-01-14
df -h results:

sda1 is my OS drive, sdb1 is my 2nd internal hard drive, sdc1 is my external HD for backups.

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              34G   33G     0 100% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  596K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  556K 1012M   1% /dev/shm
/dev/sdb1             183G  110G   64G  64% /media/disk
overflow              1.0M   64K  960K   7% /tmp
/dev/sdc1             294G  133G  146G  48% /media/server_backup_


```

---

### Post by unutbu on 2009-01-14
How about type
```

gksu baobab
```
Running baobab (disk usage analyzer) as root sometimes shows you different statistics than what you see when you run baobab as a normal user. 

In particular, perhaps look in /var/backups.

---

### Post by hangfire on 2009-01-14
Weird. Please post the output of:

```
sudo fdisk -l
```

-HF

---

### Post by jerome1232 on 2009-01-14
What about posting this

```
sudo du -hx --max-depth=1 /
## unmount those other partitions just to make sure 
## files aren't hiding under the mount point, and rerun
## that command with them unmounted, It could be that
## backup partition was unmounted and a backup happened
## while it was unmounted... 
```

---

### Post by gnelson on 2009-01-14
Ok, the gksu baobab helped find the problem, but I don't understand it.  I have an external hard drive that I use for backups.  I have it mounted to /media/server_backup.  Why is that taking up space in the filesystem?

See attached for the screen clip.

The output of fdisk -l is:
```

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93c1dc81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4377    35158221   83  Linux
/dev/sda2            4378        4866     3927892+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac918

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24181   194233851   83  Linux
/dev/sdb2           24182       24321     1124550    5  Extended
/dev/sdb5           24182       24321     1124518+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000fe3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux


```

---

### Post by jerome1232 on 2009-01-14
It was as I expected, your backup partition is mounted at /media/server_backup_

The folder that's taking up space is /media/server_backup

I'm guessing the backup partition was unmounted, a backup ran, when the backup partition was remounted it saw that the folder existed and auto-mounted to /media/server_backup_ instead of /media/server_backup as usual.

---

### Post by gnelson on 2009-01-14
> **jerome1232 said:**
> It was as I expected, your backup partition is mounted at /media/server_backup_

The folder that's taking up space is /media/server_backup

I'm guessing the backup partition was unmounted, a backup ran, when the backup partition was remounted it saw that the folder existed and auto-mounted to /media/server_backup_ instead of /media/server_backup as usual.

Outstanding!  That's it.

---

### Post by hangfire on 2009-01-14
> **gnelson said:**
> Outstanding!  That's it.

Don't forget to mark this thread as SOLVED, and I think Jerome deserves a Thanks!

-HF

---

### Post by gnelson on 2009-01-14
I absolutely would, but ...

 Re: [SOLVED] How do you mark threads
Quote:
Originally Posted by ethanay View Post
so, i don't see the option under "thread tools" for a thread that i started when i AM logged in. what now?
That feature has been temporarily disabled:
[http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

