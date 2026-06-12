---
title: "Saving files from workstation to server"
date: 2008-03-06
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2008-03-06
Hi all,

Have Xubuntu install on workstations and trying to browse the network directories to the server so I can create shortcuts on the desktop.  In other words, if someone creates a document and wants to save it to the server, how do I make a direct connection to it using the file browsing?   I can't seem to locate the server from Xubuntu although I can connect to it via a web interface, (but it's clunky hence the need for a direct folder/browse.

Can someone show me how please?

---

### Post by jcwmoore on 2008-03-06
I think you want something like sshfs, is program uses ssh to connect to a server and the mounts a server folder on to a local folder the basic usage for sshfs is 
```
sshfs user@host:/path/to/folder /path/to/local/folder
```

---

