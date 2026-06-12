---
title: "[URGENT!] Maintenance shell wants root password"
date: 2009-02-06
forum: General Help
---

### Post by SamG22 on 2009-02-06
[B][COLOR="Red"]This post is now resolved.

A massive thank you to everyone who posted to help me, I really appreciate it.[/COLOR][/B]

Just that. I restarted my PC and it decided to force a disk check - or some sort of linux equivalent which I haven't seen before.

Apparently I have bad blocks. 7 of them, no less. Hardcore, right?

Anyway, the options available were to enter a root password so I could load up a maintenance shell and perform system checks and things, or to hit Ctrl+D to reset the system.

Incidentally, this process occurs if I load the normal OS or recovery mode.

Now, I don't remember my root password. I was pretty drunk when I set it up, which frankly opens up the possible range to a whole load of stupid sh*t. There doesn't seem to be any way to grab a command line to reset it though, as the only options I get are enter password or ctrl+d.

I tried the command line from the OS selection screen, but keep getting something like "error 32, needs to be authenticated" (I'm typing this from memory, please forgive any errors.)

If anyone can help without me having to reinstall the OS and lose several hundred GBs worth of data, I'd love you forever and bake you a pie.

EDIT: I've read the other entries on the forum to do with this kind of thing, but most assume that (a) you have a CD drive and (b) you can still access some aspect of Ubuntu - terminal or some sort of CLI to perform repairs. I can't, as far as I know.

EDIT 2: The error I get is similar to, <b>but not exactly</b>, this:

[COLOR="Red"]UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
          (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sdb1: 93% (stage 4/5, 395/611)

* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read only mode. 
*
a maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password for maintenance shell and restart the system.
Dive root password for maintenance(or type Control-D to continue):[/COLOR]

---

### Post by KeyserSoze93 on 2009-02-06
> **SamG22 said:**
> Just that. I restarted my PC and it decided to force a disk check - or some sort of linux equivalent which I haven't seen before.

Apparently I have bad blocks. 7 of them, no less. Hardcore, right?

Anyway, the options available were to enter a root password so I could load up a maintenance shell and perform system checks and things, or to hit Ctrl+D to reset the system.

Incidentally, this process occurs if I load the normal OS or recovery mode.

Now, I don't remember my root password. I was pretty drunk when I set it up, which frankly opens up the possible range to a whole load of stupid sh*t. There doesn't seem to be any way to grab a command line to reset it though, as the only options I get are enter password or ctrl+d.

I tried the command line from the OS selection screen, but keep getting something like "error 32, needs to be authenticated" (I'm typing this from memory, please forgive any errors.)

If anyone can help without me having to reinstall the OS and lose several hundred GBs worth of data, I'd love you forever and bake you a pie.

EDIT: I've read the other entries on the forum to do with this kind of thing, but most assume that (a) you have a CD drive and (b) you can still access some aspect of Ubuntu - terminal or some sort of CLI to perform repairs. I can't, as far as I know.

I think it means "Enter A root password", since recovery mode is for exactly the kind of situations when you can't get into the PC any other way. This new root password is so you can perform maintenance as root, so I think it can be anything...

---

### Post by SamG22 on 2009-02-06
> **KeyserSoze93 said:**
> I think it means "Enter A root password", since recovery mode is for exactly the kind of situations when you can't get into the PC any other way. This new root password is so you can perform maintenance as root, so I think it can be anything...

Afraid not...I tried a variety of things and it rejected them all...I think if had been asking for a new pwd it would have accepted the first thing I put in.

Thanks very much for your input though - this the third or fourth post I've made on these forums and the first to get a response!

---

### Post by neur0 on 2009-02-06
Do you get the grub menu ? (press esc on boot).
Did you set the actual root password before or just used sudo with your own password?

---

### Post by SamG22 on 2009-02-06
> **neur0 said:**
> Do you get the grub menu ? (press esc on boot).
Did you set the actual root password before or just used sudo with your own password?

I'm almost certain I set the root password as something, but whenever I used the CLI I always did sudo <mypassword>. 

The GRUB menu, if it's what I think it is, loads automatically on boot as I have an emergency 15GB windows XP partition, and it gives me the choice of where to boot to. 

Thanks for your reply as well :) Any suggestions?

---

### Post by 3rdalbum on 2009-02-06
In the GRUB menu, select your Ubuntu recovery mode line but don't press Enter. Press e, and then go down to the kernel parameters and press e again. This enables you to edit the options that get passed to the kernel when it boots.

You see a parameter there that starts with init= ? As in, it has "init=" and then a filepath. Change the filepath to /bin/sh. When the kernel starts, it will immediately go to a root shell instead of booting up the distribution. You might need to manually mount your hard disk read-write, but after that you should be able to use the "passwd" command to change your root password to something you will remember :-)

---

### Post by SamG22 on 2009-02-06
> **3rdalbum said:**
> In the GRUB menu, select your Ubuntu recovery mode line but don't press Enter. Press e, and then go down to the kernel parameters and press e again. This enables you to edit the options that get passed to the kernel when it boots.

You see a parameter there that starts with init= ? As in, it has "init=" and then a filepath. Change the filepath to /bin/sh. When the kernel starts, it will immediately go to a root shell instead of booting up the distribution. You might need to manually mount your hard disk read-write, but after that you should be able to use the "passwd" command to change your root password to something you will remember :-)

