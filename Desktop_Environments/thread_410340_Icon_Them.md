---
title: "Icon Them"
date: 2007-04-15
forum: Desktop Environments
---

### Post by robertsaron on 2007-04-15
So I went to KDE-look.org and downloaded some custom icon themes. It has been installed. I do not like it and have removed it from my list of Icon themes. I have even tried to set it to a different icon theme. When applying a different Icon them it does not work. 

I go into terminal and do sudo systemsettings  to make sure I am in admin mode. I then have rebooted several time, and still same Icon theme. I cannot get it off my system.

Is there anything else that I can do?:confused:

---

### Post by ComplexNumber on 2007-04-15
> **robertsaron said:**
> So I went to KDE-look.org and downloaded some custom icon themes. It has been installed. I do not like it and have removed it from my list of Icon themes. I have even tried to set it to a different icon theme. When applying a different Icon them it does not work. 

I go into terminal and do sudo systemsettings  to make sure I am in admin mode. I then have rebooted several time, and still same Icon theme. I cannot get it off my system.

Is there anything else that I can do?:confused:
wouldn't using the admin settings merely change the icons that the root user uses (ie when you need to enter  your password to use such applications)?

if you installed it via the kde control centre, your icon theme will be found in ~/.kde/share/icons.

what theme is it that cannot be unselected?

---

### Post by robertsaron on 2007-04-16
Thanks for the help, I fixed by going into the apps folder and running the icon theme from there. for some reason when I run sudo systemsettings it will not change my splash screen or icon them. I guess the link got broken some how. 

Its fine for now. Just kind of a pain if/when I want to change things.

---

### Post by ComplexNumber on 2007-04-16
> **robertsaron said:**
> Thanks for the help, I fixed by going into the apps folder and running the icon theme from there. for some reason when I run sudo systemsettings it will not change my splash screen or icon them. I guess the link got broken some how. 

Its fine for now. Just kind of a pain if/when I want to change things.
changing your login screen requires root privileges. changing your icon theme doesn't.

btw store your icon themes in /usr/share/icons. store your themes in /usr/share/themes. then root apps such as synaptic will have the same theme as all the other apps.

---

