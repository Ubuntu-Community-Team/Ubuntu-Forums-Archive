---
title: "latest NXclient and Ubuntu NXserver not"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Nick Payne on 2006-06-26
The latest v2.0 NX client for Windows doesn't work with the 0.4.4 nxserver that I have running on Dapper. All the session connection and setup messages seem fine, but the desktop never appears, and the errors file contains a warning message about cookie mismatch. I uninstalled the 2.0 nxclient and installed the v1.5 for which I still had the setup file, and everything works fine. Does anyone know if there is a setting in node.conf that will enable the 2.0 client to work with the older server?

---

### Post by mannheim on 2006-06-26
[QUOTE=Nick Payne]The latest v2.0 NX client for Windows doesn't work with the 0.4.4 nxserver that I have running on Dapper. All the session connection and setup messages seem fine, but the desktop never appears, and the errors file contains a warning message about cookie mismatch. I uninstalled the 2.0 nxclient and installed the v1.5 for which I still had the setup file, and everything works fine. Does anyone know if there is a setting in node.conf that will enable the 2.0 client to work with the older server?[/QUOTE]

There are a couple of other threads about this -- I had the same "cookie mismatch." 

But nomachine has now made their nxserver a free download, so you can get hold of the latest matching version 2.0.0 (as long as you don't mind a version which limited two simultaneous sessions). I uninstalled the old version of nxserver (with apt-get remove **--purge**), then I did a "sudo rm -r /usr/NX/" to wipe out everything left there. Finally I installed the new nxserver, "Desktop version" 2.0.0 from nomachine's web site. You need to install the "client" and "node" debs too, because the "server" deb depends on those. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=202394"), Fiyawerx's post lists the debs you need.

I am writing this on a Windows PC, connected via nx to my ubuntu/dapper machine in my office, and I'm very happy.

---

