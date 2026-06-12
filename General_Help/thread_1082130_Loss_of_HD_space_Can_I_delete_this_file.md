---
title: "Loss of HD space: Can I delete this file?"
date: 2009-02-27
forum: General Help
---

### Post by utherpendragonfly on 2009-02-27
Yesterday I set up a new external HD and copied my home directory to it using Rsync. Everything went great, but later I noticed my avaiable internal HD space went from about 528 GB to 502 GB. What gives?
So I used Disk Usage Analyser and discovered this 40 GB file in /.local/share/Trash/files. I don't know if this has something to do with my missing HD space, but it seems like the biggest unaccounted for file I could see. Could anyone tell me what this is, and if I should delete it, and what (if not this) might have suddenly reduced my HD space yesterday?
Here are screenshots:

---

### Post by taurus on 2009-02-27
~/.local/share/Trash/files is your trash bin.

```
ls -la ~/.local/share/Trash/files
```

---

### Post by utherpendragonfly on 2009-02-27
That's weird. I guess I should have previewed the post. I don't know why no screenshots. I'll try again.

---

### Post by utherpendragonfly on 2009-02-27
> **taurus said:**
> ~/.local/share/Trash/files is your trash bin.

```
ls -la ~/.local/share/Trash/files
```

Good morning. The Trash Bin in my panel shows nothing in the trash. Can I just delete this using sudo chown? Do you have any idea if this is responsible for missing space?

---

### Post by utherpendragonfly on 2009-02-27
Oh, here is the output from terminal:
davey@davey-desktop:~$ ls -la ~/.local/share/Trash/files
total 8
drwx------ 2 davey davey 4096 2009-02-26 13:40 .
drwx------ 4 davey davey 4096 2008-10-21 11:06 ..

---

### Post by taurus on 2009-02-27
Looks like a system backup in root's trash bin.

```
sudo ls -la /root/.local/share/Trash/files
```

---

### Post by utherpendragonfly on 2009-02-27
> **taurus said:**
> Looks like a system backup in root's trash bin.

```
sudo ls -la /root/.local/share/Trash/files
```

Afraid I'm confused again! So if it's in Trash can I get delete it? I think those files from a couple of weeks ago are something I trashed using root command when I messed up with the previous internal HD.

---

### Post by utherpendragonfly on 2009-02-27
davey@davey-desktop:~$ sudo ls -la /root/.local/share/Trash/files
[sudo] password for davey: 
total 24
drwx------ 6 root  root  4096 2009-02-26 19:08 .
drwx------ 4 root  root  4096 2008-12-04 22:20 ..
drwxr-x--- 2 root  root  4096 2008-12-03 06:59 2008-12-03_06.2.58.38.644274.davey-desktop.ful
drwxr-xr-x 2 root  root  4096 2009-02-12 23:14 backup
drwxrwxrwx 2 davey davey 4096 2009-02-12 21:09 Backup
drwxrwxrwx 2 davey davey 4096 2009-02-12 21:09 Storage

---

### Post by taurus on 2009-02-27
> **utherpendragonfly said:**
> davey@davey-desktop:~$ sudo ls -la /root/.local/share/Trash/files
[sudo] password for davey: 
total 24
drwx------ 6 root  root  4096 2009-02-26 19:08 .
drwx------ 4 root  root  4096 2008-12-04 22:20 ..
drwxr-x--- 2 root  root  4096 2008-12-03 06:59 **2008-12-03_06.2.58.38.644274.davey-desktop.ful**
drwxr-xr-x 2 root  root  4096 2009-02-12 23:14 backup
drwxrwxrwx 2 davey davey 4096 2009-02-12 21:09 Backup
drwxrwxrwx 2 davey davey 4096 2009-02-12 21:09 Storage

See what's in 2008-12-03_06.2.58.38.644274.davey-desktop.ful.

```
sudo ls -la /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.ful
```
And yes, it's safe to empty the trash bin, removing it.

---

### Post by utherpendragonfly on 2009-02-27
> **taurus said:**
> See what's in 2008-12-03_06.2.58.38.644274.davey-desktop.ful.

```
sudo ls -la /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.ful
```
And yes, it's safe to empty the trash bin, removing it.

davey@davey-desktop:~$ sudo ls -la /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.ful
[sudo] password for davey: 
total 42765000
drwxr-x--- 2 root root        4096 2008-12-03 06:59 .
drwx------ 6 root root        4096 2009-02-26 19:08 ..
-rw-r----- 1 root root         221 2008-12-03 06:58 excludes
-rw-r----- 1 root root 43747213312 2008-12-03 11:21 files.tgz
-rw-r----- 1 root root     1308102 2008-12-03 06:59 fprops
-rw-r----- 1 root root       40960 2008-12-03 06:58 packages
-rw-r----- 1 root root         313 2008-12-03 06:58 partitions

I'm not sure what all this was from, but back in December I used Timevault, which ending up creating huge files that started filling up the HD (I screwed up some settings, apparently) and I got rid of it with help from this forum. Maybe this was left over?

---

### Post by taurus on 2009-02-27
You can safely remove the 2008-12-03_06.2.58.38.644274.davey-desktop.ful directory since they are all old stuff that takes up space especially the files.tgz.

```
sudo rm -rf /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.ful
```
Then, check your disk space again.

```
df -h
```

---

### Post by utherpendragonfly on 2009-02-27
Well, I think my Backup situation is in hand now using rsync to backup /home and I also copied /var/cache/apt/archives to the external HD. I thought I could do a fresh install when Jackalope is released.

---

### Post by utherpendragonfly on 2009-02-27
> **taurus said:**
> You can safely remove the 2008-12-03_06.2.58.38.644274.davey-desktop.ful directory since they are all old stuff that takes up space especially the files.tgz.

```
sudo rm -rf /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.ful
```
Then, check your disk space again.

```
df -h
```

Here's what I got:

davey@davey-desktop:~$ sudo rm -rf /root/.local/share/Trash/files/2008-12-03_06.2.58.38.644274.davey-desktop.fu
davey@davey-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             682G  145G  503G  23% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  120K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.8M 1010M   1% /dev
tmpfs                1013M  1.3M 1011M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             192G   72G  111G  40% /media/Back-up
/dev/sdb2             267G  188M  254G   1% /media/Storage

Though Nautilus still shows no extra disk space (502 GB).

---

### Post by utherpendragonfly on 2009-02-27
Before yesterday I had approximately 528 GB?

---

### Post by taurus on 2009-02-27
Have you restarted nautilus?

p.s.  Have a look in /var especially /var/backups to make sure you don't have anything large in there.

```
sudo ls -la /var
```

---

### Post by utherpendragonfly on 2009-02-27
> **taurus said:**
> Have you restarted nautilus?

No. That just occured to me after I posted that last post!
Thank you again for your help. I hope I won't need to bother you again for a while!

---

### Post by utherpendragonfly on 2009-02-27
Oh, by the way - The fdisk failed error on bootup I've had is now gone. Yay!!
Maybe the internal HD is OK for a while longer.

Have a great day!

---

