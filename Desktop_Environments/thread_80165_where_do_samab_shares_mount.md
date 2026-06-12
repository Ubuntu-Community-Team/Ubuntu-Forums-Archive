---
title: "where do samab shares mount/"
date: 2005-10-21
forum: Desktop Environments
---

### Post by bwainscott on 2005-10-21
when you access windows machines on your network modify files on the windows computer and then want to save it.  openOffice tries to save the file locally on my linux machine.  In the file tree, is there a place to access networked computers?

---

### Post by Joe_lurker on 2005-10-21
The share is not mounted.  I believe that Gnome uses samba tools to sync the file with the share.  When you open a file in Oo a temporary folder is created in the /tmp directory.  This is where you will find the file.  When you save the file the underlying system uploads the file to the share.  I don't know if the file is locked in any way.

Joe

---

