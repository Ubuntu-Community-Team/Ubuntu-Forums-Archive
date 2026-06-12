---
title: "List of kernel modules to load during the boot?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Janek on 2005-10-26
Hello.

This thread is my another approach to solve the problem described [earlier]("http://ubuntuforums.org/showthread.php?t=78392").

To sum up: for reasons unknown, my system at each boot performs search for module "ext2" which simply isn't part of the current 386 kernel.
It hangs for a moment and then displays line "FATAL: Module ext2 not found.". Next, after while, it boots properly and then works perfect - as usual.

Of course, it's not really a FATAL issue - everything in fact does work fine; the process of boot is just noticeably slower than it should be.

I suppose that somewhere in my filesystem must exist a little hidden file which holds a list of modules to load and which tells my system to search for "ext2" (which has never existed!).

I'd like to ask you if I am right and where this file could be.

Thanks a lot in advance for *any* help!

---

### Post by Xian on 2005-10-26
/etc/modules lists the local modules to be loaded during boot. However, since I've seen this message on a variety of Linux sytems I would tend to believe this is something that has been configured into the kernel. And since it causes no problems, I've never been tempted to spend the time rebuilding just for that slight delay while the message is flashed.

Google the exact warning message & see what you turn up.

---

### Post by Janek on 2005-10-26
Thanks for quick reply!

> **Xian]/etc/modules lists the local modules to be loaded during boot. [/QUOTE]
In this file there are some additional modules, but none of them is our "ext2".

[QUOTE=Xian]However, since I've seen this message on a variety of Linux sytems I would tend to believe this is something that has been configured into the kernel.[/QUOTE]
I've tried to reinstall the kernel, even to move to 686, completely remove 386 and install it one more time said:**
> And since it causes no problems, I've never been tempted to spend the time rebuilding just for that slight delay while the message is flashed.
I know it's not big deal, but it's really annoying for me; I've liked the normal, graphical process of booting and if I'm not getting it anymore, something is wrong.

[QUOTE=Xian]Google the exact warning message & see what you turn up.[/QUOTE]
I tried to do this long before posting this message.
Unfortunately, Google doesn't turn up anything interesting for me.

Thank you, however, one more time.

I'm still looking forward for any other suggestions.

---

### Post by Xian on 2005-10-26
[QUOTE=Janek]In this file there are some additional modules, but none of them is our "ext2".[/quote]
Like I said it's probably built into the kernel.

[QUOTE=Janek]I've tried to reinstall the kernel, even to move to 686, completely remove 386 and install it one more time; nothing has changed, however. [/quote]
You'd have to build a kernel yourself and configure it specifically for your system. Just using different versions of the same pre-built kernel would not give you different results.

---

