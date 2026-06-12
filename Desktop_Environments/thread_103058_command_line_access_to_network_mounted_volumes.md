---
title: "command line access to network mounted volumes?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by jlapier on 2005-12-13
If I mount a volume by using the "Connect to Server" icon in the "Places" menu - say, an SMB share or a webDAV connection, or whatever I happen to be working with at the time - is there a way to use the command line to browse that connection? I want to be able to search and grep and stuff like that via a terminal. For example, in OS X whenever you connect to a server share, you can load up a terminal and go to /Volumes/*server-connection*.

Any thoughts? Seems like an easy one, and maybe I just need more coffee...

- Jason

---

### Post by 23meg on 2005-12-13
Try the smbclient command. Type ```
man smbclient
``` to learn details on usage.

---

### Post by jlapier on 2005-12-13
[QUOTE=23meg]Try the smbclient command.[/QUOTE]

Thanks for the reply, but that's not really what I'm looking for.

smbclient gives you an ftp-like connection to an smb share. Upon connection, you get an smb shell-like prompt that only runs a small subset of commands for browsing directories and files, tranferring, and archiving. It doesn't allow commands like "grep" or "cat". It also does not allow connections to webdav servers (please correct me if I'm wrong).

---

### Post by kaamos on 2005-12-13
One way is to mount the share.

A line in my /etc/fstab:
```
//192.168.8.17/Lacie        /media/Lacie  smbfs    credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

---

### Post by anthro398 on 2005-12-13
You're mistaken.  smbclient can mount the remote share to a  local mount point, say /mnt/remote_share and you can then use it as you would any other filesystem on your local machine.

---

