---
title: "Root partition keeps mysteriously filling up.."
date: 2009-02-02
forum: General Help
---

### Post by inspired on 2009-02-02
Hi folks,
A few days ago my system more or less came to a halt. Anything that required writing to the root partition would not work. So Thunderbird could not send emails, nothing requiring sudo would work, etc.

I found out it was caused by / being full.
As I had a 16 GB root partition I found that pretty hard to believe but accepted it as I do install and try out a fair bit of software.

I followed instructions ([here]("http://ubuntuforums.org/showthread.php?t=140920")) and cleaned out perhaps 1 gig of stuff tops. The next day same thing happens. So I increase the partition to nearly 22 GB.
Today, same thing has happened again.
Now I know I have not added 6GB of stuff to my root partition in the last day.

So I start searching. I see this problem is not uncommon. Different causes are blamed. Some related to MythTV logs, others to Simple Backup putting stuff into root even though it was set to use an external drive. I have sbackup installed and also set it up to back up to an external HDD. I can't access the sbackup config gui though due to / being full.

I have read these bugs and posts:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/227753](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/227753)
[http://ubuntuforums.org/showthread.php?t=1051678](http://ubuntuforums.org/showthread.php?t=1051678)
[https://bugs.launchpad.net/ubuntu/+bug/217389](https://bugs.launchpad.net/ubuntu/+bug/217389)

And a few others. I found no answers.

I would be very grateful for some info on how to deal with this.

Also I don't understand the output of Disk Usage Analyzer. It has / a the top and says it is 100% full, with a size of 29.4 GB. Then it lists all the various folders one finds in root, along with /home and /media.
If I deduct the space /home and /media are showing, then I end up with something way way below the 21 GB of space my root has.

Something really is not making sense.

With thanks,

Jonathan

---

### Post by jerome1232 on 2009-02-02
So I take it you haven't figured out what's taking all the space, well let's take a look and see what folder is getting eatin that should lead us down the path to figureing it out.

```
sudo du -hx --max-depth=1 /
df -h
```

du - a command line **d**isk **u**sage estimator

-h - print the results in human readable form
-x - don't descend into other file system (so other disks won't get counted)
--max-depth=1 only show the top-level directory, makes the output easy to read

I'm thinking your external drive was unmounted while a backup ran, and that's what's causing the problems.

---

### Post by drs305 on 2009-02-02
> **inspired said:**
> 
Also I don't understand the output of Disk Usage Analyzer. It has / a the top and says it is 100% full, with a size of 29.4 GB. Then it lists all the various folders one finds in root, along with /home and /media.
If I deduct the space /home and /media are showing, then I end up with something way way below the 21 GB of space my root has.

Something really is not making sense.

That is just the way DUA works. The top entry always shows 100% once you have scanned something. It totals everything in the subfolders to come to 100%. It doesn't mean the system is 100% full.

To get accurate partition information on all *mounted* partitions, I use:
```
df -h
```
One advantage of the command is that it includes the space reserved for system use and counts it as "used".

Since you system is rapidly filling up, you might search for especially large files with:
```

sudo find / -name '*' -size +500M

```

If you think your trash bins are filling up (they take up space until emptied) you can find them all with this command:
```

sudo find / -type d -name *Trash*

```

The "Trash" link in my signature links to a tutorial for finding and deleting Trash, as well as other suggestions for locating large files and freeing up space.

---

### Post by inspired on 2009-02-02
Thanks Jerome,
That immediately showed me what was what. I also want you to know I appreciate you spelling out what the various settings on that command are doing. I shall make a note of these things for future use.

Yes... my /media folder has hit 16GB.
It looks like it is the same issue as one of the people I read on the net... whereby the mount point changed and sbackup started piling stuff into the actual /mount subfolder.
I have no idea why I didn't check that, after reading about this other guy having that issue. Oh yes. When I was reading that post earlier this evening I got the impression I must have uninstalled Simple Backup (I installed, tried, and removed numerous backup tools recently) because typing "simple-backup" (attempting to bring up a GUI) into the terminal I was told it is not installed and to apt-get it. I didn't know off hand that it is called sbackup, and when it said simple-backup existed, wasn't installed, and can be installed I figured that was the one.

Anyway...
Is there a way to stop sbackup from doing this? Seems like rather odd behaviour to me. The little beast! Is it too simple for its own good?
I am open to suggestions for a better backup system to (something GUI based... rsyncing and all a bunch of cron and command line stuff isn't something I feel like getting into for now... if I can avoid it;))

@DRS35
Thanks for the tips and info too. Much appreciated. I'll also check out the links in your signature.

Cheers,

Jonathan

---

### Post by inspired on 2009-02-02
Hmmm... me getting confused now. Here is the results of that command:

```
9.1M	/root
4.0K	/srv
4.0K	/mnt
16K	/lost+found
212M	/opt
0	/tmp
0	/proc
0	/sys
16G	/media
0	/dev
8.5M	/sbin
17M	/etc
4.3G	/usr
4.0K	/home
6.1M	/bin
479M	/var
205M	/lib
24M	/boot
21G	/

```

It shows 16GB in /media
I am assuming that's in the actual media folder (or a subfolder) and not a mounted device.

Yet... my Backups disk shows it is mounted to /media/backups_

There is about 18GB there.
Then there is a /media/backups folder (my original mount point that stopped being used when I ran into some odd permissions issues last week). That has only 361KB in it.

The above is showing 21 GIG in root. Is that the total size or used size?

Here are the results from $df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              22G   21G     0 100% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  372K  758M   1% /var/run
varlock               759M     0  759M   0% /var/lock
procbususb            759M  2.9M  756M   1% /proc/bus/usb
udev                  759M  2.9M  756M   1% /dev
tmpfs                 759M   12K  759M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              40G  9.8G   30G  25% /media/winxp
/dev/sda5              38G   19G   18G  51% /home
overflow              1.0M  1.0M     0 100% /tmp
/dev/mmcblk0p1        483M     0  483M   0% /media/disk

```

---

### Post by jimv on 2009-02-02
It's a lot easier to just go to Applications>Accessories>Disk Usage Analyzer.

---

### Post by drs305 on 2009-02-02
> **inspired said:**
> Hmmm... me getting confused now. 
It shows 16GB in /media
I am assuming that's in the actual media folder (or a subfolder) and not a mounted device.

Yet... my Backups disk shows it is mounted to /media/backups_

There is about 18GB there.
Then there is a /media/backups folder (my original mount point that stopped being used when I ran into some odd permissions issues last week). That has only 361KB in it.

The above is showing 21 GIG in root. Is that the total size or used size?

The 21GB / is the used size.

If you don't have anything mounted, the 16GB in /media or its subfolders is most likely a backup or file operation gone wrong. Normally a backup or such is made on a device mounted in /media. If the device isn't mounted there, the backup or other automated file operation will still take place. Instead of writing it to the device *mounted* in /media/XXX, it writes it directly to the /media/XXX folder. Thus it takes up space on your system partition instead of on the device you were expecting it to be saved to.

Normally users don't save things directly to /media. If you unmount all your devices your /media folder should be almost empty.

---

### Post by inspired on 2009-02-02
> **jimv said:**
> It's a lot easier to just go to Applications>Accessories>Disk Usage Analyzer.
Hi Jimv...
A lot easier than what, specifically?

I've been using baobab and whilst I find it useful, I am also finding these command lines handy.

Thanks,
Jonathan

---

### Post by jerome1232 on 2009-02-02
What's going on is your disk was unmounted, simple backup ran, when it saw there was no /media/backups folder (due  to the disk being unmounted) it created the folder and ran the backup, when  your disk mounted it saw that /media/backups existed and so mounted at /media/backups_ instead.

I think if simple backup could be set to not run if the backup destination doesn't exist it would solve this whole problem.

du didn't add anything in the other disks because of the -x flag, if you ran du without -x it will include your backup disk in it's estimation.


All you need to do is move all the files in /media/backups to /media/backups_ unmount the disc, then remount it, it should default back to it's /media/backups mount point.


-------------

As for a backup solution I know you said gui but this is so simple I love it.

If you make a script called autorun.sh on the top level directory of your backup drive. It will auto execute when you attach the drive. this is an example of my very simple script, it simply backs up my /home to /media/Backup/Jeremy.

```
#!/bin/bash
# an autorun backup script
gnome-terminal -x rsync -avh --delete --exclude=.gvfs ~/ /media/Backup/Jeremy
```

---

### Post by jimv on 2009-02-02
> **inspired said:**
> Hi Jimv...
A lot easier than what, specifically?

I've been using baobab and whilst I find it useful, I am also finding these command lines handy.

Thanks,
Jonathan

Easier than messing with command line commands.  It gives you a visual representation of your filesystem, and you can quickly drill down into directories to see what files/folders are largest.

---

### Post by inspired on 2009-02-03
Thanks folks.
I am very happy to have this sorted out so quickly.

Here's what I figured out (for anyone else who comes by here looking for answers)
[LIST]
[*]Simple Backup (sbackup) has an option to abort the backup if the destination directory does not exist. If backing up to an external disc, I recommend ticking this option. It's on the  Destination Tab. I have discovered, however, that on my system it does not hold this setting after setting it and saving. I will look into this as it seems to be a bug.
[*]The /Backups mount point had been created by sbackup when it didn't find the drive attached during a backup procedure
[*]When I took a look at who much stuff was in that directory it showed almost nothing. This is because the permissions set on it prevented me from seeing the content of the various backup folders.
[*]When I changed the permission (using $sudo chown -hR username Backups) I was then able to get the properties of the folder showing me the correct space (about 16GB in my case)
[/LIST]
The last point is a key one. This is what had stumped me. I could see a /Backups folder was there in /media folder (and it was not being used as a mount point for my Backups drive, that was now going to "/Backups_", and I could see it had some files in it, but using Nautilus properties on the folder, it showed only 360KB or something like that.

Again... thanks to Jerome, Jimv, Drs305 :KS

Jonathan   :popcorn:

---

