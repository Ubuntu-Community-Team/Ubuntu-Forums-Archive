---
title: "Can't create symlink to a folder. (using Nautilus now)"
date: 2008-12-05
forum: General Help
---

### Post by Mamsaac on 2008-12-05
First I tried using "ls -s" plus the destination and all (which didn't work), but now I tried using Nautilus. So, right click on the folder located on "/media/ARCHIVOS" called "Musica". I right click and choose "Create symlink" (actually "Crear enlace", but I hope translation is easy to understand) and it pops an error message saying that it couldn't be done and that the operation is not allowed.

Now, I don't know if this could be the reason (I hope not). The directory Musica is in another partition which's filesystem is FAT.

Any suggestions?

BTW, thanks for taking your time to help me in this =)

---

### Post by Mamsaac on 2008-12-05
Come on, don't ignore my thread =(

---

### Post by kpkeerthi on 2008-12-05
With could sym link a folder or a different partition.

To create a shortcut to '/media/ARCHIVOS/Musica' in your home folder, open a terminal and run the below command:
```

ln -s /media/ARCHIVOS/Musica **[COLOR="Red"]Musica[/COLOR]**

```

* Change the name highlighted to whatever you would like. Thats the name for the shortcut.

---

### Post by Mamsaac on 2008-12-05
Ah, stupid me using ls instead of ln.

Thanks =) I still don't get why Nautilus didn't work, but it doesn't matter.

---

### Post by p_quarles on 2008-12-05
I just tested this, and it looks like Nautilus defaults to creating the link in the present directory. In other words, it tried to create the symlink in /media/ rather than on your desktop, and of course you don't have permission to write things there under normal circumstances.

Perhaps someone else knows a way around this.

---

### Post by Mamsaac on 2008-12-05
Thanks, now I don't feel alone.

Anyway, I ended up not using a symlink for what I wanted to do (since the FTP server ignored symlinks...).

---

### Post by mc4man on 2008-12-05
Well you could actually do it fairly quickly in nautilus either with a nautilus action ' open dir as root' or I guess gksu nautilus. (not as quick as the ln command

As root you create a symlink, copy and paste to your desktop, then shift/delete the original symlink.
The one on the desktop will have a locked icon, to remove it move the link to trash, then move back.
 
I'm surprised you could even attempt to create a symlink from /, in 8.04 it's not available to a user, grayed out. (maybe a small oversight in 8.10

---

### Post by p_quarles on 2008-12-05
> **mc4man said:**
> Well you could actually do it fairly quickly in nautilus either with a nautilus action ' open dir as root' or I guess gksu nautilus. (not as quick as the ln command

As root you create a symlink, copy and paste to your desktop, then shift/delete the original symlink.
The one on the desktop will have a locked icon, to remove it move the link to trash, then move back.
 
I'm surprised you could even attempt to create a symlink from /, in 8.04 it's not available to a user, grayed out. (maybe a small oversight in 8.10
The issue is that the user has access to the target (a mounted volume owned by the user), but not to the directory in which the target is listed. So, he can create a user-owned symlink, but can't create it in /media.

---

