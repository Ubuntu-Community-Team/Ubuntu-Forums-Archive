---
title: "Autofs with Chinese filenames problem"
date: 2005-12-20
forum: General Help
---

### Post by mosestruong on 2005-12-20
I'm experiencing some problems with autofs of samba shares - the filenames with Chinese characters are not displayed correctly.

An example of the auto.dan config file:

photos  -fstype=smbfs,username=<user>,password=<pwd>,rw,gid=700,fmask=774,dmask=775      ://dan/photos

Which is referred to in the auto.master
/dan    /etc/auto.dan --timeout=60

Does anyone know if this is correct? Or are there a way around this problem?

Any help would be greatly appreciated!

moses

---

### Post by mosestruong on 2005-12-20
In case anyone else has the same problem, I've found the solution at [http://lists.samba.org/archive/linux-cifs-client/2005-July/000893.html](http://lists.samba.org/archive/linux-cifs-client/2005-July/000893.html)

All you need to do is change the fstype from smbfs to cifs and add iocharset=utf8 to the list of options.

This solution works for fstab too I think.

---

### Post by mosestruong on 2006-07-20
qiet72 has provided the solution to this problem in another thread at
[http://www.ubuntuforums.org/showthread.php?t=111924](http://www.ubuntuforums.org/showthread.php?t=111924)

---

