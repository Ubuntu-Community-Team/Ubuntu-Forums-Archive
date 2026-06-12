---
title: "[SOLVED] Root partition suddenly full?"
date: 2009-01-01
forum: General Help
---

### Post by letired on 2009-01-01
A week ago, my 9.2G / partition had about 40% space left, then a few days ago it went to 23%. I'm fine with that, I'd just gotten networking back and updated a bunch of apps. But then yesterday I started getting the "caps+scroll lock flash" kernel panic, and G00gle searches told me it had to do with my wireless drivers.

I installed linux-backports-modules-intrepid which should have fixed the bug, but some hours later I instead run into another issue, the ["kernel 2.6.27-7-generic bug BUG: scheduling while atomic: swapper/0/0x00000100"](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285). 
The bug fix for this was to enable the intrepid-proposed repo and so I did, and I downloaded and ran the 2.6.27-11 kernel instead. I was also told to uninstall linux-backports-modules-intrepid as it wouldn't "work" (or have anything to do) with the new kernel anyway.

After this, I naturally had some updating to do; some 350M of data according to synaptic. After a reboot, however, / is stuffed. I had about 300 kernels to choose from in /boot/grub/menu.lst, so I removed the 2.6.22-x and 2.6.24-x ones in order to gain some space. Granted, I got about 150M back on / thanks to that.

My questions are; what happened to the ~2.5G of free space? I don't have any games installed, and with my download speed right now there's no way I downloaded 2G in three minutes.

I tried apt-get clean, it just finishes the command, there's no visible output. Maybe there shouldn't be any.

---

### Post by jerome1232 on 2009-01-01
Well, this ought to at least tell you where all the space is getting hogged at. Let's see if there's anything abnormal

```
sudo du -hx --max-depth=1 /
```

--edit-- A breakdown of that command

sudo - Super User Do, in this case we are running this command as root so we can analyze the files your user can't read normally as well.

du - this is a program that estimates  disk usuage

- h - Output bytes in a human readable form by displaying in KB, MB, GB etc..
- x - Tells the command to not descend into other filesystem's, this way we are  only analyzing the disk your root partition is on.

--max-depth=1 - This make the command only display the top-level directorys, it makes the out put readable.

/ - this is the directory we want to start at, your root directory.

---

### Post by exploder on 2009-01-01
Go into "Sessions" and turn off Tracker and Tracker Applet and your drive will stop filling up.

---

### Post by drs305 on 2009-01-01
Read through this tutorial for ways to find and delete hidden and root trash, as well as other ways to free up space and find large files that may be taking up a lot of space:
 
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by my_key on 2009-01-01
There's a useful gui utility called baobab that is really handy to see were all the space is gone. I think it's installed by default in ubuntu. Just run it and scan the root partition. It gives you a graphical representation of where all the space has gone.

---

### Post by letired on 2009-01-01
> **jerome1232 said:**
> Well, this ought to at least tell you where all the space is getting hogged at. Let's see if there's anything abnormal

```
sudo du -hx --max-depth=1 /
```

--edit-- A breakdown of that command

sudo - Super User Do, in this case we are running this command as root so we can analyze the files your user can't read normally as well.

du - this is a program that estimates  disk usuage

- h - Output bytes in a human readable form by displaying in KB, MB, GB etc..
- x - Tells the command to not descend into other filesystem's, this way we are  only analyzing the disk your root partition is on.

--max-depth=1 - This make the command only display the top-level directorys, it makes the out put readable.

/ - this is the directory we want to start at, your root directory.

Firstly, thanks everyone. Here's the output from the above command:

```
6.1M	/bin
0	/dev
17M	/etc
16K	/lost+found
3.6G	/usr
7.1M	/sbin
4.0K	/mnt
8.9M	/root
52K	/mobile
35M	/boot
288K	/tmp
4.0K	/home
4.0K	/opt
20K	/media
0	/proc
0	/sys
323M	/lib
4.0K	/initrd
12K	/Recycled
4.4G	/var
4.0K	/srv
8.3G	/

```

I ran find -size +700 and interestingly, these guys show up:
```
/var/log/syslog
/var/log/messages
/var/log/kern.log
```

Furthermore;
```
$ sudo find /var/ -size +200M
/var/log/syslog.0
/var/log/messages.0
/var/log/kern.log.0
/var/log/syslog
/var/log/messages
/var/log/kern.log

```

The bug I mentioned in the OP caused lots of nothings to be written to these files. Can i purge these files without screwing anything up?

---

### Post by cariboo on 2009-01-01
oops

---

### Post by cariboo on 2009-01-01
Look at your du listing and you can see that /var is using 4.4Gb. you probably have a lot of archived packages in there. To clean up the partiton a bit in a terminal type:

```
sudo apt-get autoremove
```

and just in case:

```
sudo apt-get clean
```

Jim

---

### Post by lensman3 on 2009-01-01
You can truncate (and start over) those files on a running system by (as root):


cp /dev/null /var/log/xxxx.log


This will truncate files that are open by other process.  I suspect that most of the log files are archived, that is, they have a date attached to the file name.  Just remove (as root) the names with a date.

Recall that Linux usually reserves 10% of a file system for its own use again as root.  That way there is always some spare drive space for it to do work in.  As soon as you free some space, find out what the error message that is being saved is filling up the HD.

---

### Post by letired on 2009-01-01
> **lensman3 said:**
> You can truncate (and start over) those files on a running system by (as root):


cp /dev/null /var/log/xxxx.log


This will truncate files that are open by other process.  I suspect that most of the log files are archived, that is, they have a date attached to the file name.  Just remove (as root) the names with a date.

Recall that Linux usually reserves 10% of a file system for its own use again as root.  That way there is always some spare drive space for it to do work in.  As soon as you free some space, find out what the error message that is being saved is filling up the HD.

I did this to the six files I specified in the last post ({messages,syslog,kern.log} and their respective .0-files) and now I'm back to 46% free space on /, without having anything explode yet. Thanks.
 
Just out of curiosity, for learning purposes and if you can spare the time, why does cp-ing something to /dev/null result in it being deleted (rather than just copied, and the copy being discarded) and how is this different from rm-ing those same files?

---

### Post by dcstar on 2009-01-01
> **letired said:**
> 
......
Just out of curiosity, for learning purposes and if you can spare the time, why does cp-ing something to /dev/null result in it being deleted (rather than just copied, and the copy being discarded) and how is this different from rm-ing those same files?

Copying null into a file effectively empties the file - but the file remains with all of its credentials etc.

Deleting a file deletes the file......

---

### Post by letired on 2009-01-02
> **dcstar said:**
> Copying null into a file effectively empties the file - but the file remains with all of its credentials etc.

Deleting a file deletes the file......

Duh, that was just me being stupid and getting the order of the targets wrong there (cp /dev/null /var/whatever rather than the other way around). Thanks.

---

