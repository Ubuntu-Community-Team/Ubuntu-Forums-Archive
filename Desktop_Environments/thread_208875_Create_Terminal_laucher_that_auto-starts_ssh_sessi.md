---
title: "Create Terminal laucher that auto-starts ssh session"
date: 2006-07-04
forum: Desktop Environments
---

### Post by artelsj on 2006-07-04
My webhost allows ssh access. Is it possible to have a launcher icon in the GNOME panel that automatically starts a ssh session in gnome-terminal? Preferably without having to enter my password, but I'd survive if that's impossible.

---

### Post by llamakc on 2006-07-04
If you use ssh-keys you won't need to enter a password. So your launcher would have in the 'command' field:

gnome-terminal -e "ssh you@somewhere"

SSH-keys rock!

I just tested this and it works perfectly.

---

### Post by artelsj on 2006-07-04
Okay, cool this works...

Thanks!

---

### Post by sewmyheadon on 2008-01-17
Really splendid way to use SSH in a launcher -  thanks for the tip!

---

