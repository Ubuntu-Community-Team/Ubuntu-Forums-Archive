---
title: "Updating choosewm menu"
date: 2011-05-16
forum: Desktop Environments
---

### Post by Duke_N on 2011-05-16
Hi ...

I'm running Xubuntu 10.10. When I login, I usually choose to run a "blackbox" seesion.

I've just installed a window manager that I'd like to try out.  How do I update the list of available WMs at login, or when I run "choosewm"? TIA ...

--
Duke

---

### Post by hhh on 2011-05-16
What window manager did you install and how did you install it? Usually GDM will automatically insert a session entry. If it doesn't, just create a new .desktop file in /usr/share/xsessions (warning, you won't see the .desktop extension unless you do File>Save As... DON'T overwrite your existing Xfce Session/xfce.desktop file!!!)

[http://ubuntuforums.org/showthread.php?t=2920](http://ubuntuforums.org/showthread.php?t=2920)
[https://wiki.archlinux.org/index.php/GNOME_Tips#Add.2FEdit_GDM_Sessions](https://wiki.archlinux.org/index.php/GNOME_Tips#Add.2FEdit_GDM_Sessions)

---

### Post by Duke_N on 2011-05-16
> **hhh said:**
> What window manager did you install and how did you install it?

amiwm - it's an Amiga OS look-alike. I compiled it from source. It installs into /usr/local/bin/..

>  Usually GDM will automatically insert a session entry. If it doesn't, just create a new .desktop file in /usr/share/xsessions (warning, you won't see the .desktop extension unless you do File>Save As... DON'T overwrite your existing Xfce Session/xfce.desktop file!!!)I simply "cp"ed an existing blah.desktop to amiwm.desktop :) Then hacked it.

[> http://ubuntuforums.org/showthread.php?t=2920]("http://ubuntuforums.org/showthread.php?t=2920")> 
[https://wiki.archlinux.org/index.php/GNOME_Tips#Add.2FEdit_GDM_Sessions](https://wiki.archlinux.org/index.php/GNOME_Tips#Add.2FEdit_GDM_Sessions)Thanks for the links and the above info. I'll go and logout and see what happens!
--
Duke

---

### Post by Duke_N on 2011-05-16
@hhh

Got everything working! Much obliged! Don't rightly know if I _like_ this WM **- yet** - but that's beside the point. At least I know how to install a new WM and have GDM see it. Thanks again. Now I have to go look for a "blackbox" forum or ML.

--
Duke

---

