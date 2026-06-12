---
title: "Need explaination of odd fsck behavior"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by john_abq on 2007-09-04
Hi 

I just recently purchased a DELL 530 inspiron with Linux pre-installed and been very happy with its performance, so far. 

I've encountered some odd behavior roughly every 23 to 24 times I boot up the machine. It seema that a force check on the machine is performed. Here is the text message on the screen:

[I]os-part has been mounted 23 times without being checked, check force
[/I]
At this point the system does a memory check on the harddrive and after about 10 minutes the login screen appears and everything seems to be normal.

I'm new to Ubuntu and the only time I've seen forced checks on a Linux system is when there is unclean shutdown of the computer.

Is this normal or peculiar to ubuntu and how can I make it stop?

Thanks.

John

---

### Post by neptho on 2007-09-04
This is normal for journaled filesystems.  If you wish to change the defaults, use 'tune2fs'.

Here's an example:

```
%sudo tune2fs -l /dev/sda4 | grep -i mount
Last mounted on:          <not available>
Default mount options:    (none)
Last mount time:          Mon Sep  3 11:04:58 2007
Mount count:              34
Maximum mount count:      36
%sudo tune2fs -c 255 /dev/sda4
tune2fs 1.40-WIP (14-Nov-2006)
Setting maximal mount count to 255
%sudo tune2fs -l /dev/sda4 | grep -i mount
Last mounted on:          <not available>
Default mount options:    (none)
Last mount time:          Mon Sep  3 11:04:58 2007
Mount count:              34
Maximum mount count:      255
```

---

### Post by john_abq on 2007-09-04
Hi Neptho-

Thanks for replying.

I tried typing : 

sudo tune2fs -l /dev/sda4 | grep -i mount

and got the following response.

[I]tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Couldn't find valid filesystem superblock.[/I]

I also tried this same command with the other sda* devices and got the same response.

Any suggestions?

-John

---

### Post by Dennis N on 2007-09-04
Check this thread for information on how to change the frequency:

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by john_abq on 2007-09-05
Thanks for everyones help.

I typed 'mount' to find the ext3 devices (which what I should have done in the first place).

After that I was able to change the maximum count to a larger number using the tune2fs command.

-John

---

### Post by notwen on 2007-09-06
There is also a tool which will let you post-pone any upcoming fsck.  It works great under Feisty.  Check out this [thread]("http://ubuntuforums.org/showthread.php?t=295262") for more info.  I've modified my routine fscks to every 45 bootups and also have Bonager running just in case I don't have time to let fsck check  all 150GB of data.  Hope this helps. =]

---

### Post by philinux on 2007-09-06
I reckon autofsck is better than bonager because it's just a script that checks on shutdown if the magic number has come up. Mines 36. 

> It's really quite simple, every time you shut down, AutoFsck finds information on your disks. Every linux partition has two important number associated with it, one is the number of times it has been mounted, the other is the number of times it is allowed to before being checked. AutoFsck looks at these, and if your drives are due for checking it asks if you want to check them. If you say yes, your drives are checked and your computer shuts down. If you say no, AutoFsck will ensure that the check will not run next time at boot. You will then be asked again the next time you shut down.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by notwen on 2007-09-06
Wowzers, didn't know about this script.  Thanks for the info. =]

---

### Post by neptho on 2007-09-06
> **john_abq said:**
> I also tried this same command with the other sda* devices and got the same response.

Any suggestions?

-John

You do not want to type what someone says explicitly, without checking for yourself.  I have my root device as /dev/sda4, which is not very normal.. yours is likely /dev/sda2, or otherwise:

```
%df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              81G   15G   62G  20% /

```

Replace /dev/sda4 with whatever your root device is, and ensure you're running sudo to have it execute as root.  You should be using ext3 partitioning, it is the standard.

---

