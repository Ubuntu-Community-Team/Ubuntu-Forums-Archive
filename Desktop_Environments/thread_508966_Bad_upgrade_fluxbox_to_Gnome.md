---
title: "Bad upgrade: fluxbox to Gnome"
date: 2007-07-24
forum: Desktop Environments
---

### Post by reedk on 2007-07-24
I performed a fairly plain Edgy install and decided to use fluxbox
> sudo aptitude install fluxbox and life was good. Then I decided to go with the base Ubuntu Gnome desktop
>  sudo aptitude install ubuntu-desktopand removed fluxbox. Now, I don't get a Gnome/Ubuntu desktop, but what looks like a plain X desktop.

How do I set Gnome as the default display manager or at least set it for the one user I use on a daily basis?

---

### Post by kevinlyfellow on 2007-07-24
Does GDM startup?  Install sysv-rc-conf and see if gdm is set to startup.

---

### Post by RedSquirrel on 2007-07-25
> **reedk said:**
> I performed a fairly plain Edgy install and decided to use fluxbox
 and life was good. Then I decided to go with the base Ubuntu Gnome desktop
and removed fluxbox. Now, I don't get a Gnome/Ubuntu desktop, but what looks like a plain X desktop.

How do I set Gnome as the default display manager or at least set it for the one user I use on a daily basis?

Did you install gdm as well? That would take care of everything.

If you want to use startx, then in your ~/.xinitrc you need this line to run GNOME:

```
exec gnome-session
```in place of 'exec startfluxbox'.

---

