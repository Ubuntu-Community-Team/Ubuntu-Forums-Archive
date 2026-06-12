---
title: "Warning about mdadm on upgrade to Breezy"
date: 2005-10-17
forum: Desktop Environments
---

### Post by ioliver on 2005-10-17
On upgrading my 2TB server to Breezy, I got this warning -

---------------------------------
Subject: Debconf: Configuring mdadm -- Initialise the superblock if you reuse hard disks

WARNING! If you are using hard disks which have a md superblock from an
earlier installation in a different RAID array, you MUST zero the
superblock before activating the autostart feature.

For doing this, do not start the RAID devices automatically and zero the
superblock (mdadm --zero-superblock /dev/xxx). You can then further use
'dpkg-reconfigure mdadm' to activate the autostart feature.
---------------------------------

I currently have a raid array that isn't connected. Will this autostart OK when I reconnect it when using Breezy? Is this warning just to do with bringing disks from totally different array onto a machine with the new mdadm and then doing an autostart?

BTW, the *must* sounds like something bad happens if we don't do this.  Anyone know any details?

Regards

Ian

---

