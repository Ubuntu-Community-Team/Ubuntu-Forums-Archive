---
title: "CLI rdesktop (or similar) in framebuffer"
date: 2009-05-17
forum: General Help
---

### Post by Jose Catre-Vandis on 2009-05-17
Is there an app available that can run an Windows remote screen in the framebuffer (i.e. in a CLI environment)?

I can use directvnc to access linux vnc servers in the framebuffer, but would like to be able to access windows machines using the framebuffer too.

or is my only recourse to install a vnc server in the windows machine?

---

### Post by mb_webguy on 2009-05-17
If you're trying to remotely access a Windows machine from a Linux CLI, I'd suggest installing a ssh server on the Windows machine.  Here's a link to an article discussing the installation of an [ssh server on Windows Server 2008]("http://www.windowsnetworking.com/articles_tutorials/install-SSH-Server-Windows-Server-2008.html"), but it should apply to other versions of Windows as well.

---

### Post by Jose Catre-Vandis on 2009-05-17
Thanks mb-webguy, but that only really gives a command line into the windows machine (unless I can shh -X or Y ??), I was after the full graphical experience through the framebuffer.

For now I have installed tightvnc on the windows machine, opened up the firewall for it, and can happily bring it up with directvnc on the framebuffer. (No X running)

---

