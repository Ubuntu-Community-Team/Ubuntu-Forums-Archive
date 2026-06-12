---
title: "mount nfs at bootup"
date: 2006-09-23
forum: Desktop Environments
---

### Post by myname on 2006-09-23
I am having a problem with my mounted network share (on my client) not showing up at bootup time.

I have the server set up, and if I perform the following from a terminal it works:

sudo mount 192.168.0.55:/data /mnt/parolee nfs rsize=8192,wsize=8192,timeo=14,intr

however, when I put the following in the fstab file, it does not remount at bootup:

192.168.0.55:/data /mnt/parolee nfs rsize=8192,wsize=8192,timeo=14,intr

however, if I open a terminal and enter in:

sudo mount /mnt/parolee

everything works, just not a bootup.  How can I get this to be recognized at bootup?

--kevin

---

