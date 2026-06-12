---
title: "Nautilus in 18.04 can't browse samba network tree"
date: 2018-06-16
forum: Desktop Environments
---

### Post by s-byczkowski on 2018-06-16
Nautilus in Bionic Beaver 18.04 (all packages up to date) can not browse samba tree after clicking "Windows Network" icon. It will show "Empty Folder". When typing server address smb://192.168.1.1 or smb://server_name it will connect to the samba host and show me shared folders/printers over smb protocol. No problem here. 
The problem is with smb tree browsing. There is a part of Gnome - gnome virtual file system and gvfsd-smb-browse which should show the smb tree output, but it has a problem which I can see if I do in terminal:
```

killall gvfsd-smb-browse && GVFS_DEBUG=1 /usr/lib/gvfs/gvfsd-smb-browse

```
and click Windows Network in Nautilus I see:
```

smb-network: Queued new job 0x55b19a2c9f40 (GVfsJobCreateMonitor)
smb-network: [COLOR=#ff0000]send_reply(0x55b19a2c9f40), failed=1 (Action not supported by the processing engine)[/COLOR]
smb-network: backend_dbus_handler org.gtk.vfs.Mount:QueryFilesystemInfo (pid=5708)
smb-network: Queued new job 0x55b19a2e7820 (GVfsJobQueryFsInfo)
smb-network: send_reply(0x55b19a2e7820), failed=0 ()
smb-network: backend_dbus_handler org.gtk.vfs.Mount:Enumerate (pid=5708)
smb-network: Queued new job 0x55b19a2c30c0 (GVfsJobEnumerate)
smb-network: send_reply(0x55b19a2c30c0), failed=0 ()

```

[COLOR=#ff0000]I can see the smb tree if I do smbtree in terminal, no problem![/COLOR]

I think this "action not supported by processing engine" is the culprit of Nautilus not being able to browse smb tree.
But what is this problem??? Wrong compilation options or compilation against wrong samba package???

---

### Post by Morbius1 on 2018-06-16
Same answer I gave you before:
> > **Morbius1 said:**
> Edit /etc/samba/smb.conf.

If you don't have an smb.conf install smbclient: sudo apt install smbclient

Right below the workgroup = WORKGROUP line add this line:
```
client max protocol = NT1
```

Does it work now? If it does remember:

Good News: You should be able to browse again for samba / smb hosts.
Bad News: Even though you will be able to see it you will not be able to  access any host that has disabled SMB1 - like Win10.


The default for "client max protocol" was changed to SMB3 so that it could connect to a Win10 machine or any other machine that has disabled SMB1. This change inadvertently disabled the ability of the file manager to browse the network - at least for netbios names. They fixed it for smbtree by temporarily dropping down to SMB1 ( what samba calls NT1 ) but they haven't fixed it for libsmbclient which is what gvfs uses.

Note: This is a browsing problem not a host name resolution problem. You can still connect to the other machine by name but you must do it explicitly.

[COLOR=#0000cd]**EDIT**[/COLOR]: I actually talked about this before 18.04 was released: [Bionic Beaver can not discover samba hosts - netbios.  ]("https://ubuntuforums.org/showthread.php?t=2384959")

---

### Post by s-byczkowski on 2018-06-23
OK. SO why the smbtree,smbclient commands work but Nautilus and -> gvfs-smb-browse does not?
And I do not have to put "client max protocol = NT1" in smb.conf for the smbtree to work  and browse thru the smb network. But gvfs-smb-browse has a problem and  that is why Nautilus can not browse sabma network.
It is Gnome gvfs problem. But what it is exactly? The debug message from gvfs is not really helpful here, is it?
There is a thread about it at [RedHat Bugzilla]("https://bugzilla.redhat.com/show_bug.cgi?id=1513394") and there also this [patch for gvfs-smb-browse]("https://bugzilla.redhat.com/attachment.cgi?oldid=1400829&newid=1400830&action=interdiff&format=raw")[URL="https://bugzilla.redhat.com/show_bug.cgi?id=1513394"] which forces it to switch to NT1 what smbtree and smbclient are doing now by design. It is not safe to use NT1 on all samba. After recompilation of gvfs-smb-browse Nautilus displays smbtree.
[/URL]

---

### Post by s-byczkowski on 2018-06-23
Analazing source code I found GVFS_SMB_DEBUG variable
```
killall gvfsd-smb-browse && GVFS_SMB_DEBUG=1 /usr/lib/gvfs/gvfsd-smb-browse
```
gives this:
```
Using netbios name UBUNTU BIONIC.
Using workgroup WORKGROUP.
Kerberos auth with 'user@WORKGROUP' (WORKGROUP\user) to access '192.168.1.1' not possible
WARNING: The "syslog" option is deprecated
Using netbios name UBUNTU BIONIC.
Using workgroup WORKGROUP.
SPNEGO: Could not find a suitable mechtype in NEG_TOKEN_INIT
Performing aggressive shutdown.
Kerberos auth with 'user@WORKGROUP' (WORKGROUP\user) to access '192.168.1.1' not possible

```

---

