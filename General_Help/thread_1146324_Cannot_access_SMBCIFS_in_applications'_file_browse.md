---
title: "Cannot access SMB/CIFS in applications' file browser dialog"
date: 2009-05-02
forum: General Help
---

### Post by mrisher on 2009-05-02
Hi, all:

Running Ubuntu 9.04 (AMD64), I can mount a SMB share quite easily using the Nautilus/Gnome utilities. The drive is then mounted under ~/.gvfs/share_name and I can easily access it from Nautilus or from a terminal window.

However, several applications I'd like to use, like the included Transmission BitTorrent client, and Picassa, do not show this directory or the mounted drive in their built-in Open File dialog, therefore I cannot open from or save to my shared drive.

Can someone please help either a) change the mount point to a non-hidden directory (e.g. change ~/[COLOR=Red].[/COLOR]gvfs (dot-gvfs) to ~/mnt), or b) tell these other applications about my mounted directory?

Thank you.
/m

---

### Post by cariboo on 2009-05-02
You can manually mount the share either by using the mount command:

```
sudo mount //server/share /media/share
```

In order to manually mount the share you will need to install smbfs.

You can also setup the the share to be mounted automatically in fstab:

```
//server/share cifs /media/share  relatime 0  2
```

In both cases you will have to set the permissions of the mount point to allow it to be world read/writeable.

---

### Post by mrisher on 2009-05-02
Thanks for the reply. I have tried mounting via smbmount (or mount.cifs, which I think is the successor) but receive an error each time:

```

mark@mark-desktop:~$ sudo mount //192.168.1.13/storage ./gvfs
[sudo] password for mark: 
Password: 
[COLOR=Red]mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/COLOR]

```I am able to view the mounts via smbclient, so I do have a fundamental connection...

```

mark@mark-desktop:~$ smbclient -L 192.168.1.13 
Enter mark's password: 
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

    Sharename       Type      Comment
    ---------       ----      -------
    storage         Disk      
    IPC$            IPC       

```Should I infer that fuse/gvfs mounting will not be available to an application, and that a kernel mount is the right path to continue pursuing?

#EDIT: I have resolve this error by checking in syslog and finding a recommendation to try "-o nounix". Now it works. Thanks for your help!

---

