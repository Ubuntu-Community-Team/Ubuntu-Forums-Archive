---
title: "file system errors, unexpected inconsistency, fsck failed..."
date: 2006-02-12
forum: Desktop Environments
---

### Post by VCSkier on 2006-02-12
hello everyone.  i've been running ubuntu on my ibm thinkpad t41 for a couple weeks now, and i love it.  i've very new to it; this is my first time ever using linux, and when i decided to try it, i went all out.  i completely removed windows from my system, and and running a clean, full install of breezy.

i don't know what i did to cause this, but as of this morning, my boot process is being interrupted by what appears to be a major error... (i copied this by hand, and then typed it from my hand-written copy, so it may not be exact)

```
...
*Checking root file system...
/ contains a file system with errors, check forced.
/:
Inodes that were part of a corrupted orphan linked list found.

/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
                                                                                                                    [fail]
*fsck failed.  Please repair manually and reboot.  Please note
*that the root file system is currently mounted read-only.  To
*remount it read-write:

* # mount -n -o remount,rw /

*CONTROL -D will exit from this shell and REBOOT the system.

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~# _
```

obviously, the first thing i tried was typing "mount -n -o remount,rw /"  nothing happened...  i also tried playing around w/ the fsck command alittle, but i kept getting a warning message that my file system is currently mounted read-only, and that i could seriously damage my system if i ran fsck...

this happened once before, a week or so ago, soon after in first installed ubuntu.  at that point though, i had not done much configuration on it, so just did a clean, full reinstall of the os.  things worked fine then.  more recently, i've spent quite abit of time configuring things the way i wanted them and setting things up (i've also taken some rather important class notes), so i'd rather not reinstall and lose all of that at this point.

any directly or advice would be great.  let me know if you need me to provide any more details.  thanks.

---

### Post by tmahmood on 2006-02-12
first you better backup your importent data. 
May be bad sectors are developing in your drive. so you should check your drive. first unmount the partition then run fsck you should not run fsck on a mounted partition.

I recived this error when I tried to mount a physically damaged partition.

---

### Post by VCSkier on 2006-02-12
what would be the proper commands for doing this?  i'm very new at this.  thanks.

---

