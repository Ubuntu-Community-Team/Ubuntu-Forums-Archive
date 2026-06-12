---
title: "Automount Samba shares - not showing in Places"
date: 2009-05-25
forum: General Help
---

### Post by randyklein99 on 2009-05-25
I have successfully been able to automount my samba shares to /mnt/SharedPictures.  However, they do not show in the Places menu. Before, I was automounting them to /home/user/SharedPictures and it showed up in the Places menu.  

Do I need to add anything to the /etc/fstab file to have it show in Places?

Here is the automount from that file:
```

# samba Pictures
//192.168.1.100/myfiles/Pictures /mnt/SharedPictures cifs credentials=/home/user/.smbpasswd 0 0

```

---

### Post by randyklein99 on 2009-05-25
Well, I was finally able to put together the right mix of search words and found an answer.  In Nautilus, you simply need to browse to the directory /mnt/SharedPictures and add it as a bookmark. It then shows up in Places and survives a reboot.

Apparently, if you mount to /media instead of /mnt this is done automatically.  

Is there a way to add this auto feature for anything in /mnt as well?

---

