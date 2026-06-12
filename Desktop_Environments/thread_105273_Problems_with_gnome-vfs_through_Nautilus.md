---
title: "Problems with gnome-vfs through Nautilus"
date: 2005-12-18
forum: Desktop Environments
---

### Post by cpugeniusmv on 2005-12-18
The other day I mounted an FTP server so that I could access it through Nautilus and other applications.  Today I cannot.

The only thing I have done that probably would have caused this is some major changes to permissions recursively in my home directory.  (go-rwx)

I seem to be able to mount the FTP server, but when I try to access it (before it asks for a password) it gives me:

> Couldn't display "ftp://*username*@*hostname*:*port*/".

I dug around as much as I could stand and couldn't find anything it might need to access in my home directory (and it's running as me anyway, right?).  Any ideas?

EDIT: SSH (SFTP) seems to work.  But I'd still like to get to the bottom of this FTP issue.

---

### Post by cpugeniusmv on 2005-12-20
Now it's showing a different message:

> Details: There is no default action associated with this location.

Assuming I need to setup a default action for that location, how would I go about doing so?

---

### Post by Yoda_Oz on 2006-01-06
im having the same problem! bump!

---

### Post by borisattva on 2006-01-22
hey guys, i was having the exact same problem until i accidently found the explanation and posted it [here]("http://ubuntuforums.org/showpost.php?p=675050&postcount=10").

hopefully it can be of some use to you still

---

