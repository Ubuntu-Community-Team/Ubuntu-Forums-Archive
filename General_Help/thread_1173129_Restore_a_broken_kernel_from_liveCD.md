---
title: "Restore a broken kernel from liveCD?"
date: 2009-05-29
forum: General Help
---

### Post by pYrO1v1aniac on 2009-05-29
Hey guys. I've been googling this and I have yet to find a solution.

I installed ubuntu on a macbook pro 4,1 2 days ago on a brand new harddrive. All was well, everything's set up to my liking and then this morning I boot up and after the grub load, I get 

[0.000000] ACPI DMI BIOS YEAR=0, assuming ACPI-Capable machine
[0.262008] ACPI ABORTED because bad GZIP magic numbers
[2.162354] i8042.c: No controller found
[2.424342] Kernel panic - Not syncing: VFS unable to mount root fs on unknown= Block (0,0)

Is there any way I could repair this from the liveCD? If not, how would I backup settings and such before attempting a reinstall?

---

### Post by drs305 on 2009-05-29
I posted this after a search. Now I see the error messages are not exactly the same. Shot in the dark: From a LiveCD terminal, try updating your initramfs file. It's worked for others with the some of the same error messages. No guarantees but it won't hurt anything. This must be done from a working kernel or rescue cd such as [systemrescuecd]("http://www.sysresccd.org/Main_Page").
```
sudo update-initramfs -k all -c -v
```

---

### Post by pYrO1v1aniac on 2009-05-29
ubuntu@ubuntu:~$ sudo update-initramfs -k all -c -v
update-initramfs is disabled since running on read-only media

No luck. Any other suggestions?

---

### Post by drs305 on 2009-05-29
Sorry, it has to be run from a rescuecd such as [systemrescuecd]("http://www.sysresccd.org/Main_Page") or another kernel, not from the LiveCD. First post corrected.

**ADDED**: From a rescuecd you don't use the "sudo" preface.

---

### Post by pYrO1v1aniac on 2009-05-29
Okay, can you recommend me a good one?

[edit] sorry, re-read. Trying systemrescuecd now.

---

### Post by pYrO1v1aniac on 2009-05-29
Nope doesnt work. It asks to correct sudo to _sudo, and then complains 

_arguments:comparguments:303: can only be called from completion function

sudo itself is not found

update-initramfs is not found.

What now?

---

