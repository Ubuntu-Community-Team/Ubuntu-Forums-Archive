---
title: "System-&gt;Administration-&gt;Boot ?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by jnoreiko on 2005-12-01
[This page from the Ubuntu Guide]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521330") says this:

>  Launch System->Administration->Boot

but I don't see it in the menu. (Fresh install of 5.10)

---

### Post by Dr. Nick on 2005-12-01
I think that guide may be a bit old, Not sure.

Anyway that program was removed before 5.10 was officialy released because it had some bugs in it. 
What exactly are you trying to do? Most of what it could do can be done other ways.

here is a howto for disabling services that start on boot, not quite as pretty as the one that was removed but it can get the job done just as well , if not better [http://www.ubuntuforums.org/showthread.php?t=89491&highlight=services](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=services)

---

### Post by jnoreiko on 2005-12-01
I wanted to add a Windows entry into the GRUB menu.
... but something I've done has messed GRUB up anyway, so I'm going to reinstall it anyway.

---

### Post by Dr. Nick on 2005-12-01
Oh how bad is it messed up? Adding windows via the command line is pretty easy usually
That howto doesnt address this, I was thinking of another program :)
Anyway if you want have a look here [http://www.ubuntuforums.org/showthread.php?t=97558&highlight=windows+grub](http://www.ubuntuforums.org/showthread.php?t=97558&highlight=windows+grub)

---

### Post by jnoreiko on 2005-12-01
I was trying to put grub on the floppy as well, in case installing Windows broke things.

In terminal, I tried 'sudo grub-install /dev/fd0' and also the ("fd0") notation. Both gave different errors.
Next reboot, I just get the grub prompt.

---

### Post by Dr. Nick on 2005-12-01
ew, yeah that sounds bad, you can just use the recovery option from the install cd ,if you didnt know, to repair grub. If you have to reinstall windows and it erases grub then you can also use the install cd to repair grub to save from a full reinstall. Their are a few howtos on that aswell on these boards

---

### Post by jnoreiko on 2005-12-02
Yup, that's what I've done. All works now, thanks :)

---