That sounds PERFECT, and you sir would happily be the recipient of some tasty cake. However, being the useless moron I am it doesn't seem to be working. A series of screenshots are attached below to show the various options I'm taking and their results:

(Also bear in mind I'm trying to replicate this on the Ubuntu VM I have running here at work, but the distro and build running on both my test VM, which is working okay otherwise, and the netbook I have at home which is borked, is identical I believe.)

Starting with:

[IMG]http://turtleupload.googlepages.com/Feb.0601.jpg[/IMG]

I push e and move down to:

[IMG]http://turtleupload.googlepages.com/Feb.0602.jpg[/IMG]

Which has an intial value of:

[IMG]http://turtleupload.googlepages.com/Feb.0603.jpg[/IMG]

Which I then change to:

[IMG]http://turtleupload.googlepages.com/Feb.0604.jpg[/IMG]

And on pushing esc from that screen and then b to boot, am faced with:

[IMG]http://turtleupload.googlepages.com/Feb.0605.jpg[/IMG]

----

Could you possibly shed some light on what I'm doing wrong? Thanks so much.

---

### Post by neur0 on 2009-02-06
Actually, he said
```
... go down to the kernel parameters ...
```
you went to initrd
And just edit the line , don't erase other parameters.
And it should probably be init=/bin/bash    not init=/bin/sh

---

### Post by SamG22 on 2009-02-06
> **neur0 said:**
> Actually, he said
```
... go down to the kernel parameters ...
```
you went to initrd
And just edit the line , don't erase other parameters.
And it should probably be init=/bin/bash    not init=/bin/sh

Thanks for your reply. There was no text apart from in the line I chose that has the text "init". The second line I tried appending init=bin/sh, or bin/bash, and then the third line just in case, but neither had the effect they were supposed to.

---

### Post by albinootje on 2009-02-06
> **SamG22 said:**
> Just that. I restarted my PC and it decided to force a disk check

Can you please boot from the Ubuntu installation cdrom, and use the "live session", then post the output of :
```

sudo fdisk -l

```
and do a manual file system check on your Linux partitions, like :
```

sudo fsck /dev/sdb1

```

---

### Post by SamG22 on 2009-02-06
> **albinootje said:**
> Can you please boot from the Ubuntu installation cdrom, and use the "live session", then post the output of :
```

sudo fdisk -l

```
and do a manual file system check on your Linux partitions, like :
```

sudo fsck /dev/sdb1

```

I sure can, but will need to do it later tonight when I get home. At work currently.

Can you suggest anything that would help with the gentleman's post above about changing the root pwd from the grub menu?

---

### Post by albinootje on 2009-02-06
> **SamG22 said:**
> I sure can, but will need to do it later tonight when I get home. At work currently.

Okay.
> 
Can you suggest anything that would help with the gentleman's post above about changing the root pwd from the grub menu?

I suggest you run file system checks on your Linux partition(s) first.

After that mount the Linux partition which is your / partition, and change the root password or, perhaps better, disable it.
Here's an example, let's assume your Linux / partition is on /dev/sda6, and you're using the "live session" of the Ubuntu installation cdrom :
```

sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6
sudo chroot /media/sda6
sudo usermod -L root
-> OR to change the root password again :
sudo passwd root
exit

```
Reboot without the cdrom after that.

---

### Post by az on 2009-02-06
> **SamG22 said:**
> Thanks for your reply. There was no text apart from in the line I chose that has the text "init". The second line I tried appending init=bin/sh, or bin/bash, and then the third line just in case, but neither had the effect they were supposed to.

> **SamG22 said:**
> 
Can you suggest anything that would help with the gentleman's post above about changing the root pwd from the grub menu?

You need to edit the line that starts with "kernel".  Just append "init=/bin/bash" to it.  There is no "init=" on it by default.  Do not use the initrd line (the line below) since that of something different altogether.

But it would be simpler to just boot the installation (live) cd, or any linux live cd and fix the filesystem from a shell there.

sudo fsck /dev/sdb1

If that doesn't work, obtain another hard drive and try some data recovery software before you attempt to "fix" the disk.  Image the faulty drive to another drive (or a file on another drive) and then try to fix the broken system on the new (working) disk.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by duds2008 on 2009-02-06
> **az said:**
> You need to edit the line that starts with "kernel".  Just append "init=/bin/bash" to it.  There is no "init=" on it by default.  Do not use the initrd line (the line below) since that of something different altogether.

But it would be simpler to just boot the installation (live) cd, or any linux live cd and fix the filesystem from a shell there.

sudo fsck /dev/sdb1

If that doesn't work, obtain another hard drive and try some data recovery software before you attempt to "fix" the disk.  Image the faulty drive to another drive (or a file on another drive) and then try to fix the broken system on the new (working) disk.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery) Shouldnt it be rw init=/bin/bash so as to overcome ro ?

---

### Post by az on 2009-02-06
> **duds2008 said:**
> Shouldnt it be rw init=/bin/bash so as to overcome ro ?

Actually, it doesn't make sense to boot into the failed filesystem.  You will need to unmount it to fix it and you won't be able to unmount it if you are using it. 

I suggest using a live cd.  I should have realized that earlier.

---

