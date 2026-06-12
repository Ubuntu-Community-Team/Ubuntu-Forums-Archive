---
title: "Network Servers in treeview in Nautilus"
date: 2006-07-16
forum: Desktop Environments
---

### Post by efikkan on 2006-07-16
Hi

Can anyone tell me how to add the "Network Servers" to the treeview in Nautilus? I want to browse the local network (computers with Windows) like in Microsoft Windows Explorer. This feature is required for me and my family to convert from Windows to Linux.

Please help me.

Greetings,
efikkan.

---

### Post by doas777 on 2008-02-06
if you figure it out, please post your solution. I'm looking for the same fix.

---

### Post by tillkowski on 2008-02-06
> **efikkan said:**
> Hi

Can anyone tell me how to add the "Network Servers" to the treeview in Nautilus? I want to browse the local network (computers with Windows) like in Microsoft Windows Explorer. This feature is required for me and my family to convert from Windows to Linux.

Please help me.

Greetings,
efikkan.

Have you tried mounting them? From "Places", select "Connect to server...", as a service type select "Windows share", then enter "//computer-name" for server. Click "Connect" and the computer will be mounted to your system, Nautilus will show it in the tree view and possibly on the desktop.

For more on mounting and how to mount volumes automatically on startup, check out this handy guide: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If your network is migrating to Linux anyways, you should also look into NFS, I find it to work much nicer than Samba (Windows share).

---

### Post by fig_wright on 2008-03-22
It seems odd that the only way to get Samba shares into the tree view is to mount them! What is so different about the tree view that it cant see the things in "places" view?

---

