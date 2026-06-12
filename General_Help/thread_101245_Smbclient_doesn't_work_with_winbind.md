---
title: "Smbclient doesn't work with winbind?"
date: 2005-12-09
forum: General Help
---

### Post by talbot on 2005-12-09
Hi folks,

I followed the instructions on the [HOWTO: NT Domain Authentication ]("http://ubuntuforums.org/showthread.php?t=5409") and now i can log on my office's network domain. :p 

Everything is working fine except the sound, who doesn't work when I'm logged with my NT user, and the single sign on.
I thought that if log in using the winbind and the pam modules I could use the Samba utilities without having to enter my password again, but it keeps asking every time I call the smbclient program or I try to browse a machine using nautilus 

Somebody knows if this behavior is expected or I made some mistake?

Thanks in advance

My smb.conf file:

```

# Global parameters
[global]
        workgroup = PLANUM
        server string = %h server (Samba, Ubuntu)
        security = domain
        obey pam restrictions = Yes
        password server = 172.31.1.1
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins server = 172.31.1.7
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template shell = /bin/bash
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

```

---

