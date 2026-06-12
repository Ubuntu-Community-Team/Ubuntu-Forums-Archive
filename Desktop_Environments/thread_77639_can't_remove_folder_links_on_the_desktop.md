---
title: "can't remove folder links on the desktop"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Jnifoo on 2005-10-17
Using a clean install of breezy on my workstation (keep my /home from hoary)
Now, I just can't delete any link on my desktop in X session (gnome - no difference with a kernel optimized for K7 or i386).
Message is always the same : "error not on the same file system when trying to delete /home/jnifoo/thelinkedfolder" (free translation of a the french message)
But actually, I just want to remove the link and not the folder where the link point to.

Any idea or suggestion to do this ? On Hoary, there is no problem with this current action. Perhaps I miss a package to install ?

Thanks for your support.

---

### Post by Pablo_Escobar on 2005-10-17
Quick question : We're not these folders created or copied with root account ?

---

### Post by Jnifoo on 2005-10-17
Hum, seems that you are right... This links are coming from an intranet, and yes it belongs to root, but with a chmod 777.
Just don't understand why this is a problem under Breezy and not under Hoary.
Any solution ?

---

### Post by Jnifoo on 2005-10-17
replying to myself... 
solution is easy but not user friendly : unlink with a sudo commande and it is ok. 

Actually, my network disks (via samba) are automatically mounted as a root process in the fstab, perhaps I have to change this to find a user friendly solution on unlinking.

Thx Pablo: you're question was the answer :)

---

### Post by Pablo_Escobar on 2005-10-17
Glad to be of service :) I hope your Samba setup will work well :)

---

