---
title: "NTFS problems..."
date: 2009-01-04
forum: General Help
---

### Post by Gizenshya on 2009-01-04
Windows sometimes blocks my wubi installation from booting (not related to my other thread).

After a while, I figured out that it was something that (to the best of my recollection) was called "$logfile" in the NTFS drive.  If the power goes out, or if windows otherwise is shut down "improperly," it refuses to let me boot into ubuntu, or even mount any volumes that were mounted under vista when the system shutdown UNTIL vista re-mounts, and the "properly" unmounts each one.  This is incredibly annoying to say the elast.

At present, I can get by it with the external/removable volumes by force-mounting (which is still a pain), but for the wubi installation, so far I've only been able to boot it after I reboot and shutdown my vista OS.

ok, enough with the background, here's the question haha

How do I keep ubuntu from checking the $logfile for an unclean shutdown/un-mount when booting or mounting an NTFS volume?  (OR, how do I enable force boot/mount every time?-- with no FSTAB editing, as the sda/sdb/etc. locations change a lot as I have many USB connections and drives, and use the drives of friends a lot).

---

