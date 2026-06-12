---
title: "How to assign samba share permissions?"
date: 2009-01-21
forum: General Help
---

### Post by lumix on 2009-01-21
Seems like this should be very straight-forward, yet I can find nothing on this.  So if I create share [foo] in my smb.conf, how (presumably in smbpasswd) do I give Bob rights to use said share?

I suppose that implicit in this question is the hope that share and file/folder permissions are separate, since we wouldn't want to assume that smb users ought to have the same privileges as, say, ssh users.

---

### Post by ajmorris on 2009-01-22
hi there,
here is an example entry for your smb.conf:
```
[foo]
comment = foo
path = /foo 
valid users = bob
public = no
writable = yes
printable = no
create mask = 0765
```

An entry like that would be what you are looking for, you can play around with your permission mask etc as well.

Before testing out your newly created share, make sure you restart your samba daemon first :)


AJ

---

### Post by cariboo on 2009-01-22
I found [Samba 3 by Example]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf") a great help when I origionally setup Samba. The examples range from a samll network to very large networks.

Jim

---

### Post by Yashiro on 2009-01-23
Be aware that setting up a shared folder using ubuntu's nautilus interface **does not create traditional samba shares**. It creates usershares which are configured differently to traditional shares.

---

