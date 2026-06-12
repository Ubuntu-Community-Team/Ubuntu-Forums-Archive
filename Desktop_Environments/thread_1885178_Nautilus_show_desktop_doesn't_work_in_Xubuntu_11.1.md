---
title: "Nautilus show_desktop doesn't work in Xubuntu 11.10 :("
date: 2011-11-22
forum: Desktop Environments
---

### Post by mahy on 2011-11-22
Hi y'all,

im running Xubuntu 11.10 and would like to use Nautilus as the default file manager. In previous version it was necessary to prevent it from managing the desktop by unticking /apps/nautilus/preferences/show_desktop in gconf-editor. Sadly, this no longer works in 11.10. Nautilus still stubbornly wants to manage my desktop. Is there any better approach? Many thanks for your help.

---

### Post by Sonador on 2011-11-22
Hi mahy,

this thread is similar, it should help you: [http://ubuntuforums.org/showthread.php?t=1871789](http://ubuntuforums.org/showthread.php?t=1871789)

---

### Post by mahy on 2011-11-23
> **Sonador said:**
> Hi mahy,

this thread is similar, it should help you: [http://ubuntuforums.org/showthread.php?t=1871789](http://ubuntuforums.org/showthread.php?t=1871789)

Hi Sonador,

thanks for the suggestion, but I found nothing in dconf-editor to disable managing desktop by Nautilus... :-/

---

### Post by Sonador on 2011-11-24
I'm not sure, what is your goal. Probably you want to use **xfdesktop** (xubuntu default) as desktop manager, and nautilus instead of thunar. In this case, you should run **nautilus --no-desktop**, so nautilus will not take power over the desktop.

Or you are looking for unticking **show-desktop-icons** in the dconf-editor org>gnome>desktop>background. This option stops nautilus drawing desktop background and showing icons, and I suppose that mean nautilus is not managing desktop.

Or are you looking for other solution?

Have a nice day, S.

---

### Post by LewisTM on 2011-11-25
What about also unticking /desktop/gnome/background/draw_background  in gconf-editor?

---

