---
title: "Kernel Panic Help"
date: 2009-03-02
forum: General Help
---

### Post by hibliss on 2009-03-02
Hello,

I have searched these forums and Google with little luck so far.

My system locked up when I connected a USB camera. After waiting 20 minutes, I hard reset it.

When it restarted, I was greeted with:

[10.205320] Kernel Panic - not syncing: Attempted to kill init!

So, I restart and attempt to load Ubuntu 8.10, 2.6.27-11-generic (recovery mode). I get this at the end:

Begin running /scripts/init-bottom...
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
Mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
/bin/sh: Can't open single
[10.399783] Kernel Panic - not syncing: Attempted to kill init!


So it seems that it is trying to resume from /dev/disk/by-uuid/........ but there is no resume image. I am under the impression it is trying to boot from the wrong HDD. I have bototed to liveCD just fine. 

I am pretty new to this, first time I had a major problem in Ubuntu. How might I go about changing the disk it boots from?

Thanks!

---

### Post by eldragon on 2009-03-02
first thing to do is boot from a livecd, and fsck the / filesystem

---

### Post by hibliss on 2009-03-02
> **eldragon said:**
> first thing to do is boot from a livecd, and fsck the / filesystem

Thanks for your reply. So I need to boot to LiveCD, go to terminal, and type "fsck /filesystem"?

Ok, it says:

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contaqins an ext2 filesystem (and not your swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternative superblock:
      e2fsck -b 8193 <device>

---

### Post by eldragon on 2009-03-02
> **hibliss said:**
> Thanks for your reply. So I need to boot to LiveCD, go to terminal, and type "fsck /filesystem"?

1. boot the live cd
2. open a terminal
type
```

$ sudo fsck /dev/sd[a1 a2 b1 b2]

```
where you should replace [XX] with whichever is your / partition

example, my root partition is /dev/sda1
so my command would be
```

$ sudo fsck /dev/sda1

```

and remember, the $ sign means run as a regular user, the # sign would mean run as root when talking about command line commands. you dont have to type those.

---

### Post by hibliss on 2009-03-02
Great.

I ran the command, which for me is on sdg1.

It says :

/dev/sdg1 contains a file system with error, check forced.
Pass 1: Checking inodes, blocks, and sizes

and I get a blinking cursor in the terminal window. I hear it reading the HDD, so I assume it is checking the disk and for now I just wait?

Also, thanks for explaining some of the basics of command line instructions and how you relay them.

Edit: Ok, now it is asking me if I want to Clone multiply-claimed blocks<y>?

File ??? (inode #467994, mod time Mon Mar 2 06:08:30 2009)
  has 1 multiply-claimed block(s), shared with 1 file(s):
	<filesystem metadata>
Clone multiply-claimed blocks<y>? 

Should I say yes?

---

### Post by eldragon on 2009-03-02
> **hibliss said:**
> Great.

I ran the command, which for me is on sdg1.

It says :

/dev/sdg1 contains a file system with error, check forced.
Pass 1: Checking inodes, blocks, and sizes

and I get a blinking cursor in the terminal window. I hear it reading the HDD, so I assume it is checking the disk and for now I just wait?

Also, thanks for explaining some of the basics of command line instructions and how you relay them.


yes, leave it be, if there are errors, it might take a while. and it might even not fix your problem which will make you force a reinstall.

i realized you needed some extra info on how to run the commands after you asked a bit more about /filesystem, it said much about what you knew ;)

for further reference, / = root filesystem, its where everything gets mounted. if its broken, the kernel image cannot be read, which is whats happening to you.

---

### Post by hibliss on 2009-03-02
Good to know how much my n00bness shines through :D

I edited the post above. Should I say yes?

Thanks.

---

### Post by eldragon on 2009-03-02
> **hibliss said:**
> Good to know how much my n00bness shines through :D

I edited the post above. Should I say yes?

Thanks.

i dont know much about how ext3 works, but if im reading correctly, it means theres a block referenced by many files, and it doesnt know who is the rightful owner, i would say yes to be on the safe side.

---

### Post by hibliss on 2009-03-02
The cause of the issue is clearly restarting without allowing the OS to properly shutdown. Shame on me I know.

Well it finished and I am restarting now. Will post back soon.

Did not boot, same error. Any more ideas?

---

### Post by eldragon on 2009-03-02
can you mount the partition with the livecd?

backup /home and format. thats all i can think of. and anyway, if you manage to get it working, you will never know what other side effects you will have from an unclean shutdown

---

### Post by hibliss on 2009-03-02
Yes I can mount the partition from liveCD.

I am looking at fstab now:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdg5 swap swap defaults 0 0

sdg5 is my swap partition, but how come my filesystem is not listed? Not by UUID or by name?

---

### Post by eldragon on 2009-03-02
> **hibliss said:**
> Yes I can mount the partition from liveCD.

I am looking at fstab now:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdg5 swap swap defaults 0 0

sdg5 is my swap partition, but how come my filesystem is not listed? Not by UUID or by name?

the livecd fstab file is for the livecd session.
the / partition there is actually a ramdrive.

to mount your hdd root partition:
```

$ sudo mount /dev/sdg1 /mnt

```

you will find your home in /mnt/home

---

### Post by hibliss on 2009-03-02
Ok, so this looks right:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdg1
UUID=3b72a934-a159-497c-a392-866c2cbb0988 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdg5
UUID=a501d0b6-dd47-d3b0-dc01-46394ba9bc91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

So if I backup my /home folder and reinstall, then restore it, how far along will I be? Will I need to reinstall my programs? 

I am obviously very new to this.

Thanks for all the support.

---

### Post by eldragon on 2009-03-02
yes, installing programs is a must.

but, after doing the initial install, all your settings will be there since they are all stored in your home.

if you wish to retain systemwide settings, you can backup /etc too and then move config files as you see fit (aka, install a program, remember you had modified a file in /etc, find it and restore your original version).

i wouldnt step over the entire etc folder just in case there is something wrong with the old one.

---

