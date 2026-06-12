---
title: "ntfs-3g files written by linux appear as shared in vista"
date: 2009-03-13
forum: General Help
---

### Post by entropy1 on 2009-03-13
I am a newbie with a dual boot system with ubuntu 8.10 and windows vista home premium.

In fstab I mount the windows partition with

/dev/sda3  /media/C  ntfs-3g  quiet,defaults,rw,uid=<myuid>,gid=<mygid>,fmask=177,dmask=077  0 0

When I create a new file under linux and then reboot in vista to see the file, the file always shows up as shared with all users.  What can I do so that vista does not automatically share new files created by linux?

---

