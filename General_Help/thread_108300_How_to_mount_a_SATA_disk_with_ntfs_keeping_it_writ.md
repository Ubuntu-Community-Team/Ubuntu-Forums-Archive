---
title: "How to mount a SATA disk with ntfs keeping it writable?"
date: 2005-12-25
forum: General Help
---

### Post by S1l0 on 2005-12-25
Hi everyone!
I were trying hard to leave windows & M$_threats and I think the time is now, because I found Ubuntu distro and ...just loved it!
I hope someone help me to take the first steps, so here is the first need   : )

**Could someone give me some help about mounting a SATA disk with ntfs keeping it writable?**:

It's just a partition with data that I wanna share in my home network with Samba.
I can mount it with read&execute permissions for root an any user, but can't write.

I copy pasted my fstab options, mount output and the ls -lha output:

	**fstab**
		/dev/sda2		/media/sda2	ntfs		ro,user,nls=utf8,noatime,umask=0000,fmask=0000,dmask=0000,uid=1000,gui=1000	0	0

	**mount output**
		/dev/	sda2		/media/sda2	type ntfs	(ro,noexec,nosuid,nodev,noatime,nls=utf8)

	**ls -lha output**
		dr-x------	1	root	root	4.0k	2005-12-18	20:09	.
		drwxr-xr-x	15	root	root	4.0k	2005-12-18	20:09	..
		dr-x------	1	root	root	28k	2005-12-18	20:09	software
		dr-x------	1	root	root	8.0k	2005-12-18	20:09	music
		...

I hope you can help me with this. Explain me everything.
Thanks for your time.
Best regards,

---

### Post by rachaef on 2005-12-25
You might want to take a look at Captive:
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

AFAIK that's the only way to have full read/write support for NTFS under linux, the kernel driver's support for writing is rather limited.

regards
rachaef

---

### Post by S1l0 on 2005-12-25
[QUOTE=rachaef]You might want to take a look at Captive:
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

AFAIK that's the only way to have full read/write support for NTFS under linux, the kernel driver's support for writing is rather limited.

regards
rachaef[/QUOTE]

thanks. I'll take a look. ; )

---

