---
title: "9p (Plan 9) shares using libvirt - random garbage returned"
date: 2012-06-04
forum: Desktop Environments
---

### Post by leo_m on 2012-06-04
I have a host folder containing photos shared across to my guest vm configured using libvirt (virt-manager).

I mount this in the guest with file-type 9p.  The share mounts okay and some of the photos get rendered okay, but randomly, it returns garbage (strange characters on screen) instead of photos.  The same folder, the same guest works okay when access is via VirtualBox shared folder system.

But I cannot use the virtualbox fs type (-t vboxsf) in the mount command successfully when I run the guest using libvirt, hence I have to use fs type 9p then.

Is there a workaround?  Has anyone else experienced such a thing?  What is the most efficient and error-free way (in the context above) to share files between hosts and guests using libvirt then?  Please do not talk about samba, I do not want that. 

I have tried sshfs in the past, but sshfs does not do a good job of updating the mounted directories/files when these get changed on the host.

Any expert opinions regarding filesharing between host/guest?

---

