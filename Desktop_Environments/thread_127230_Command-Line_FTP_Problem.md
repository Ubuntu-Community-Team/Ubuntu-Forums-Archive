---
title: "Command-Line FTP Problem"
date: 2006-02-08
forum: Desktop Environments
---

### Post by SuperMike on 2006-02-08
When I do command-line FTP on Ubuntu 5.10, and try to upload a binary file to an FTP server, it starts off by saying it's going into BINARY mode and to wait while it copies it up. But then it takes forever and I have no choice but to do CTRL+C. Is this tool broke?

Note I connected and did:

lcd / <-- to change to the dir where the binary file was
cd incoming
pwd <-- to confirm I was where I needed to be
put myfile.tar.gz

Instead, I had to fire up gftp in GNOME and within seconds the file was copied over to the FTP server.

---

### Post by dcstar on 2006-02-08
[QUOTE=SuperMike]When I do command-line FTP on Ubuntu 5.10, and try to upload a binary file to an FTP server, it starts off by saying it's going into BINARY mode and to wait while it copies it up. But then it takes forever and I have no choice but to do CTRL+C. Is this tool broke?

Note I connected and did:

lcd / <-- to change to the dir where the binary file was
cd incoming
pwd <-- to confirm I was where I needed to be
put myfile.tar.gz

Instead, I had to fire up gftp in GNOME and within seconds the file was copied over to the FTP server.[/QUOTE]
Try pftp (the default Passive Mode version)

---

