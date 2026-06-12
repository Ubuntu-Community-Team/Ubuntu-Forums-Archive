---
title: "Samba/Xubuntu 7.04 help"
date: 2007-06-06
forum: Desktop Environments
---

### Post by rockbot on 2007-06-06
completely new to this os. I have the following problem. I have sucessfully installed xubuntu by following this guide:

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4)

I'm now stuck with the samba configuration.

> root@rockbot-desktop:/etc/samba# gedit smb.conf

(gedit:5248): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
root@rockbot-desktop:/etc/samba# /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ OK ] 
 * Starting Samba daemons...                                             [ OK ] 
root@rockbot-desktop:/etc/samba# smbpasswd -a Username
New SMB password:
Retype new SMB password:
Failed to modify password entry for user Username


The above is copied and pasted from the terminal. I get the above "not found" errors when opening and saving the config file. I continue anyway only to have it reject my password which I typed and retyped at least 20 times. I suspect there is more than 1 problem going on here. Below please find a copy of my smb.conf file modified as per the tutorial:

> [global]
panic action = /usr/share/samba/panic-action %d
workgroup = "rockhome"
netbios name = "rockbot"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700


Please help if you can andlet me know if any additional info is needed. Keep in mind your dealing with a beginner :)

---

