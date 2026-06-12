---
title: "Unable to Connect to SSH Server"
date: 2005-04-30
forum: Desktop Environments
---

### Post by mdavidn on 2005-04-30
I'm using a fresh install of Hoary straight off the CD. I updated my system using APT, but it only downloaded packages related to OpenOffice.org.

I'm trying to connect to an SFTP server using Nautilus. I've tried various combinations of options in the "Connect To Server" dialog. I've tried various "Service types," I've tried the hostname with and without the protocol "sftp:" or "ssh:", etc. It just never connects to either a remote server or the other machine on my LAN. When it attempts to connect, often there's no network traffic at all. When connecting to my other local box, Nautilus will sometimes initiate a connection and prompt for a password, after which it displays a blank, brown "Nautilus" window with no files. Any suggestions?

I have no problems connecting to either of these servers with the OpenSSH utilities "ssh" or "scp".

---

### Post by mdavidn on 2005-05-01
I fixed this problem by marking all the gnomevfs packages for reinstallation. For some reason, the freshly installed packages didn't work properly.

---

