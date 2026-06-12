---
title: "Help! Gvfsd is consuming memory!"
date: 2009-05-14
forum: General Help
---

### Post by guywithcable on 2009-05-14
Gvfsd is consuming memory non stop. I've reinstalled it in Synaptic and rebooted several times and that didn't help. Dbus-daemon is using CPU too. All four of my CPU cores are varying between 14% and 60% consistently. Please help!

---

### Post by guywithcable on 2009-05-15
Well, it seems to have stopped after running fsck several times from a live CD. It said that one inode was using some extent label and extents weren't enabled. This makes sense cause I'm using ext3 not ext4, but I don't know why that inode had the extent label on it. It also fixed some sizes, multiply-claimed blocks, and orphan inodes. This was all in my /home partition. The root partition had no errors on it.

BTW, I'm using Jaunty.

---

