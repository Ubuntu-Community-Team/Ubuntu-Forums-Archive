---
title: "strange non-root write access to SMB mount"
date: 2007-07-27
forum: Desktop Environments
---

### Post by cjlindem on 2007-07-27
Hi,
I mount a shared directory on my windows 2003 server from Ubuntu 7.04 using fstab.  I'm using the newer cifs method instead of smb.  Everything is fine, except that when I try and copy many files at once (a directory) onto the share, logged in with my user account, the files show up with a lock for their icon, and I generally get an access denied error message at some point during the copy process.  Some files do copy over, and doing one file at a time does not give any problems.  If I copy the same directory from nautilus as root, I do not get this issue.  The properties on the mount's folder show that both root and my user account have the same rights to the share.  I don't understand why it's getting confused when I copy many files at once and deciding arbitrarily that I don't have write access from my user id.

Any suggestions are appreciated, thanks.

---

