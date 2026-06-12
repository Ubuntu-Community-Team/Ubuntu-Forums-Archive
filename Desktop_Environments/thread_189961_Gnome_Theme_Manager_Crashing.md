---
title: "Gnome Theme Manager Crashing"
date: 2006-06-05
forum: Desktop Environments
---

### Post by boichukj on 2006-06-05
The Gnome theme manager keeps crashing when i select a theme from the list.  Is there anyway to correct this?

Thanks for the help

---

### Post by codypumper on 2006-06-05
How much RAM do you have?

---

### Post by boichukj on 2006-06-05
I have 1 gig of ram.  It never happened with the old version of Ubuntu just the 6.06

---

### Post by codypumper on 2006-06-05
Considering you have more RAM than I that couldn't be the problem...
Run it as root
code:
sudo gnome-theme-manager

Tell me if you get any errors.

---

### Post by garenasix on 2006-06-05
[QUOTE=codypumper]Considering you have more RAM than I that couldn't be the problem...
Run it as root
code:
sudo gnome-theme-manager

Tell me if you get any errors.[/QUOTE]

i seem to be having problem with splash screen manager it will start to load then die

i found your post and figured id try what you suggested even tho it was for gnome-theme-manager  thinking that the splash screen manager would be some part of the gnome theme manager

and i got this



------------------------------------------

root@garenasix:/home/garenasix# sudo gnome-theme-manager

(gnome-theme-manager:6888): GnomeUI-WARNING **: While connecting to session mana ger:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

(gnome-theme-manager:6889): Gtk-WARNING **: Theme directory  of theme ICON-Cryst al-SVG-1.1.0 has no size field


(gnome-theme-manager:6889): Gtk-CRITICAL **: gtk_icon_info_get_filename: asserti on `icon_info != NULL' failed

(gnome-theme-manager:6889): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon _info != NULL' failed

-------------------------------------------------

i also got a popup

the popup
-----------------------------------------------------------------------------------
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
---------------------------------------------------------------------------------------

and my theme manager seems to work also,, just cant get the splash screen manager to load

i do have KDE on this also it was installed when it was 5.10 and i did the upgrade to 6.06 through update manager doing a gksudo update-manager then clickin the upgrade button in the update manager

other then that everything else seems to be working Gr8

---

### Post by dmorel on 2006-06-05
Are you running XGL/Compiz?
If so, do you have miniwin or Doc enabled?

---

### Post by codypumper on 2006-06-05
What icon pack are using? Try switching to a different one and see if the problem persists. If it does run:
sudo gnome-theme-manager
Then post your errors again please (while using a different icon pack).

---

### Post by boichukj on 2006-06-06
Ok i ran it with sudo gnome-theme-manager and i got this error:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

When i use the icon in the system menu (without the sudo) it will load up but when i select a theme it will crash.  

I do have xgl installed

---

### Post by miguelastico on 2006-06-06
i have this problem too
on this forum i have found that it seems to be related to XGL
anyone solved?

---

### Post by Melvil on 2006-06-06
This was a compiz bug for a long time. I'm not sure whether it's been fixed already

---

### Post by KucingKelabu on 2007-10-25
Hmm odd. I had this problem last night. I removed emerald and relog and its back to normal.

---

### Post by curtiswtaylorjr on 2007-11-13
I uninstalled/removed Emerald and all is well again.

---

