---
title: "Boot Freezes and mounts / as readoly---help"
date: 2009-05-27
forum: General Help
---

### Post by ddoherty03 on 2009-05-27
All,
 
I just installed Jaunty, it booted fine.
I installed a couple of extra packages to get a non-root raid array up.
Now when I boot, it freezes about 1/5 of the way across the progress bar then stops. When it flips back to the console, I can get it going again with Alt-Ctl-Del, but most of the startup faile because the / file system (ext3) is mounted read-only. I am not mounting the RAID array on boot up, so I don't thing that is the issue. I can mount the / read-write manually with
 
mount -o remount,rw /
 
but the system comes up broken. The dmesg shows the message 
 
EXT3-fs: mounted file system with ordered data mode.
 
which looks like it mounted OK, but not so.
 
Anyone have any ideas of what might be happening or what I should look at to figure out what's going on?
 
Any help greatly appreciated.
 
Regards,

---

