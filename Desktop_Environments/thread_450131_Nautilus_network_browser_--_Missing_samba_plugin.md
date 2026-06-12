---
title: "Nautilus network browser -- Missing samba plugin?"
date: 2007-05-21
forum: Desktop Environments
---

### Post by benanzo on 2007-05-21
I recently installed the feisty-server on my machine and then compiled my own kernel and installed the xserver and gnome-core, gdm, and some fonts.  I've found this is  great way to really slim down what gets installed in Ubuntu.  I have since gone through and added the exact apps that I want.

A couple problems that I have come across though is that I seem to be missing support for network browsing in nautilus and the only options that appear in the "Connect to Server..." menu is SSH and Custom.  I want to have the usual options for WebDAV and FTP etc but can't seem to find the right packages/plugins to get that functionality back.  Also, when I try to browse the network in nautilus it doesn't actually search anything.  I have smbclient installed but something tells me that isn't exactly what is required.

Any help would be great!

Ben

---

### Post by benanzo on 2007-05-21
I found it.

```
sudo apt-get install libgnomevfs2-extra
```
This solves both the network browsing problem and adds the correct options to the Connect to Server... menu

---

