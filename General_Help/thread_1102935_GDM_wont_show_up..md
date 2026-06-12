---
title: "GDM wont show up."
date: 2009-03-22
forum: General Help
---

### Post by realizee on 2009-03-22
Hi, I just installed a new theme for my GDM, and now the GDM wont start. Any suggestions to conquer this problem?

---

### Post by mhgsys on 2009-03-22
> **realizee said:**
> Hi, I just installed a new theme for my GDM, and now the GDM wont start. Any suggestions to conquer this problem?

fist, make a backup of your xorg.conf so you can easily edit settings later.

```

sudo nano /etc/X11/xorg.conf

```

and save it like xorgbackup.conf or something like that.

then reset X 

```

 sudo dpkg-reconfigure -phigh xserver-xorg

```

reboot gdm.

```

sudo /etc/init.d/gdm restart.

```

if your videocard is not automatically detected you can use your xorgbackup.conf to see what settings you used to use.
and change /etc/X11/xorg.conf.

---

