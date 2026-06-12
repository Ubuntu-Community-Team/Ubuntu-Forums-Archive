---
title: "File copy hangs"
date: 2023-10-24
forum: Desktop Environments
---

### Post by msknight on 2023-10-24
Ubuntu Cinnamon 22.04 Cinnamon 5.2.7 Kernel 6.2.0.34 generic - I've seen other people reporting the problem, but no replies to their threads

Problem - when copying files DOWN from a network CIFS share to either a local SSD or a USB drive, the copy process hangs via GUI. (Nemo, Caja and Thunar tried, all hang up and have to be pkilled.) Mount point is /mnt/jaguar ... so it's in the /mnt directory and not my home directory.

Files copied are not large, totalling 115kB.

What works - Copying from USB or SSD back up to the CIFS share works. Copying between USB and local SSD also works. Command line commands also work with no issue. CP, RCOPY, etc.

On the USB copy, the activity light is observed to stop, so I've concluded not a buffer issue.

Have previously had no swap, so enabled swap and tested... still hung up.

Have tried editing /etc/sysctl.conf and adding lines for vm-dirty_background and vm.dirty_ratio... still hung up. (I'm probably going to remove these lines as they're system wide, I believe.)

This was bugging me on Mint and has transferred to Ubuntu Cinnamon. The server was previously OpenIndiana and I've changed that to Debian... I've still got the hang up when copying from Cifs share.

Nothing in the syslog, either for process failures or apparmor complaints.

I'm starting to conclude a kernel issue, and I've got a feeling I've been here before, but don't want to start changing to other kernels without seeking advice on this first.

---

### Post by ActionParsnip on 2023-10-24
I'd check the file systems on the file server side to make sure the file systems are complete and consistent

---

### Post by msknight on 2023-10-24
Server side are checked and fine. Copy via CLI works no problem.

---

### Post by msknight on 2023-10-24
As an additional, translating the shares to NFS sees all file transfers work. However, I believe CIFS has greater security (ie. it won't allow writing if you just change the UID of the attached user) so I don't really want to rely on NFS if I can help it.

So I need to bottom this CIFS thing out.

---

### Post by TheFu on 2023-10-24
NFS with Kerberos is highly secure. More so than CIFS.  Also, if any system on the LAN isn't secured, all file sharing is suspect.  Expecting end-users to have good passwords is foolish.  Basically, anything secured through a password is asking to be hacked.  Always use certs or PKI-keys and avoid passwords alone for any system security.

Any chance the GUI program being used to copy is a snap package?  Snaps have different default security settings and don't usually allow access outside the user's /home/{username} directory.

---

### Post by msknight on 2023-10-24
None of them are snaps.

---

### Post by TheFu on 2023-10-24
> **msknight said:**
> None of them are snaps.

Next I'd ask which file systems are involved. source and target.  I don't have any clue, just looking for issues.  I haven't used CIFS in a few years now.  When you use smbclient, is everything fine?

---

### Post by msknight on 2023-10-25
Everything on the command line is fine.

---

### Post by msknight on 2023-10-25
Upgraded to 23.04 and 6.2.0.35 generic - still happens.

---

### Post by msknight on 2023-10-26
cache=loose in the mount options might be helping. 

So far, tests appear to be promising. Only time will tell now.

---

### Post by msknight on 2023-10-26
Looks like I'm settling on cache=strict,actimeo=60 for the moment and I'll see how it runs with this. Small file tests have worked so far.

---

