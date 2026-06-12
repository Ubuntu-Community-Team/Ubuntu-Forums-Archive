---
title: "trash not working in thunar when user files spread across 2 file systems"
date: 2013-08-03
forum: Desktop Environments
---

### Post by halfbeing on 2013-08-03
I have just installed UbuntuStudio (which uses XFCE) and I have chosen to encrypt my home folder (/home/robert). However some of my files I have chosen to store outside the encrypted file system (in /home/unencrypted) to maximise disk read/write performance. The problem is that the stuff stored outside the encrypted file system on the root file system cannot be sent to trash by Thunar. I am certain this will eventually result in me permanently deleting things by mistake. Is there any way I can get a working trash set up for files on the root (unencrypted) file system?

---

### Post by halfbeing on 2013-08-04
I have now come up with part of the solution in that I have successfully created a trash folder and files are being sent to it.

My uid and gid are both 1000 and both robert so I did:
> sudo mkdir -p /.Trash-1000/{files,info}
sudo chown -R robert:robert /.Trash-1000

The less serious problem I now have is that Thunar can't see those trashed files and so I have to navigate to them manually to delete them permanently. Is there a way to get Thunar to see those files as trash?

---

