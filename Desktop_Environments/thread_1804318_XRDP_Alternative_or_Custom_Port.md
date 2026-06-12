---
title: "XRDP Alternative or Custom Port"
date: 2011-07-14
forum: Desktop Environments
---

### Post by jbayne3 on 2011-07-14
Hello All,
 
I've recently setup XRDP on my Ubuntu Workstation (11.04, Gnome). XRDP works just fine when I have it set to the default RDP port (TCP 3389) or customly set to a higher port number (i.e. TCP 7432). I've noticed when I try to change it to a lower-numbered port (i.e. TCP 110), the XRDP process dies. The XRDP-sesman process remains functional. Does anyone have any insight why this may be the case? 
 
My only consideration would be to step through the source code and make a (hopefully) minor modification and re-compile. Any help or recommendations would be grateful, especially, since I do not want to re-compile :-)
 
Thank you,
 
Jimmy

---

### Post by jbayne3 on 2011-07-14
Correction:
 
The change of port does not work for any numbers under 1024.  1025 and above work.  This may bring me a step closer to resolving this...

---

### Post by majickmann on 2011-11-05
Traditionally only the root user is allowed to bind() to a port with a number lower than 1024.

Hope this helps...
:-)

---

