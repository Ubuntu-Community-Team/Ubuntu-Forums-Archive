---
title: "[SOLVED] Kubuntu Gutsy: impossible to modify login manager"
date: 2007-11-25
forum: Desktop Environments
---

### Post by o_caudron on 2007-11-25
Hi,

My kubuntu login screen shows only one user in the list, and it's one I don't use. I can't find how to change this. Whatever I do, the login screen stubbornly refuses to change (is the default kubuntu login screen and decides for itself which users to show). I have first tried to change it from system settings->login manager, no change. I have tried installing the kdm theme manager and change the theme, no change. I have tried everything I could find on google and forums (changes in 20_kubuntu_default_settings, in /etc/kde3/kdm/kdmrc, etc.), no change. Everywhere I look the settings are consistent but the login screen doesn't use them. Complete mystery.

I have suspected that the login manager may be gdm instead of kdm, but as far as I can tell the system uses the kdm login mgr. 

I'd like to change the look of the login screen (preferably by setting the style myself rather than using a theme), but I'd settle for having at least the list of users right.

This is Kubuntu Gutsy Gibbon. Help please!

Regards,

Olivier Caudron.

---

### Post by samwyse on 2007-11-25
I got the default KDM theme from System Settings after a reboot. I did edit all the different things, but it didn't change anything until a reboot. I'm not sure how I did it. Currently all the kdm files I edited are the defaults as far as I can tell, because I changed everything back after I noticed nothing changed (until the reboot).

---

### Post by o_caudron on 2007-11-25
Figures.

I have rebooted several time since I started on this, to no avail. Now I post this request, I reboot, and it works. Grrr. :confused:

Well, that's good news anyway, although I have no idea what made this work in the end...

Olivier.

---

