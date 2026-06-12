---
title: "Kernel panic after routine shutdown"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Rehevkor on 2005-06-09
Last night I shut my laptop down same as always, with no changes to configuration or software, and today it won't boot. Here's the message, which occurs immediately after "Starting Ubuntu..."

```

pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

```

I also tried booting into recovery mode, which gave me the same error. I have a fairly recent backup of the system, but I'd rather try to fix this manually before attempting a restore.

Any ideas?

---

### Post by Rehevkor on 2005-06-10
Actually, I was mistaken. This happened after I installed the latest kernel update from the ubuntu update manager. It seems to have killed my install.

How can I reverse that update?

---

### Post by skoal on 2005-06-10
[QUOTE=Rehevkor]Actually, I was mistaken. This happened after I installed the latest kernel update from the ubuntu update manager. It seems to have killed my install.

How can I reverse that update?[/QUOTE]

What kind of update was it? From a -386 to a -686 kernel update? or an update on the same kernel, like -386.1 to -386.2?  If it was the first way (from 386 to 686), you can reboot and select the "good" kernel from grub and then remove the other one.  If it was the latter case, you can fire up Synaptic, select the kernel package in question, go to "Package" menu and "force update" to the lower (known working) version.  I think that should succesfully downgrade your kernel without removing anything.

\\//_

---

### Post by braunsfeld on 2005-06-10
Maybe this->[https://bugzilla.ubuntu.com/show_bug.cgi?id=11135](https://bugzilla.ubuntu.com/show_bug.cgi?id=11135)

For me installing initrd-tools from breezy did the trick. I booted into the system with a "quick and dirty" copied kernel and modules from a linux live-cd (kanotix).

---

