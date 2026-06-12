---
title: "Files Can't Read Phone"
date: 2022-05-19
forum: Desktop Environments
---

### Post by geeky-1 on 2022-05-19
Often when I try to open a File window or refresh the window for my phone, it gives me the error below:
> Unhandled error message: The name:1.210 was not provided by any .service files
I've found the solution is to open a terminal window and enter nautilus -q to close all my Files windows, but it is a hassle to reopen all my Files windows again. This bug seems to have been around for quite a while now and wonder why it hasn't been fixed.

---

### Post by Holger_Gehrke on 2022-05-19
It's not a bug just in the file-manager. Mounting of devices connecting though MTP is handled by the Gnome Virtual Filesystem (gvfs) which communicates with the file-manager through dbus. The 'name:1.210' is a 'unique dbus name' (as opposed to 'well-known dbus names' which are somewhat human-readable like for example 'org.gtk.vfsd.UDisks2VolumeMonitor'). Unique names are automatically assigned to connections and don't have .service files. I think the name became invalid - probably because the phone disconnected and reconnected and got a new name, invalidating the old one - and the file-manager kept using the old one. The phone shouldn't do this, but the file-manager should be listening for 'NameOwnerChanged' signals to catch this kind of misbehavior.

Holger

---

### Post by ActionParsnip on 2022-05-19
If the Ubuntu system has an SSH service running, you can connect using AndFTP (on the phone) over WIFI and manipulate files (push and pull)

---

