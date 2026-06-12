---
title: "Can't Rename  Computer"
date: 2012-09-03
forum: Desktop Environments
---

### Post by HDTimeshifter on 2012-09-03
I moved my file server to a newer computer (a hard drive crashed and I took the opportunity to move the drives to a faster PC while replacing the bad drive).  I had named my server "Athlon", but since it is no longer running on an Athlon, want to name it something more appropriate and not hardware dependent like "Server".  The only place I could find to rename it is in Browse Network / Properties of the computer, however when I try to rename it complains "Operation not supported by backend."  I'm the administrator with full priviledges - how do I rename it?  The server is running 12.04 Desktop (I basically just use it to back up files from my main desktop PC and laptop).

---

### Post by elliotbeken on 2012-09-03
I think you need to change the name in the hostname file...

sudo nano /etc/hostname

or 

sudo gedit /etc/hostname

save and restart...

Hope this helps

---

### Post by Lars Noodén on 2012-09-03
In addition to /etc/hostname, you'll also want to update /etc/hosts
Unfortunately the reboot is probably unavoidable.

---

