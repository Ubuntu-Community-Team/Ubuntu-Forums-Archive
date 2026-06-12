---
title: "Ubuntu/debian daemon startup script?"
date: 2009-06-14
forum: General Help
---

### Post by dragos240 on 2009-06-14
I like arch's rc.conf it has everything in one file, where is ubuntu's startup daemon script?? Because I disabled gdm on startup, and I want gdm to startup again, because sudo gdm is annoying.

---

### Post by unutbu on 2009-06-14
The command ```
update-rc.d gdm defaults 30
```

creates the following symlinks:
```

   /etc/rc0.d/K30gdm -> ../init.d/gdm
   /etc/rc1.d/K30gdm -> ../init.d/gdm
   /etc/rc6.d/K30gdm -> ../init.d/gdm
   /etc/rc2.d/S30gdm -> ../init.d/gdm
   /etc/rc3.d/S30gdm -> ../init.d/gdm
   /etc/rc4.d/S30gdm -> ../init.d/gdm
   /etc/rc5.d/S30gdm -> ../init.d/gdm
```

When Ubuntu starts up, all the scripts in /etc/rcS.d are executed, followed by all the scripts in /etc/rc2.d. The above command puts a symlink in /etc/rc2.d (/etc/rc2.d/S30gdm) and thus causes gdm to run at boot. (Ubuntu boot runlevel 2 by default. "runlevel 2" means scripts in /etc/rc2.d are executed.)

If you'd like a semi-graphical (curses-based) program to control which start-up scripts are run at boot,
install the **sysv-rc-conf** package and run 
```

sudo sysv-rc-conf
```

For more information see
See [http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit), and
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

