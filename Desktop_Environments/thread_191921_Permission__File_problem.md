---
title: "Permission / File problem"
date: 2006-06-08
forum: Desktop Environments
---

### Post by G-nat on 2006-06-08
Either screwing with permissions or installing ssh something's gone badly awry.  My GDM is not happy.  In any case, I keep getting the error:

/var/run/sudo writable by non-owner (040777), should be mode 0700

The result is that I don't have to use sudo when I probably ought to -- and it won't let me when I do need to.  I can't change the permissions on var/run. 
Or run a repair.  (Or perhaps I don't know how to repair it??)  Any suggestions?

---

### Post by murataht on 2006-06-08
it seems your sudo is not working, and you don't have root password to repair it. if you want to change the permission of the "/var/run/sudo" maybe you can use the live cd to fix it. or maybe boot up into "recovery mode" will help that too, cause you have root permission in "recovery mode", i think. (please correct me if i am wrong). for the recovery mode you can enter from the grub menu.

---

### Post by Ramses de Norre on 2006-06-08
Can you press ctrl-alt-F1 and log in there? If so do ```
sudo chown /var/run/sudo root && sudo chmod 700 /var/run/sudo
```
If that doesn't work out: reboot and choose recovery mode in grub menu. In there do ```
chown /var/run/sudo root && chmod 700 /var/run/sudo
```

---

