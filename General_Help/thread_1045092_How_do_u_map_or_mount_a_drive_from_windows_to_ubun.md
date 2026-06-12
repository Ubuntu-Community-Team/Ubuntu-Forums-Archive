---
title: "How do u map or mount a drive from windows to ubuntu or ubunto to ubuntu?"
date: 2009-01-20
forum: General Help
---

### Post by Linuxwho? on 2009-01-20
Also, does any type of setting need to be changed to allow users to ssh and/or vnc into the ubuntu server?  Thanks.

---

### Post by handband2 on 2009-01-20
Check out these two posts:
Map Network Drive
[http://ubuntuforums.org/showthread.php?t=1045108](http://ubuntuforums.org/showthread.php?t=1045108)

HOWTO: sshfs (mounting remote directories trough ssh)
[http://ubuntuforums.org/showthread.php?p=1618910](http://ubuntuforums.org/showthread.php?p=1618910)

---

### Post by HermanAB on 2009-01-20
From easiest to most difficult:
FTP (vsftp or proftp with FileZilla on Windows)
NFS (with Services for Unix installed on Windows - free download from MS)
Samba (Windows networking)

See this:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

FTP needs no configuration.  NFS only needs ONE line of configuration.  Samba needs hundreds.

Cheers,

Herman

---

### Post by Linuxwho? on 2009-01-20
Thanks !!  :)  I am basically looking for command line.  I should have stated that but forgot...  Looks like it has to be setup to work unlike where windows you just either type in the cmd prompt.?

---

