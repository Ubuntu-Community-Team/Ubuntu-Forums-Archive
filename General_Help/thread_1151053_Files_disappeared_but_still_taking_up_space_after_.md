---
title: "Files disappeared but still taking up space after mount"
date: 2009-05-06
forum: General Help
---

### Post by kaprikawn on 2009-05-06
Hi,

I've just installed a new hard drive and I created a mount point for it and configured the fstab file for it.

But then I did something stupid.

I started copying files onto my mount point before I actually mounted the hard drive.  So my OS partition got filled up with all these files instead of onto my new hard drive as I intended.  Then I restarted my computer and the hard drive mounted as it should.  And the files that I copied onto my OS partition by mistake aren't where I copied them anymore but my OS partition is still full.

Can anyone tell me where these files are or give me a way of otherwise finding them so I can delete them?

Thanks in advance.

---

### Post by CatKiller on 2009-05-06
Unmount the new hard drive (sudo umount /dev/whatever) and mount it somewhere else. The files you copied will be in a directory at the old mount point. Move them from the old mount point to the new mount point. Then unmount the new drive again and mount it back to where you wanted it.

---

