---
title: "File Append Rather than Overwrite using gvfs"
date: 2009-01-19
forum: General Help
---

### Post by jadymitchell on 2009-01-19
I have been blissfully using Geany in concert with gvfs on Hardy for some time to easily edit files on a remote server.  All of a sudden, when I save changes to a file with Geany (using an ftp connection via gvfs 0.2.5ubuntu3), the file will append rather than overwrite.  It will only do this on some remote servers, not others.  

The problem is not Geany related as the same thing happens with other non-GVFS enabled applications such as Leafpad.  I have considered that it is a problem with the remote server, but I have no way to change the configuration of the remote server and, even if I did, wouldn't know where to begin.

Can anyone suggest a way to go about troubleshooting this problem?  Thank you.

---

### Post by jadymitchell on 2009-01-21
Bump

---

### Post by llevering on 2009-06-17
I do have the same problem with Interepid Ibex, gvfs 1.0.2.0-ubuntu3. Is there anybody who had the same problem and found a workaround? I hope so!

---

### Post by Bobly on 2010-10-29
Resurecting an old post as it still comes up in google searches for this bug.


Proper behaviour can be achieved by connecting to the FTP server through nautilus over SFTP (SSH) rather than FTP. Geany will then open files from the remote server and properly overwrite when saving.

---

### Post by habl on 2010-11-08
Same problem here on lucid lynx. Using Geany and gedit, both have the same problem. Really annoying, I have to use tools like filezilla now when working on FTP server.

Switching to SFTP is not an option, the server is FTP only and it's a hosted server without any rights to change things.

Would really appreciate hints on how to fix this since filezilla is just annoying.

It's pretty hard to reproduce the problem, since it doesn't happen on all servers (server with the problem is using ProFTPD 1.3.2 in case anybody is interested). Have a couple of more FTP servers (using vsFTPd 2.0.1) which are working fine.

Don't know what information is usefull and what not so just ask if more is needed.

---

### Post by habl on 2010-11-08
There is a bug report for it, see [https://bugs.launchpad.net/bugs/507236](https://bugs.launchpad.net/bugs/507236)

Still if somebody knows a workaround feel free to let me know =)

---

