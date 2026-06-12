---
title: "fstab nfts owner"
date: 2010-11-15
forum: Desktop Environments
---

### Post by georgebrough on 2010-11-15
Hi,

I'm new ish to Ubuntu & linux and I've just moved my home folder on to an NTFS drive that is also accessed by windows.  I am now struggling to take ownership of the drive.  I've read that if I add uid=1000 to the options in /etc/fstab that should make me owner, but I've done this, and run sudo mount -a, and rebooted but root remains the owning user and group of everything on the partition.  I have checked that I am user 1000 (by running id).  

my latest set of options is

ntfs-3g    rw,user,auto,fmask=0177,dmask=0077,uid=1000

Can anyone help me please!?

George

---

### Post by sikander3786 on 2010-11-15
Hi.

You can never have your /home on an NTFS drive because NTFS doesn't support Linux permissions system.

You'll need an ext3 or ext4 for your home folder.

---

