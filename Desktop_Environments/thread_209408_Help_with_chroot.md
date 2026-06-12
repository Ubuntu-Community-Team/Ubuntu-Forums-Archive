---
title: "Help with chroot"
date: 2006-07-05
forum: Desktop Environments
---

### Post by go2dell on 2006-07-05
Before anybody suggests it, please note that this is not a 32bit vs. 64bit problem, unless some helpful person was able to sneak in and replace my processor with a shiny new AMD64. ;) 

In short, I had a strange crash earlier and it appears that at least some of the kernel modules were zapped.  In essence, the machine won't boot anymore on the installed Ubuntu, but I have been able to boot just fine from the Ubuntu install CD to check all my partitions.  All now appears to be fine with the partitions, but there was apparently a death in the module family.

The fix should be simple -- or so I thought -- just boot with the Install CD, chroot into my installed Ubuntu, reinstall the kernel and associated modules (just to be safe), exit and reboot into a working system.

The problem is that I can't chroot.  I get that blasted error:
```
chroot: cannot run command `/bin/bash': Exec format error

```

My next step, if this doesn't work, is to backup anything important onto my data drives and reinstall Ubuntu fresh.  I don't really want to do that because I'll have to set all my preferences again, and besides, my curiosity is piqued.

Since this isn't a 64bit issue, anybody have any other ideas?  What silly thing have I forgotten to do?

---

### Post by mlind on 2006-07-05
What about
```

sudo chroot */mnt/root* /bin/sh

```

---

### Post by go2dell on 2006-07-05
```
ubuntu@ubuntu:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2006-05-31 01:15 /bin/sh -> bash

```

therefore

```
chroot: cannot run command `/bin/sh': Exec format error

```

Same is true of "/bin/bash." ](*,) 

Good thought, though.  My thanks for the effort.

---

### Post by mlind on 2006-07-05
You are booting using the livecd ? And trying livecd's /bin/bash?
I dunno if it helps, but I've never had problems "alternate" install cd's chroot
when doing a system recovery.

For last resort, try that or download knoppix or similar.

---

### Post by go2dell on 2006-07-05
Just to see what happens, I also tried using Rescue Mode from the Alternative Install CD.  It can mount my root partition but it can't execute a shell in the target; it can only execute a shell in the CD environment.

I already tried Knoppix, with exactly the same result.  I'm going to try digging up one of my old Gentoo CDs to see if I can chroot off there.  After all those Gentoo installs, I would have thought it would be a piece of cake to do this on Ubuntu.

Is there a reliable way to redirect apt-get or dpkg operations to a different target?  That would allow me to drop in a fresh kernel image without needing to chroot, although it sort of gives me the willies.  It's beginning to seem as though it's my only hope.

This is getting ridiculous, but kinda fun.  \\:D/

---

### Post by mlind on 2006-07-05
[QUOTE=go2dell]Just to see what happens, I also tried using Rescue Mode from the Alternative Install CD.  It can mount my root partition but it can't execute a shell in the target; it can only execute a shell in the CD environment.

Is there a reliable way to redirect apt-get or dpkg operations to a different target?  That would allow me to drop in a fresh kernel image without needing to chroot, although it sort of gives me the willies.  It's beginning to seem as though it's my only hope.

This is getting ridiculous, but kinda fun.  \\:D/[/QUOTE]

If you're chrooted to your own root (/) and have networking capabilities, just by
running aptitude and apt-get should work like normal. Just mount your /boot if it's
a separate partition and *aptitude install linux-kernel-xxx*.

/edit 
misread your earlier post. I don't think that "dropping thing" is easy or even possible task.
Why cannot it execute shell in the target environment, do you get an error?

---

### Post by go2dell on 2006-07-05
I didn't write down the exact error message, but it's essentially that the Rescue Mode found a "/bin/sh -i" in the target environment but cannot execute it.  It doesn't really give any more reason than that.

---

### Post by go2dell on 2006-07-25
The problem was solved by reinstalling (and chroot works again), but if anybody else has the same problem, try using the chroot install mode of dpkg instead:

[http://www.us.debian.org/doc/manuals/reference/ch-package.en.html#s-un-bootable]("http://www.us.debian.org/doc/manuals/reference/ch-package.en.html#s-un-bootable").

---

