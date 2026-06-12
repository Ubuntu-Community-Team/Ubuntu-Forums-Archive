---
title: "Skunked permissions on my NAS"
date: 2007-12-03
forum: Desktop Environments
---

### Post by walexand on 2007-12-03
I've got a WD MyBook World, which is packed with about 1TB of good stuff.  This NAS device runs some kind of Linux variant with CIFS support. 

Somehow Ubuntu set the permissions on the entire device to a weird state.

Even though the permissions state that I am the owner, and have full access: 

Access: (0700/drwx------)  Uid: ( 1000/    bill)   Gid: ( 1000/    bill)

I cannot write to this device.  I spent about a week trying to figure it out before I tried to access it from Windows, only to discover the same problem from Windows.  According to Windows, root is the owner.

I've tried every mount option I could find, chown, chmod, chawcomeonnowpleasework with no results.

If I don't mount with my UID, it mounts owned by root and cannot be accessed at all.  If I set my UID, I can read but not write.  Any attempt to change the permissions or ownership results in access denied.

I even set the root password and tried from su and even that wouldn't let me change it.

I've also tried overriding the permissions from the NAS device itself.  The NAS believes that permissions are wide open.

So basically now I have a 1TB read-only device.

Any hints would be hugely appreciated.  Even a hypothesis as to how I brought this about since I certainly don't ever want to repeat it.

Thanks,

Bill

---

### Post by Linicks on 2007-12-05
Normally these devices require a top level share on /

Check that the share is open to EVERYONE or the like - it could be that.

Nick

---

