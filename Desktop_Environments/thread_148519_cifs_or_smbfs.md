---
title: "cifs or smbfs"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Scanner on 2006-03-22
This may have been discussed in the past but I didn't find anything with a quick scan of the forums.  I am pretty familar with smbfs and have been using it for a while to connect shares on our Windows servers, but recently someone asked me why I wasn't using cifs instead, and mentioned that cifs was the newer supported format and would be easier.  What is the difference and in someone with more knowledge than me which should I be using?

---

### Post by scubajeff on 2006-03-22
As far as I know, if your windows server is 2003, you should use cifs instead of smbfs.

---

### Post by kwelndar on 2006-03-23
I don't know about being easier, but cifs is designed to replace smbfs.  Both can be compiled into the kernel and be used without conflict, so you might want to try both to see which you like. There are some differences though so you might want to check the requirements of the Windows server version to see which would be more compatible.

The cifs filesystem client was considered "experimental" until Linux kernel 2.6.7 (cifs version 1.9).

See the [CIFS vfs page]("http://linux-cifs.samba.org/") at Samba.org

---

### Post by dcstar on 2006-03-23
[QUOTE=Scanner]This may have been discussed in the past but I didn't find anything with a quick scan of the forums.  I am pretty familar with smbfs and have been using it for a while to connect shares on our Windows servers, but recently someone asked me why I wasn't using cifs instead, and mentioned that cifs was the newer supported format and would be easier.  What is the difference and in someone with more knowledge than me which should I be using?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=128873&highlight=cifs](http://ubuntuforums.org/showthread.php?t=128873&highlight=cifs)

---

### Post by Scanner on 2006-03-24
Thanks, cifs it is.  It does seem easier and faster.

---

### Post by queenorych on 2006-03-24
In the past I have also had issue with large file support for smb mounts.  cifs worked great.

---

