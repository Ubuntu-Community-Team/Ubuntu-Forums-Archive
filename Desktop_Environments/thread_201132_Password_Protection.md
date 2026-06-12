---
title: "Password Protection"
date: 2006-06-21
forum: Desktop Environments
---

### Post by lonelypauly on 2006-06-21
Was wondering if there is a way to password protect certain folders on my desktop.  any way to do that?

---

### Post by Winblowz on 2006-06-21
I think you should be able to just right-click the file and go to properties to set the permissions. At least thats how it is in KDE (Kubuntu).

---

### Post by lonelypauly on 2006-06-21
i am aware of that...but what i want is a password prompt that opens for certain folders, ya know? in case my pc is on and somebody gets curious

---

### Post by aysiu on 2008-03-31
> **lonelypauly said:**
> i am aware of that...but what i want is a password prompt that opens for certain folders, ya know? in case my pc is on and somebody gets curious
You can lock your desktop in both Gnome and KDE.

---

### Post by jakupl on 2008-03-31
you could write ```
sudo chmod 000 'file'
```

than you need super user privileges to open it.

---

### Post by jakupl on 2008-03-31
This is not secure at alll though... the only really good way is encrypting it.
try seahorse if you want, you will find it in synaptic package manager.

---

### Post by MountainX on 2008-03-31
For my needs changing the owner and the permissions is probably exactly what I need. Here is another thread where I received a detailed answer:
[http://ubuntuforums.org/showthread.php?t=741140](http://ubuntuforums.org/showthread.php?t=741140)

I'm thinking I'll change the folder owner (to say, "notroot") and do chmod 0700 kind of like jakupl suggests, and then do the following as suggested in the other thread:
```
gksudo -u notroot nautilus
```

My only issue is that Nautilus "forgets" a bunch of settings when I open it like this - or at least that's my impression of what happens. But that's a minor issue.

Overall, I think this is a good solution for me.

---

