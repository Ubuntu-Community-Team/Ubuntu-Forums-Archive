---
title: "when i start the pc i get a terminal screen"
date: 2006-08-17
forum: Desktop Environments
---

### Post by spottyrover on 2006-08-17
I i installed drapper about a week ago now when i turn on the pc
it goes straight to a terminal where i have root privalidge when i type startx i get the error of not having permission for X server. I get this as a root user or as a login user enviroment

any ideas would be appreciated

thanks dave

---

### Post by murataht on 2006-08-17
can't you choose which kernel you gonna boot from grub menu, like normal kernel or a recovery mode, etc??? i think you are in the recovery mode, just a wild guess.

---

### Post by spottyrover on 2006-08-18
I get past grub ok 
the pc boots up as usuall
the problem is at the point where it goes to the gui to choose which user, it logs back in to the terminal  
If I knew where to look I am sure the problem can be fixed
When I try to use either startx or telinit 5 to start gnome.
 the reported problem ( If I remember corectly )is that the users do not have permission to use the x server in gui mode.

thanks for your replys

---

### Post by murataht on 2006-08-18
you are welcome. 

this means, it is a permission problem. maybe check the gdm permission.

```
ls -l /usr/sbin/gdm
```

if it shows ```
-rwxr-xr-x
```, problem is somewhere else. if it does not, changing it may solve the problem. 

good luck.

---

### Post by spottyrover on 2006-08-19
I got these results checking from a different installed version (i want this one since i got mythtv working a week before it stopped)

ls -l /media/hdb5/usr/sbin/gdm
-rwxr-xr-x 1 root root 249616 Aug  2 14:05 /media/hdb5/usr/sbin/gdm


any other ideas?

thanks
dave

---

### Post by jackn on 2006-08-19
You might be in single-user mode (root, console).
The following files may have been changed, or they might provide useful info:

[LIST]
/etc/inittab
[/LIST]

  [LIST]
~/X11/xinit/xinitrc and   /etc/X11/xinit/xinitrc
[/LIST]

Finally, is there a dedicated mythtv forum or mailing list? Might the installation of mythtv and the loss of the GUI be related? It just might be a well-known issue to mythtv users.

Jackn

---

### Post by spottyrover on 2006-08-19
thanks for your help
I started ubuntu this morning and now it works ok i did not change anything
so I am more confused than ever now

again thanks for your help
dave

---

