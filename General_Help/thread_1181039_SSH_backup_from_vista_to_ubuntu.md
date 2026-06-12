---
title: "SSH backup from vista to ubuntu"
date: 2009-06-07
forum: General Help
---

### Post by OiPenguin on 2009-06-07
I need a regular backup solution for "the odd one out", a Vista machine in an Ubuntu environment. I've set up [sbackup]("http://sbackup.sourceforge.net/") from Ubuntu desktop to Ubuntu server over SSH, but need advice on an easy to set up solution which does scheduled (incremental) backups from Vista to Ubuntu. Anyone?

---

### Post by blueridgedog on 2009-06-07
Couldn't the Vista box do its own backups using the build in backup tool, saving the output to a drive mapped onto the Ubuntu box?  If you want to avoid the drive mapping, then run an ssh server on one of them and use sftp to upload the resulting files via either a scheduled job on the Vista side or a cron job on the ubuntu side.

---

