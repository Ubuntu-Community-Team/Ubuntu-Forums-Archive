---
title: "ntfs driver now has write support?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by saads on 2006-02-23
I found this on the [Linux NTFS]("http://www.linux-ntfs.org/") project page:

Write support: Last, but not least, the kernel driver now does all sorts of mambo jumbo when mounting a volume R/W. Features come slower than ntfsmount (fuse) but much more stable.

So does that mean we can now mount NTFS drives as rw instead of ro?

---

### Post by pestilence4hr on 2006-02-23
I am not sure, but on the [status]("http://www.linux-ntfs.org/content/view/15/29/") page it says

> Still read-only, but with safe file overwrite support on all Windows versions without changes to the file size (uncompressed, unencrypted, nonsparse files only).

I think it has very limited R/W support.

---

### Post by MighMoS on 2006-02-24
Well, in Ubuntu breezy, we'll have just ro support unless you compile your own kernel.  In Dapper, which uses the 2.6.15 kernel (if I remember correctly), NTFS write support is present for *most* situations, the exceptions I can remember off the top of my head being that heavily fragmented file systems don't always work well.

---

### Post by NiceGuy on 2006-02-25
Hey all,

I'm running a dual boot system with windows XP and dapper. What options would you guys recommend I put in my fstab so I had read/write for my XP partition? Would putting 'defaults' work? Should I include something like "errors=remount-ro".

Like this:

```

# <file system> <mount point>   <type>  	<options>      	<dump>  <pass>

/dev/hda1	/mnt/windows	ntfs		defaults,errors=remount-ro 	0	0

```

ps. should dump and pass both be 0?

---

### Post by MighMoS on 2006-02-26
something like:
```
/dev/hda1 /mnt/windows ntfs rw,[uid=XXXX] 0 0
```
What's in brackets is optional , and XXXX is your numberic user ID.  This will make that user "own" the new mount.  If you don't know your userID, just use the first number in ```
grep `whoami` /etc/passwd
```

---

### Post by Sutekh on 2006-02-26
[QUOTE=NiceGuy]

ps. should dump and pass both be 0?[/QUOTE]

I'll let you decide

[Tuxfiles - How to edit and understand the fstab - dump and fsck options]("http://www.tuxfiles.org/linuxhelp/fstab.html#five-six")

---

### Post by Sutekh on 2006-02-26
[QUOTE=MighMoS]something like:
```
/dev/hda1 /mnt/windows ntfs rw,[uid=XXXX] 0 0
```
What's in brackets is optional , and XXXX is your numberic user ID.  This will make that user "own" the new mount.  If you don't know your userID, just use the first number in ```
grep `whoami` /etc/passwd
```[/QUOTE]
You can also use the command **id** to get a user's uid```
id <username>
```  The -g option can be added to get group id info too.

---

