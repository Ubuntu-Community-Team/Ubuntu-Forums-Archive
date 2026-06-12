---
title: "Boot process stops..."
date: 2005-11-26
forum: Desktop Environments
---

### Post by alhi on 2005-11-26
...with the following msg:

* checking all file systems [ok]
* mounting local filesystems... [ok]
find: ./orbit-tarou/linc-466e-0-1b6dbb955fb25: Permission denied
rm: cannot remove `./orbit-tarou/linc-221d-030d1579956e96&#180;: Input/output error
* starting hotplug subsystem... t empty0d157994ffa7: Input/output [ok] 

My Ubuntu is version 5.10 with the ReiserFS filesystem.

Before this error came up, I had a current fluctuation.
What do I have to do to revive my Ubuntu?

Thx in advance.

---

### Post by alhi on 2005-11-26
My problem has changed slightly. I found out, that the files in /tmp/orbit-tarou/ caused the problem. So, I moved them to my home dir. The good news is, the boot process works again. But now, X server reports a problem:

(gnome-session:8553): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/tarou:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/tarou:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/tarou:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/tarou:/tmp/.ICE-unix/8553 

Anyone have a clue about this?

Thanks.

---

### Post by taurus on 2005-11-27
Change the permission to that file, ~/.ICEauthority, or remove it and all will be good again...

---

### Post by alhi on 2005-11-27
Thanks for your reply, but unfortunately it doesn't work. Same error.

---

### Post by taurus on 2005-11-27
Okay, remove both /tmp/orbit-tarou/ & /tmp/.ICE-unix/

sudo rm -rf /tmp/orbit-tarou /tmp/.ICE-unix

---

### Post by alhi on 2005-11-27
[QUOTE=taurus]Okay, remove both /tmp/orbit-tarou/ & /tmp/.ICE-unix/

sudo rm -rf /tmp/orbit-tarou /tmp/.ICE-unix[/QUOTE]

When I try

sudo rm -rf /tmp/.ICE-unix

it simply gives me a "Permission denied", but when I start Ubuntu in "recovery mode" it says:

[4295881.205000] ReiserFS: warning: is_leaf: free space seems wrong: Level=1, nr_items=56, free_space=65488 rdkey
[4295881.205000] ReiserFS: hdc1: warning: vs-5150: search_by_key: invalid format found in block 262181. Fsck?
[4295881.205000] ReiserFS: hdc1: warning: vs-13070: reiserfs_read_lock_inode: i/o failure occured trying to find stat data of [29150337 0 x 0 SD]
rm: cannot remove '/tmp/ICE-unix//8553`: Permission denied

I tried to delete other stuff in /tmp like .X0-lock, but I can't remove it either.
I can't remove anything at all in /tmp.

---

