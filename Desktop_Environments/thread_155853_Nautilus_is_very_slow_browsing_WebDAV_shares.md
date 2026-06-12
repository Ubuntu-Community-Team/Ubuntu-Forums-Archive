---
title: "Nautilus is very slow browsing WebDAV shares"
date: 2006-04-05
forum: Desktop Environments
---

### Post by linhgb on 2006-04-05
Hi all,

I have a WebDAV-enabled web application on a Debian Sarge server, dual Xeon 2.4 and 1GB of RAM. I'm accessing it via the local 100Mbps connection, from my Ubuntu Breezy box and a WinXP laptop. Connecting to it via Nautilus is unbearably slow and from the output of the 'top' command on the **server**, the CPU usage shoots up to between 25 and 60% on 2 apache2 processes. The WinXP client (which is Explorer) and the Linux command line client cadaver use about 8% max each. Is this a Nautilus or Gnome-vfs2 problem? Does anyone know any fix, or another GUI client for Linux? I can handle the command line fine and I think cadaver is OK for me but others here may prefer a GUI client.

Thanks a lot.

P.S: I had a look at davfs2 but this one stores password in cleartext in a file chmodded 600 owned by root so it's not an option for us (policy, shared machine issue).

---

