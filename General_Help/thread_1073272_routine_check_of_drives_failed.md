---
title: "routine check of drives failed"
date: 2009-02-18
forum: General Help
---

### Post by jan23778 on 2009-02-18
Hi everyone,

I am fairly new with Ubuntu and something has happened that I have no idea how to correct. I seem to have shut down the system incorrectly and now on start up it checked all the drives. It has come back with a fail:

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4
checking drive /dev/sda1: 92% (stage 4/5, 761/3680)

*an automatic file system check (fsck) of the root filesystem failed.
a manual fsck must be perforned, then the system restarted.
the fsck should be performed in maintanance mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintanace shell will now be started.
After performing system maintanance, press control-d to terminate the maintanance shell and restart the system.
bash: no job control in this shell
root@jan-desktop:~#

Pleae someone help I just do not know what to do next and I am panicking that I would have to contact an engineer as I have no idea what to do next.

Any advice will be really appreciated.

Thanks

---

### Post by Herman on 2009-02-18
:D Hello jan23778,
You should boot up your Ubuntu Live CD and open Gnome Partition Editor.
It's in 'System'-->'Administration'-->'Partition Editor'.
Right-click on your Ubuntu partition and click 'Check'. 
Then click 'Apply', and a confirmation window will appear.
Click the 'Apply' button in the confirmation Window and wait while the file system check is working.
After it has finished, you should be able to boot Ubuntu and it should be all fixed. 

Regards, Herman :D

---

