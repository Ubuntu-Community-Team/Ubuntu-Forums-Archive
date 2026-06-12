---
title: "Mac menu effect under gnome on edgy"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by FMara on 2007-03-29
Hello - I'm hoping that somebody can help me avoid a reinstall.  I experimented with changing my Ubuntu 6.10 system from gnome to KDE.  I set the KDE display options to use mac-like menu bars.  I decided that I preferred gnome and performed a complete uninstall of KDE and its dependencies.  This wiped out several KDE applications that I've installed.

I do rely on a single KDE application, Digikam.  I reinstalled Digikam and all of its associated add-ins.  DigiKam uses the mac-style menu bars, even though I deleted everything except the minimum KDE files required to run apps under gnome.  I'm sure there is a configuration file somewhere that controls this behavior.  How can I restore the standard gnome menu bar behavior?  I'd like to do it without having to reinstall the KDE desktop.  Thanks.....

---

### Post by nanotube on 2007-03-29
my guess is that some config files in your .kde directory remained after you uninstalled kde, so the config for the menu style is hiding in there somewhere. since i don't run kde, i can't really pinpoint it for you, but just look around under .kde in your home dir, and check anything that looks like a config file. :) a google search might help you narrow it down, too.

---

### Post by FMara on 2007-03-29
Thanks for the recommendations.  I tried two more steps.  I deleted all of the folders associated with gnome configuration and rebooted.  This restored all of the gnome defaults.  I also renamed   /etc/kde3 and /etc/kubuntu-default-settings, rebooted, and started DigiKam.  I still get the mac-style application menu bar at the top of the screen.

I also tried renaming /etc/gtk-2.0 and restarting the application.  I still get the mac-style menu bar.

---

### Post by nanotube on 2007-03-29
i meant the ".kde" directory, that should be in your home dir. notice the initial "." in the directory name. when you change preferences in kde as a user, stuff doesn't get written to /etc or anywhere else outside of the home dir. so look there (or rename it to something else, just so you have a backup, instead of deleting).

oh, and by the way, directories starting with "." are "hidden", so to view them in nautilus, View > Show hidden files.

---

### Post by FMara on 2007-03-29
@Nanotube.....Thanks!  Problem solved.  Appreciate the coaching.

---

### Post by nanotube on 2007-03-29
great! glad i could help. :)

---

