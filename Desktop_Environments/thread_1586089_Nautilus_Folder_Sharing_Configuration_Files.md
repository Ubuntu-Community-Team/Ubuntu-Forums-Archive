---
title: "Nautilus: Folder Sharing Configuration Files"
date: 2010-10-01
forum: Desktop Environments
---

### Post by crypticlabs on 2010-10-01
Can someone please tell me where the smb.conf file is that Nautilus uses when enabling "Folder Sharing" (when alternate clicking the folder in Nautilus and selecting the option "Sharing Options")? The file /etc/samba/smb.conf does not seem to be the file Nautilus is using.

Thanks.

---

### Post by David2926 on 2010-10-01
Try thie file in your home folder.
/home/"user"/.gnome2/nautilus-share-modified-permissions

---

### Post by loopodoopo on 2010-10-01
Hi crypticlabs, 

The configuration for the shares can be found in:

```
/var/lib/samba/usershares
```

In this folder you can find the name of your share.

---

### Post by luvshines on 2010-10-01
This link gives other info as well:
[http://ubuntuforums.org/showthread.php?p=9003359](http://ubuntuforums.org/showthread.php?p=9003359)

---

### Post by endotherm on 2010-10-01
you can use 
```
net usershare info
``` to access the nautilus-share specific parts of your configuration. the rest (the global stuff like workgroup name and whatnot) still remain in /etc/samba/smb.conf. just remember, you cannot have duplicated config statement between the two, so make sure you don;t define usershares in your smb.conf.

---

### Post by crypticlabs on 2010-10-01
Thanks everyone. This is exactly the information I was looking for.

---

