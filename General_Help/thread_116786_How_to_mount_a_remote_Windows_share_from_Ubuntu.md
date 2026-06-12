---
title: "How to mount a remote Windows share from Ubuntu?"
date: 2006-01-13
forum: General Help
---

### Post by Robor on 2006-01-13
I've got Ubuntu Breezy loaded on my IBM T42 laptop.  It's not always at my house so I don't want to put a mount in fstab but I'd still like to quickly access a remote share on my Win2003 Server.  I guess the easiest thing to so is put a 'launcher' on my desktop that points to a remote share on my Win2003 Server.  My first attempt was to map to the entire drive via the Administrative share (//servername/E$) and my second attempt was '//servername/sharename'.  

I've done some reading and attempted some commands but so far all attempts have failed.  I'm currently at work so I can't give the specific error message but I remember it had something to do with the mount point not existing.  However, the mount point did exist and I was able to create/delete files inside the mount point directory.

I should note that (after entering my Windows password) I was able to browse my network via nautalus.  Any ideas?

---

### Post by oakz on 2006-01-13
Go to Places -> Connect to Server...
For "Service Type" select "Windows Share",  fill in the rest of the information. If it connects it should create a shortcut on your desktop that you can later use to bring up the share.

---

### Post by Robor on 2006-01-13
[QUOTE=oakz]Go to Places -> Connect to Server...
For "Service Type" select "Windows Share",  fill in the rest of the information. If it connects it should create a shortcut on your desktop that you can later use to bring up the share.[/QUOTE]
Nice!  I guess I was trying to do it the hard way, eh?  I'll give that a try when I get home.  Thanks!  :p

---

### Post by matt.raffel on 2008-04-14
> **oakz said:**
> Go to Places -> Connect to Server...
For "Service Type" select "Windows Share",  fill in the rest of the information. If it connects it should create a shortcut on your desktop that you can later use to bring up the share.

How does that work the with administrative share?   like H$?  

Btw, I do not have a domain controller....

Matt

---

