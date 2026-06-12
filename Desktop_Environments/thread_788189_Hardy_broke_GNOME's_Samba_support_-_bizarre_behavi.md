---
title: "Hardy broke GNOME's Samba support - bizarre behavior"
date: 2008-05-09
forum: Desktop Environments
---

### Post by Shii on 2008-05-09
What I did in both 7.10 and 8.04:

Places -> Connect to Server...

type in SMB domain, share, folder, and username

What 7.10 did:

Connected me to the correct folder immediately, and created a link to the folder on my desktop. When I log out and log back in, the folder is happily still there.

What 8.04 does:

Prints out this error message:

> Can't display location "smb://domain/share/folder

The specified location is not mounted

Creates a link for the ROOT share on my desktop (WHY?!)

When I open it up, creates a SECOND link to the root share on my desktop

When I log out, both links disappear permanently

---

### Post by chrism3568 on 2008-05-12
Try the following from a terminal window but replace the 'windowsbox' with the IP address. Using the client from the terminal will provide you with any error messages. This worked for me.

smbclient //windowsbox/share

example smbclient //192.168.2.2/share

---

### Post by Shii on 2008-05-16
```
shii@daxyne:~$ smbclient //home.its.longdomain.com/home
session request to HOME.ITS.LONGDOM failed (Called name not present)
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```
I did enter the password right, too

---

