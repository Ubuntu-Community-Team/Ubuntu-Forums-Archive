---
title: "help mount USB harddrives in Ubuntu"
date: 2009-02-28
forum: General Help
---

### Post by grafxalien on 2009-02-28
Today was my first experience ever with linux, and well, ive been working on it for about 12 hrs now and I need help.  I am trying to mount 4 USB harddrives in ubuntu, then share them on my network.  I have found a couple different methods to mount drives and none seem to work correctly.  Here is what I am currently using:
in my fstab file i added:

/dev/sdb1 /home/travis/F ntfs users,defaults,unmask000 0 0
/dev/sdc1 /home/travis/G ntfs users,defaults,unmask000 0 0
/dev/sdd1 /home/travis/H ntfs users,defaults,unmask000 0 0
/dev/sde1 /home/travis/I ntfs users,defaults,unmask000 0 0

Well, when I reboot, the first two usually mount fine, but the other 2 do not.  If i go into a terminal, log into root and type mount -a, then all 4 drives mount correctly.  

Sharing has also seemed strange.  I edited the global section of the smb.conf file to have usershare owner only = false

Sometimes after I restart, that line just disappears and I can no longer set shares from my "travis" login, only from the root.

Finally, sometimes the shares I set just disappear after I restart.

Any help would be really appreciated..I dont have the time to waste another entire day trying to figure this out..

---

### Post by Xiong Chiamiov on 2009-02-28
Gnome has some magic GUI to share folders via Samba.

It's a much better idea to mount things under /media, rather than your home directory.  You should also use names that actually mean something, rather than the Windows-esque letters.

unmask should be umask.

Get the drive mounting fixed first, then deal with samba separately.

---

### Post by grafxalien on 2009-02-28
the drive letters are fine with me because I have the actual drives label that on the casing.

I made the changes you suggest, still only the first 2 drive mount automatically.  If I switch to root user, then the other 2 load.  Then if I switch back to travis user, all 4 are there.  Any idea what is going on?

---

### Post by grafxalien on 2009-02-28
I get this error on the 2 harddrive that dont mount:
Unable to mount.
Unpriviledged user cannot mount NTFS block devices using the external FUSE library.  Either mount the volume as root, or rebuild NTFS-3g with integrated FUSE support and make it setuid root.

All 4 of my harddrives are the same..doesnt make sense to me why 2 of the drives get this error and 2 load fine.  Any ideas how to fix?

---

