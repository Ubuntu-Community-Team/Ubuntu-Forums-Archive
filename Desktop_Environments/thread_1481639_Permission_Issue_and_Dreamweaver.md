---
title: "Permission Issue and Dreamweaver"
date: 2010-05-12
forum: Desktop Environments
---

### Post by dkundu on 2010-05-12
Hi,
 
I am migrating from Windows to Ubuntu. I am having a problem when trying to edit files using Dreamweaver - permission denied.
 
I have LAMPP installed and htdoc is sitting (/opt/lampp/htdoc) and I also installed macromedia dreamweaver 2004 MX through WINE. I set the site to [http://localhost](http://localhost) (/opt/lampp/htdoc). Everything is working fine. When I edit any file and try to save, it says "Permission denied". What I can do to allow Dreamweaver to read-write all files in htdoc.
 
Or should I connect htdoc through ftp and edit and upload through ftp? It will be very hectic. Please, let me know what I can do. Thanks.

---

### Post by 3rdalbum on 2010-05-12
Dreamweaver (and all your Wine programs) run as your ordinary user account. Your ordinary user account can't modify files that are outside your home directory, normally, for security and stability reasons.

However you can modify the permissions for the /opt/lampp/htdoc directory. Open a file browser as root (administrator):

```
gksudo nautilus
```

because those files are currently owned by root. Navigate to the /opt/lampp/directory. Right-click on htdoc and go to Properties, then the Permissions tab, and set it so "Others" can "Read and write" ('others' includes your user account, of course). Now Dreamweaver will be able to write directly to the htdocs directory.

---

