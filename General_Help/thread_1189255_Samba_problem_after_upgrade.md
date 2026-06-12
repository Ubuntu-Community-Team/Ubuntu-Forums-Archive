---
title: "Samba problem after upgrade"
date: 2009-06-16
forum: General Help
---

### Post by matt91 on 2009-06-16
Just upgraded my server today from 8.10 to 9.04. I kept my samba config from before where I could connect from windows without having to log in, now it prompts for username and password and none of the ones I use work. Here is my samba config file, I have omitted the other shares I have as they are virtually the same.

```
[global]
        workgroup = MSHOME
        server string = Samba Server
        security = SHARE
        guest account = matt
        log file = /var/log/samba/%m.log
        max log size = 50
        socket options = TCP_NODELAY
        printcap name = /etc/printcap
        dns proxy = No
        valid users = matt
        read only = No
        guest ok = Yes

[r]
        path = /data/storage
        force user = root
        create mask = 0777
        force create mode = 0777
        directory mask = 0777
        force directory mode = 0777
        hosts allow = ALL
        delete readonly = Yes

```

Yes, I know I shouldn't be using these permissions but It works for me. I think my whole permissions is a mess though :)

I just need to be able to access /data/storage from windows without being nagged.

Matt

---

### Post by matt91 on 2009-06-16
Removing the force user fixed it.

---

