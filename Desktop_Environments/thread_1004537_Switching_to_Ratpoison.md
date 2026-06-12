---
title: "Switching to Ratpoison"
date: 2008-12-07
forum: Desktop Environments
---

### Post by misterjamin on 2008-12-07
Hi all,

Long-time RedHat/Fedora/CentOS user here, just switched to MythBuntu 8.10 from MythDora 5 for my main mediacentre.

I used (and loved) Ratpoison on MythDora, and I'm hoping to use it on MythBuntu too, but I'm struggling to figure out how? I have the package installed, but that's as far as I've got, as it doesn't show up in the GDM sessions list either.

Thanks in advance

MrJ

---

### Post by hictio on 2008-12-07
How did you installed? Perhaps it is on a directory not on your $PATH?
You can test is a second by stopping the gdm service, and starting it by hand (I mean ratpoison)?

To stop the GUI, tyoe this:
```

sudo /etc/init.d/gdm stop

```

Or, perhaps, with gmd still stopped, creating an ~/.xinitrc file, an adding raptoison to it?
[Switching Between Window Managers and Desktop Environments](http://www.rapierbit.org/linux/winmgrs.html)

Long time Ratpoison user way back on RH 9 :)

---

