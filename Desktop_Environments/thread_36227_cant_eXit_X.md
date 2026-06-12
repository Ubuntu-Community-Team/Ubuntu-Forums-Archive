---
title: "cant eXit X"
date: 2005-05-22
forum: Desktop Environments
---

### Post by fff on 2005-05-22
I've just installed ubuntu 5.04 using default installation options but my problem is this:
I cant kill x and go to pure console without x.

I've tried init 3 and telinit 3 in a console,terminal,being root and a normal.

I've even changed the runlevel in /etc/inittab and tried modifying the kernel parameters in grub.

Please help me.

---

### Post by Sam on 2005-05-22
[QUOTE=fff]I've just installed ubuntu 5.04 using default installation options but my problem is this:
I cant kill x and go to pure console without x.

I've tried init 3 and telinit 3 in a console,terminal,being root and a normal.

I've even changed the runlevel in /etc/inittab and tried modifying the kernel parameters in grub.

Please help me.[/QUOTE]
Try```
$ sudo /etc/init.d/gdm stop
```

---

### Post by fff on 2005-05-23
[QUOTE=Sam]Try```
$ sudo /etc/init.d/gdm stop
```[/QUOTE]
 thanks

---

### Post by Pitbull11188 on 2005-05-24
Have you tried changing your session type to fail-safe terminal upon login? Or you could always try ctrl+alt+f4. Hope it helps.

---

