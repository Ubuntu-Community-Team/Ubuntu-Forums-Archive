---
title: "Autofs mounts drive as ready only"
date: 2009-06-17
forum: General Help
---

### Post by eeijlar on 2009-06-17
Hi,

I am not using Ubuntu (Open Suse), but since Ubuntu is the only OS with any stuff on autofs... I thought this might be a good place to start.

I have auto-mounted a remote disk using autofs. It's a drive that can be accessed from Windows or Linux. The problem is that the drive mounts as read-only, even though I have read write access to it from Windows. I have a dual boot of XP and OpenSuse. I can write to the drive in Windows but not Linux. I can browse the drive, no problem but can't write to it :(

Any ideas?
/jlar

---

### Post by swerdna on 2009-06-17
> **eeijlar said:**
> Hi,

I am not using Ubuntu (Open Suse), but since Ubuntu is the only OS with any stuff on autofs... I thought this might be a good place to start.

I have auto-mounted a remote disk using autofs. It's a drive that can be accessed from Windows or Linux. The problem is that the drive mounts as read-only, even though I have read write access to it from Windows. I have a dual boot of XP and OpenSuse. I can write to the drive in Windows but not Linux. I can browse the drive, no problem but can't write to it :(

Any ideas?
/jlarHi jlar, three questions:
[LIST=1]
[*]Are you asking so you can learn how to mount it in openSUSE, or what -- I'm a bit confused.
[*]What's the filesystem, NTFS or FAT32?
[*]And what do the openSUSE ppl say about the permissions problem on the automounted drive?
[/LIST]

---

### Post by eeijlar on 2009-06-18
Hi swerdna,

Didn't realise you moonlighted over here too... (-:

I have a more detailed post on the OpenSuse forums:

[http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives.html](http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives.html)

I know I shouldn't be cross posting, but I have been trying to get this working for months, so any help I can get would be great.

/jlar

---

### Post by eeijlar on 2009-06-18
> Are you asking so you can learn how to mount it in openSUSE, or what -- I'm a bit confused.I am using OpenSuse at work and about half of us use Linux, the rest use XP. So, it's not an academic exercise... At the moment I am sending files via sftp from Linux to the remote disk, it's the only way I can write to it.

> What's the filesystem, NTFS or FAT32?It must be FAT32... don't know really. When I log into a Solaris box, my /home is on this disk, same for HP-UX. And, in Windows it can be mapped as a network drive... 

If I do

```
cat /proc/mounts
```It has this signature:

```
-hosts /net/mysterious/remote/disk autofs rw,fd=5,pgrp=4749,timeout=600,minproto=5,maxproto=5,offset 0 0
```> And what do the openSUSE ppl say about the permissions problem on the automounted drive?I have a reply now... so hopefully

---

### Post by swerdna on 2009-06-18
> **eeijlar said:**
> Hi swerdna,

Didn't realise you moonlighted over here too... (-:

I have a more detailed post on the OpenSuse forums:

[http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives.html](http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives.html)

I know I shouldn't be cross posting, but I have been trying to get this working for months, so any help I can get would be great.

/jlar
It's valid IMO to get the help wherever you can get it. You don't seem to be getting much on this form the folks over in opensuse forums so far. Now that I see the problem, I'm not au fait with that stuff, sorry. Good luck with the folks over here.

---

### Post by eeijlar on 2009-06-22
I got this working thanks to the folks over at OpenSuse.... see here for post:

[http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives-2.html#post2002691](http://forums.opensuse.org/network-internet/413401-permissions-autofs-mounted-drives-2.html#post2002691)

---

