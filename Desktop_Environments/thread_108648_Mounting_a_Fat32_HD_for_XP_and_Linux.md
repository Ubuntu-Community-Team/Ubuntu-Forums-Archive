---
title: "Mounting a Fat32 HD for XP and Linux"
date: 2005-12-26
forum: Desktop Environments
---

### Post by icarius on 2005-12-26
I have recently been converted to Linux by a good friend of mine that pittied my Windows infested computer. However, I am currently trying to figure out how to get Ubuntu to see a Fat 32 partition that I have set up to be shared by both XP and Ubuntu, any help?????????:confused: :confused:

---

### Post by pharcyde on 2005-12-26
mount -t vfat /dev/hdXX /localdir

Where hdxx is the partion and drive of the partion (i.e. hda2 for second partion on first drive on primary ide)

where localdir is the folder on the local file system you want to mount the drive.

---

### Post by icarius on 2005-12-26
Is localdir the place where the mount is made to or do I need to put in the place where I need to mount it, and also I want to create a shortcut on my desktop, do I just create a link to the mount? THX

---

