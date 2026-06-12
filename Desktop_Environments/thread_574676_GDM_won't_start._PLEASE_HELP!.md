---
title: "GDM won't start. PLEASE HELP!"
date: 2007-10-13
forum: Desktop Environments
---

### Post by eager2know on 2007-10-13
Something happend to my GDM. I was working on the my computer when first my startup icons dissappeared from the top panel. I tried to reboot X with ctrl-alt-backspace but it stuck with time spinning cursor. When I tried to reboot the login window didnt show up. When I tried to login using my usename and password it says "can't cd to /home/username". The same goes for all other accounts. I can only login in recovery mode and xstart opens windows with a bunch of error messages.

/etc/init.d/gdm restart gives * Starting GNOME Desktop Manager...[fail]

The only hope is you all good people out there. Please help.
Thanks.

---

### Post by mnml on 2007-10-13
same for me, i made some change via the gdm preference panel.

---

### Post by PmDematagoda on 2007-10-13
What did you do before this happened? Did you install or remove any applications or packages, did any system crashes occur before this, anything special?

---

### Post by Martje_001 on 2007-10-13
Remove the GDM configuration file (make sure you have a backup) and restart. GDM will automaticly make a new one AFAIK.

---

### Post by Doomguy0505 on 2007-10-25
How do you do this???!

---

