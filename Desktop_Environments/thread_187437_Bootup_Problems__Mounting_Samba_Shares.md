---
title: "Bootup Problems / Mounting Samba Shares"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Doomhammer on 2006-06-03
So I had Kubuntu working fine, but here when I tried to boot up a while ago, when the splash screen got to "Starting hardware abstraction layer hald [ ok ]" it cut to the standard console instead of the splash screen (same messages were being displayed, however) and just sat there for around 10 minutes...

It popped up an error message, but KDM was started too quickly for me to read it, and apparently there's no log of the system boot (why not ?!), so I guess I'll never know what it said...

So then logging into KDE it hung for around 30 minutes at "Loading the desktop..."

My question is this: most of my files are stored on a samba share on my fileserver downstairs, so they are being mounted / accessed to both during boot (to mount them) and while KDE loads (to retrieve my wallpaper from them). The reason this is relevant is because after I booted up, typing "cd /mnt/ajrdata" (one of my samba shares) crashed Konsole, as did "ls /mnt/ajrdata" - I had to "umount -f /mnt/ajrdata; mount /mnt/ajrdata" before it would work again.

So is the reason all these problems occoured possibly because Ubuntu was unable to mount the network shares [correctly] ? If so, why would it fail, if I was able to just go do it manually after everything started up ? And why doesn't Ubuntu keep a log of system boot so I could figure out what error message I got (which would probably explain all of this) ?

---

### Post by jdavis on 2006-06-03
Same problem here:

[http://www.ubuntuforums.org/showthread.php?t=186127](http://www.ubuntuforums.org/showthread.php?t=186127)

---

### Post by Dagur on 2006-06-04
I have this problem too. The boot process halts for a long time when starting "hardware abstraction layer HALD". 

I've found out that if I comment out the samba bits in /etc/fstab the boot process works fine, then I have to uncomment and do "mount -a" to mount the samba shares (it works without a problem after that).

---

