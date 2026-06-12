---
title: "Virtualbox issues"
date: 2008-12-08
forum: General Help
---

### Post by weweboom on 2008-12-08
I would like to transfer files from my hard drive (ubuntu) to my virtual hard drive (vista ultimate) how would i go about doing that

---

### Post by HotShotDJ on 2008-12-08
Create a VirtualBox shared folder. Its VERY easy. See: [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12)

---

### Post by phinullfermata on 2008-12-08
In virtualbox (before you start a vm), when you click on the VM you added, you see a bunch of headings under the details tab on the right.  One of these is "Hard Disks".  Click on that and it will give you a list of hard disk mounts you have enabled (which is probably blank).  Click on the "+" icon on the right hand side and select the folder you want to share.  That folder should then be included as a mounted drive in your VM.  I haven't done this in a while so the details may be fuzzy, you might want to look it up in the manual as well.

---

