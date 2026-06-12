---
title: "Disk Usage Problems"
date: 2009-01-12
forum: General Help
---

### Post by piratejake on 2009-01-12
Hey guys, I apologize for my noobness but I'm having a little issue with the disk usage in my file system. I've got my Ubuntu partition on a 250 gig HD (dedicated only to Ubuntu btw). I switched to the OS about a month ago and haven't downloaded a lot since. I do have 60 gigs of music on the HD but that is pretty much the only extraneous stuff.

The issue is that I'm being told I'm out of free space but this clearly isn't the case. Here's a screenshot of the disk usage analyzer and the folders where it says I only have 5.9 megs of space and then when i get into the host file it says i have 157 gigs free (which is true but not what DUA says)
SS: [http://img110.imageshack.us/my.php?image=screennh1.jpg](http://img110.imageshack.us/my.php?image=screennh1.jpg)


I hope the solution isn't too painfully obvious and I don't awaken the wrath of the infamous flamers tormenting noobs.

Thanks in advance for the help!

---

### Post by hangfire on 2009-01-12
> **piratejake said:**
> 
The issue is that I'm being told I'm out of free space but this clearly isn't the case. Here's a screenshot of the disk usage analyzer and the folders where it says I only have 5.9 megs of space and then when i get into the host file it says i have 157 gigs free (which is true but not what DUA says)
SS: [http://img110.imageshack.us/my.php?image=screennh1.jpg](http://img110.imageshack.us/my.php?image=screennh1.jpg)


I can't view your image on FF3/Ubuntu 8.04.1.

Please post the output of: ```
df -k
```

-HF

---

### Post by piratejake on 2009-01-12
```
jake@ubuntu:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13457172  12769576      4004 100% /
tmpfs                  2027220         0   2027220   0% /lib/init/rw
varrun                 2027220       116   2027104   1% /var/run
varlock                2027220         0   2027220   0% /var/lock
udev                   2027220      2708   2024512   1% /dev
tmpfs                  2027220       592   2026628   1% /dev/shm
/dev/sda1            244195528  79618708 164576820  33% /host
lrm                    2027220      2380   2024840   1% /lib/modules/2.6.27-9-generic/volatile
overflow                  1024        48       976   5% /tmp
jake@ubuntu:~$ 

```

---

### Post by hangfire on 2009-01-12
> **piratejake said:**
> ```
jake@ubuntu:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13457172  12769576      4004 100% /


```

Your root disk is 100% full, and that is a problem. Ubuntu needs some breathing space to function properly.

Go to a terminal window:

```
sudo bash
cd /tmp
ls -l 
# Choose some old, large files, we'll call them <filename#>
rm -f *<filename1> <filename2> ...*
```

and so on. Go to /var/tmp and do the same thing. 

-HF

---

### Post by piratejake on 2009-01-12
i gave this a shot, but i believe i cleaned out /tmp ealier to no avail.

here's what i got:

```
root@ubuntu:/tmp# ls -l
total 0
drwx------ 2 jake jake 100 2009-01-12 17:00 keyring-7PPGsF
drwx------ 2 jake jake 520 2009-01-12 17:01 orbit-jake
drwx------ 2 jake jake  80 2009-01-12 17:00 pulse-jake
drwx------ 2 jake jake  60 2009-01-12 17:00 seahorse-MkTkxP
drwx------ 3 jake jake  80 2009-01-12 17:00 Tracker-jake.6260
drwx------ 2 jake jake  40 2009-01-12 17:00 virtual-jake.bLTt9j
root@ubuntu:/tmp# rm -f orbit-jake
rm: cannot remove `orbit-jake': Is a directory
```

i wish you could see my screenshot... it seems to me that the problem is the filesystem and home folder is full but once i get into the host folder i suddenly have 150 gigs free... it's like a somehow screwed up the partition or something, idk

---

### Post by drs305 on 2009-01-12
Following our brief PM for clarification, this is a wubi install inside windows. From my understanding, the wubi install creates a single, non-resizable file at the time of installation. Do you recall how much space you actually dedicated to the ubuntu install? It doesn't really matter how much space is on the drive, only how much you dedicated to the wubi file. 

I do not believe the file size can be changed. You could try to move any data files you might have that are within the installation to another location to free up space.

I wrote a tutorial on removing trash which sometimes clutters things up and takes away valuable space. The how-to includes other methods of removing extra files to create some space, so you might take a look at it and see if any of the techniques could help you in this situation.
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

Perhaps someone will come up with a way of increasing your wubi install but if not you will either have to live with the current size or reinstall with a larger /.

Wish I could give you a better solution. 

Welcome to ubuntu and the forums.

**Added:** See avolle's post below which provides a link offering a possible solution by moving the /home folder to a virtual disk.

---

### Post by ugm6hr on 2009-01-12
Probably an idiosyncrasy of Wubi (which I assume you used to install).

If you use Wubi, please make that clear with any support requests.

---

### Post by avtolle on 2009-01-12
piratejake, take a look at [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?) to see if this may be of help to you. Good luck.

---

### Post by piratejake on 2009-01-12
thank you very much, everyone. i'll dig into those pages and see what i can do. i'll report back when i've made some headway.

apologies for not mentioning the wubi install, note taken.

---

