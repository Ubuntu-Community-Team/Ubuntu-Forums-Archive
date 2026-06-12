---
title: "samba file sharing to windows"
date: 2006-05-01
forum: Desktop Environments
---

### Post by emm721 on 2006-05-01
i have a computer set up with ssh and samba installed. it has ubuntu breezy server installed. i want to be able to access files on it from windows computers through \\server. so far it works, but i cant write files to it. can anybody help with this?

---

### Post by DSn0wMan on 2006-05-01
Does your user have write priveledges to the directory you are wrighting to?

---

### Post by emm721 on 2006-05-01
im writing to the /home/user directory, but i did make it write/read for all.

---

### Post by DSn0wMan on 2006-05-01
I found this bit of info in the ubuntu wiki:

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

smb.conf

This describes your /home folder. Usually you want to share this folder in a home-environment, because these are the files you want to share. To do so, make the following changes: 


    ![homes]
       comment = Home Directories
       browseable = yes

    # By default, the home directories are exported read-only. Change next
    # parameter to 'yes' if you want to be able to write to them.
       writable = yes

    # File creation mask is set to 0700 for security reasons. If you want to
    # create files with group=rw permissions, set next parameter to 0775.
       create mask = 0775

    # Directory creation mask is set to 0700 for security reasons. If you want to
    # create dirs. with group=rw permissions, set next parameter to 0775.
       directory mask = 0775

---

### Post by emm721 on 2006-05-01
Unable to create new folder, "New Folder"

Access is denied.

and yes i did change the smb.conf to that.

---

