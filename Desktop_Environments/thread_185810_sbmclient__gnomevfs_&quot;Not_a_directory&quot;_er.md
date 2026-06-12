---
title: "sbmclient / gnomevfs &quot;Not a directory&quot; error on Windows share"
date: 2006-06-01
forum: Desktop Environments
---

### Post by sander marechal on 2006-06-01
Hello,

I have connected to a Windows share using the Places -> Connect to server option. Ik can open the share in Nautilus and browse it, but I cannot open any files. I get a "Not a directory" error.

I also tried it from the console:

```

$ gedit smb://<domain>%3B<username>@<server>/path/to/somefile.txt

** (gedit:16461): WARNING **: Hit unhandled case 19 (Not a directory) in gedit_unrecoverable_loading_error_message_area_new.

(gedit:16461): libgnomevfs-WARNING **: trying to read a non-existing handle

$

```

I'm wresting with this for quite some time now. I really need to be able to use this share or I might as well switch my work PC back to WinXP :-(

EDIT: I should probabely add that I don't have this problem with other shares on our corporate network. Just the one that I need most.

---

### Post by Filippo on 2006-06-07
Same problem after udate to dapper.

For now :
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28share%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28share%29)

I don't know if there is a problem with **libgnomevfs2-extra**

Using nautilus for mount a remote samba share is all right,
instead with a win domain, i can browse the network, but I can't use/edit remote file with "Not a directory" error.

---

### Post by sander marechal on 2006-06-07
Thank you, mounting an smbfs works great!

One pointer for other people: If you cannot mount a windows share as an smbfs file system (or if you get errors if you do that), mount it as a cifs file system.

---

