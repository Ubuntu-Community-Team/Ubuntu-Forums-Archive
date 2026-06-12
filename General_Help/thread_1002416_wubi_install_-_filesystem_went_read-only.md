---
title: "wubi install - filesystem went read-only"
date: 2008-12-05
forum: General Help
---

### Post by jubilantjeremy on 2008-12-05
Hey guys

I've got a wubi install of ubuntu 8.04 on my girlfriend's PC. Something "happened" (unclean shutdown?) and the filesystem went read-only to prevent damage.

The problem I'm having now - **how can I make the filesystem rw again?**
I can get into root shell via recovery mode, and can open fstab up for editing, and change the -ro back to -rw. But I can't save it, obviously.

In the bootup messages, I see lines such as :
> 
start-stop-daemon: Unable to open pidfile '/var/run/klogd/kmesgpipe.pid' for writing: Read-only file system (Read-only file system).

and
> 
chown : changing owndership of '/var/run/klogd': Read-only file system


I just did a chkdsk on the windows partition, in the vague hope that it would sort it out - but no high hopes there. 
I googled, but couldn't find anything specific to the problem I'm having. 

Anyone able to lend a hand?

Cheers
Jeremy

---

### Post by Jammanuser on 2008-12-05
> **jubilantjeremy said:**
> 
I just did a chkdsk on the windows partition


Did u do a "chkdsk /r" or just a "chkdsk"??? ;) if you've only done the latter, than i suggest maybe trying "chkdsk /r" to see what u come up with then! 

Cheers! :)

-jammanuser

:D

---

### Post by jubilantjeremy on 2008-12-09
> **Jammanuser said:**
> Did u do a "chkdsk /r" or just a "chkdsk"??? ;) if you've only done the latter, than i suggest maybe trying "chkdsk /r" to see what u come up with then! 

Cheers! :)

-jammanuser

:D

Thanks for your reply. 

The way I performed chkdsk in windows was to right-click the drive, enter the property > tools dialogue, then select 'Check Now'. I ticked both 'automatic fix' and 'attempt recovery of bad sectors' boxes. 

Windows told me it could not run the operation without rebooting, and so scheduled it for the next startup. I rebooted and it ran, but very quickly - taking less than 20 seconds and not really giving me a chance to notice what was going on. 

In any case, I get the feeling the problem does not lie within windows or its filesystem, but only the ubuntu disk. 

Someone suggested I run a live CD, mount the disk and then run fsck, or edit fstab to make it rw. Would that work? If so, I'd really appreciate someone **running me through how to mount it and perform the fsck in a live CD** :)

Cheers

Jeremy

---

### Post by Jammanuser on 2008-12-09
> **jubilantjeremy said:**
> Thanks for your reply. 

The way I performed chkdsk in windows was to right-click the drive, enter the property > tools dialogue, then select 'Check Now'. I ticked both 'automatic fix' and 'attempt recovery of bad sectors' boxes. 

Windows told me it could not run the operation without rebooting, and so scheduled it for the next startup. I rebooted and it ran, but very quickly - taking less than 20 seconds and not really giving me a chance to notice what was going on. 

In any case, I get the feeling the problem does not lie within windows or its filesystem, but only the ubuntu disk. 

[COLOR="Red"]Someone suggested I run a live CD, mount the disk and then run fsck, or edit fstab to make it rw. Would that work? If so, I'd really appreciate someone **running me through how to mount it and perform the fsck in a live CD**[/COLOR] :)

Cheers

Jeremy

Hello! :D that's something i can help u with, but only because i did it myself just recently...

Ok...so here's how to mount ur root.disk, and then run the fs check:

First, of course, boot with the LiveCD, and open up a terminal! Then run:

```
sudo mkdir /win
sudo mount /dev/[COLOR="Red"]sda3[/COLOR] /win

```

Note: the "sda3" should be replaced (if not correct!) with the appropriate partition that Windows is installed on, i.e. "sda1" of "sda2" instead of "sda3"! it was "sda3" in my case, and would probably be the same for u...but just bear that in mind in case it isn't! 

Next mount the root.disk (before u simply mounted the Windows partition itself...but now ur going to mount the ubuntu root.disk, so that u can perform a fsck on it!):

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Now, to run the fsck, use:

```
sudo fsck /win/ubuntu/disks/root.disk
```

Let me know if it works or not...

Cheers! :D

-jammanuser

---

### Post by Jammanuser on 2008-12-09
> **jubilantjeremy said:**
> Thanks for your reply. 

The way I performed chkdsk in windows was to right-click the drive, enter the property > tools dialogue, then select 'Check Now'. I ticked both 'automatic fix' and 'attempt recovery of bad sectors' boxes. 


ok...hmm...i've never run it that way before myself! i used the command prompt, and simply typed in "chkdsk /r"...so i'm not entirely sure which one it uses! u might want to try "chkdsk /r" in the command prompt...just in case it used the other one! it may find something then!

Cheers! ):P

-jammanuser

:D

---

