---
title: "Unmounted HDD reappears after reboot!"
date: 2007-11-11
forum: Desktop Environments
---

### Post by xpronic on 2007-11-11
How do I stop this from happening? 

Also is there a way to unmount HDD's without logging in as root?

---

### Post by ofb on 2007-11-11
Let's back up a second - how is it being mounted on reboot? Is it listed in your fstab? Then you'd want to comment that line out. To have a look,

```
cat /etc/fstab
```

To change,

```
gksudo gedit /etc/fstab
```

If you're going to do anything more exciting than simply commenting out a line (by placing '#' at the beginning of the line) then you should make a backup copy of the file first.

```
sudo cp /etc/fstab /etc/fstabBAK
```

---

### Post by xpronic on 2007-11-11
It's listed in the fstab. When you say 'comment the line out', do you mean delete it lol? :/

This is what I got from typing fstab into the Terminal:
```
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=24c6deb0-d9cd-42a9-974c-a401c4db74d2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=80F0EE3DF0EE3954 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=DA8C30B98C30924D /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=8238FB4F38FB40A9 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb3
UUID=921CB6E21CB6C091 /media/hdb3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=8b6c5eed-fc1a-428f-845d-585764d62251 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
What do I change if I want to stop hdb1 & hdb3 from remounting after restarting my PC? :confused:

---

### Post by ofb on 2007-11-11
Lines that begin with a hash mark (#) are not read by the system. They are comments for whatever human is reading the file. Hence when we say "comment out", we mean placing a hash mark at the beginning of a line.

This is sometimes done instead of deleting a line in order to leave it there for future use, or for easy reversal of an experiment.

So to comment out hdb3, it would look like this

```
# UUID=921CB6E21CB6C091 /media/hdb3     ntfs    defaults,umask=007,gid=46 0       1
```

Next time you boot, the system will not read that line, so will not mount that drive.

That make some sense?

---

### Post by xpronic on 2007-11-11
Makes perfect sense, thanks. :D

I'm still getting used to the different terms and codes used for Ubuntu. :P

---

### Post by juje on 2007-11-14
I have a similar problem (delete a partition but didn't unmounted it before)...now every time i boot a get that same error...the difference is that the command line don't let me gksudo anything cause i'm working thru the command line...is there any way to comment that line thru the command line?
Thanks!

(sorry for my lousy english)

---

### Post by Caprica_Resistance on 2007-11-14
Hi everyone

You can just add **noauto** to line with parameters e.g.
UUID=921CB6E21CB6C091 /media/hdb3     ntfs    defaults,umask=007,gid=46 0       1

UUID=921CB6E21CB6C091 /media/hdb3     ntfs    defaults,umask=007,**noauto**,gid=46 0       1

the partition will not be mounted after reboot.

---

### Post by juje on 2007-11-14
Hi! thanks for the tip, but my question is how to do it...I mean, how do i comment that thru the command line (sudo@desktop: $), which command will let me comment the line without need to get into graphical interface?
I know how to do it thru the terminal, cause it'll appear the file itself (i mean the graphical interface)

---

### Post by Caprica_Resistance on 2007-11-14
sudo vim fstab
if you don't know how to use vim don't run it (you won't exit from it - probably;))

you can install midnight commander
sudo apt-get install mc

sudo mc
and edit file by f4 shorcut (mcedit)

---

### Post by juje on 2007-11-14
ok, thanks! i did it...now i'm a prosperous gutsy user...

---

### Post by ofb on 2007-11-14
Caprica_Resistance, how does using 'noauto' differ? 

I think the difference is that you can now do 'mount /dev/hdb3' and the parameters from the fstab, 'ntfs defaults,umask=007,gid=46,', will be applied. Also I'm guessing the final two fields for dump and fsck are obeyed for the umounted drive. But I don't know for sure. Would you elaborate?


juje,

You can also use nano for a quick editor within terminal which is less intimidating that vim. Run 'sudo nano fstab' to have a look.

For the commands displayed across the bottom, the displayed '^X' means 'Ctrl-x' on Ubuntu.

---

