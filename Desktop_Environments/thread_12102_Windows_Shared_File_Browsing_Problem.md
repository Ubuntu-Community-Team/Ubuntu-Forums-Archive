---
title: "Windows Shared File Browsing Problem"
date: 2005-01-21
forum: Desktop Environments
---

### Post by SpaulS on 2005-01-21
This seems so simple, but I cannot find a complete answer on any of the forums. I have:
Ubuntu Linux with Samba client support
Windows XP with shared folders

I can:
See the Windows server and the shared folders
Browse the all the Windows shared folders
Drag file from the Windows shared folder and copy it into the Ubuntu machine
Drag file from the Ubuntu machine and copy it into the Windows shared folder
Print to the Windows shared printer from Ubuntu

I cannot:
Double click and open files directly from the shared Windows folder. This is using Nautilus.

I recall that there may be a Gnome bug associated with this, but I can no longer find it, but it may be something else as well.

Thank you for you help!

---

### Post by wk1989 on 2005-01-28
[QUOTE=SpaulS]This seems so simple, but I cannot find a complete answer on any of the forums. I have:
Ubuntu Linux with Samba client support
Windows XP with shared folders

I can:
See the Windows server and the shared folders
Browse the all the Windows shared folders
Drag file from the Windows shared folder and copy it into the Ubuntu machine
Drag file from the Ubuntu machine and copy it into the Windows shared folder
Print to the Windows shared printer from Ubuntu

I cannot:
Double click and open files directly from the shared Windows folder. This is using Nautilus.

I recall that there may be a Gnome bug associated with this, but I can no longer find it, but it may be something else as well.

Thank you for you help![/QUOTE]
 Hi, I experienced the exact same  problem as you, I just installed Ubuntu a few hours ago. 
I can browse the folders through terminal, but can't seem open them in Nautilus.

---

### Post by wk1989 on 2005-01-28
Okay, my problem is solved, this is what I did, hope this helps. :D 
"sudo mount /dev/hda7 /mnt/win -t vfat -o umask=000"

---

