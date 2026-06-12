---
title: "how to downgrade rsync to 2.6.9?"
date: 2009-03-26
forum: General Help
---

### Post by Alex Yeh on 2009-03-26
Hi, folks. I need to downgrade rsync, so that it works properly. I am trying to back up a large-ish (only a little over 140 gigabytes) set of data from a drive on my laptop to a remote computer. Back when I was using OpenBSD, I routinely backed up large datasets with rsync with no problem whatsoever. However, apparently the version of rsync included with Ubuntu, and also, the most recent version of rsync (compiled "by hand") grind to a halt with an error when I try to sync a local and remote directory. rsync 2.6.9 (apparently) does not suffer from this particular problem. I am using Intrepid Ibex.

---

### Post by dcstar on 2009-03-26
> **Alex Yeh said:**
> Hi, folks. I need to downgrade rsync, so that it works properly. I am trying to back up a large-ish (only a little over 140 gigabytes) set of data from a drive on my laptop to a remote computer. Back when I was using OpenBSD, I routinely backed up large datasets with rsync with no problem whatsoever. However, apparently the version of rsync included with Ubuntu, and also, the most recent version of rsync (compiled "by hand") grind to a halt with an error when I try to sync a local and remote directory. rsync 2.6.9 (apparently) does not suffer from this particular problem. I am using Intrepid Ibex.

Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and see if that version exists, uninstall the original and install the old one.

---

### Post by Alex Yeh on 2009-03-26
yup - figured that out independently. Much thanks!

it didn't help much, I'm just getting a new error now. I guess I'll reinstall the new version now. hehe...

---

### Post by Alex Yeh on 2009-03-26
I found a workaround - I mounted the remote folder using sshfs, and rsynced the two "local" directories. Worked like a charm.

---

