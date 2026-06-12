---
title: "Samba not streaming videos"
date: 2009-05-24
forum: Desktop Environments
---

### Post by paopao on 2009-05-24
I'm using Kubuntu 9.04.

When I connect to my other computer running Windows XP using the Samba share, it wants to download the file to some temporary folder first and then play it.  When I connected Windows to Windows, it would stream the file and not completely download it.  Even when I was running Ubuntu 8.10 a few weeks ago, it would also stream the file.  I'm wondering if this has something to do with KDE or the newer version of Ubuntu.

Even though the network at my home is fairly fast, it would be nice to have the videos stream like they did before.

Thank you!

---

### Post by dargaud on 2009-06-04
This behavior may depend on the app you use to play the file, and also sometimes to the codec used. Have you tried different players ?

---

### Post by krazyd on 2009-06-04
As dargaud suggested, this is dependent on what app you use to play the file - whether it can understand ioslaves. I'm pretty sure smplayer can do what you want: go to Open>URL... and enter smb://computername/folder/file.avi

Another alternative to this is to mount the samba share within the local filesystem. smb4k is an advanced smb browser app for kde which can do this for you from a great GUI. it's in the repos.

---

