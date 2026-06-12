---
title: "How to do /usr/bin/smem &gt; /dev/null at shutdown?"
date: 2009-02-24
forum: Desktop Environments
---

### Post by lotuseclat79 on 2009-02-24
The title command, smem, can clear RAM at shutdown before powering off, and I am looking at the /etc/init.d/halt script to do it, however, since I am running in a Live CD environment, I do not see a way to do it.

If I issue the smem command before the halt command in the do_stop routine, then all of memory which contains the tmpfs is wiped and the halt command could not execute to poweroff.  Possibly, the halt command could be executed from the LiveCD, but then again, the mount point, etc. would already be lost.

If I issue the smem command after the halt, it likely will not execute, as the system would likely poweroff before it could execute, however, there is a setting for HALT to be either power off or halt which is set to power off by default.  If it were set to halt instead of poweroff, would that work?

The halt command symbolically points to the reboot command - it looks like.

The system I saw this approach work was a KDE oriented system, and it was done in a halt.sh script at shutdown.  Perhaps it might be a bit easier to do in a KDE environment if the shutdown sequence there is similar, but I'm sure it must be possible somehow in a Gnome environment for Ubuntu 8.10, eh?

-- Tom

---

