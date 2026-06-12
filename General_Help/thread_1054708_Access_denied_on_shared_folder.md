---
title: "Access denied on shared folder"
date: 2009-01-30
forum: General Help
---

### Post by tullmejs on 2009-01-30
I have made a directory (chmoded 777), on a usb-drive, that I mount. It is shared. Read only-box is unchecked. 

At the computer with the drive as well as at vnc-viewer and WinSCP on remote Windows machine I can read and write to the directory.

Alas in Windows, accessing the folder, I can read it, but not write to it.

What's up with that?

---

### Post by halovivek on 2009-01-30
You have check with the windows permission in the server side. Right click on the folder - sharing and check for the permission of the users in advance tab.

---

### Post by kmac on 2009-01-30
Samba, I'm assuming?

Check your Samba config...

---

### Post by tullmejs on 2009-01-30
> **halovivek said:**
> You have check with the windows permission in the server side. Right click on the folder - sharing and check for the permission of the users in advance tab.

I don't have sharing on right click menu! (xubuntu)

> **kmac said:**
> Samba, I'm assuming?

Check your Samba config...

I don't know where to begin. I did find the entry for my directory in smb.conf, it reads:

[mydir]
path = /media/main/mydir
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by tullmejs on 2009-01-30
My bad! I made the mother folder 777, and that one *is* indeed writeable.

Subfolders are not. Somehow I supposed they automatically would be. 

Resolved.

:oops:

---

