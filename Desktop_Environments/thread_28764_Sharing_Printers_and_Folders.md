---
title: "Sharing Printers and Folders"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Rodrigo on 2005-04-21
Wich method will be better to share a printer and folders for this case?
  4 pc using Kubuntu, 1 router, 1 printer on the "main" pc (its main becouse it has the printer hehe :wink: )
  and in that "main" pc a folder filled with music and other goodies ready to be shared.

---

### Post by squallbsr on 2005-04-21
As for sharing your printer, you can use cups and give each of the other pcs the url for the cups printer.  I don't have a lot of info on that, but IIRC you can do the printer that way.

As for sharing your music, you can use NFS, Samba, CODA, and many others.  NFS is probably the easiest to setup (install the NFS server, edit /etc/imports /etc/exports -- IIRC), Samba works too (use smbmount) but will take a little bit more setup.  Samba probably will tolerate a broken network link (a machine being rebooted) better than NFS.

Disclaimer: Its been a while since I messed with NFS, I have never used CODA or any of the other networking filesystems.  I would use Samba if there is EVER going to be a windoze box on the network (i.e. - Friends coming over with their WinXP Laptop, etc), that is if you feel like sharing...

---

### Post by Gianni Exile on 2005-04-21
The easiest is Samba IMHO.

NFS is quite easy too, but things break "hard" and it's easier to share with other OS's in the future using Samba.

Do "apt-get install samba" on the main machine, then in KDE right click the folder  you  wish to share, and set it up for "guest access".  You may wish to also manually add the following lines to /etc/samba/smb.conf file, in the "[global]" section, making that machine a Primay Controller for your domain.
```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
workgroup = WORKGROUP
domain master = yes
local master = yes 
os level = 65
preferred master = yes

```

Now the other machines will be able to see it automatically on the LAN.  You can also install "smbmount" and mount the shared drive at boot time, or use automount to mount it on demand.  Mounting the shared drive is better since it is  transparent to applications, and if you use shared accounts via LDAP/NIS (or just users/groups ID numbers are the same on all machines) than all permissions should work as well.  Samba won't lock your machines up either, or make things hang like NFS can.  For completely static mounts, over long times, NFS is a  bit faster.

---

