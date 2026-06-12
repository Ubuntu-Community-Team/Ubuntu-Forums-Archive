---
title: "Pressing 'D' key minimizes to desktop over xrdp in ubuntu 12.1"
date: 2013-03-04
forum: Desktop Environments
---

### Post by sudoNebula on 2013-03-04
I've read numerous threads about this same issue with earlier versions of Ubuntu but unfortunately the solution presented in every thread I've read hasn't worked.  Most of these threads point to the "Hide all normal windows and set focus to the desktop" keyboard shortcut as the culprit.  When I set my corresponding "Hide all normal windows" keyboard shortcut to 'disabled' nothing changes.  Per another thread ([http://ubuntuforums.org/showthread.php?t=1595871](http://ubuntuforums.org/showthread.php?t=1595871)) I also tried to find some shortcuts via gconf-editor but the /apps/metacity directory does not contain a 'global_keybindings' entry, nor does my '[LEFT][COLOR=#000000]/var/lib/gconf/debian.defaults/%gconf-tree.xml[/COLOR][/LEFT]
' file contain a 'show_desktop' entry.  If anyone know the cause of this issue or has any suggestions on where to find other keyboard shortcuts setting locations related Ubuntu 12.1 or xrdp I'd greatly appreciate it.

---

### Post by sudoNebula on 2013-03-05
Ok I solved my problem.  Rather than looking it gconf as many answers for older versions of ubuntu have suggested, the solution was to use dconf instead.  The keyboard shortcuts in question were stored in [COLOR=#333333][FONT=Ubuntu Beta]org.gnome.settings-daemon.plugins.media-keys

[/FONT][/COLOR]See this thread for more details[FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]:  [/COLOR][/FONT][http://askubuntu.com/questions/26056/where-are-gnome-keyboard-shortcuts-stored/217310#217310](http://askubuntu.com/questions/26056/where-are-gnome-keyboard-shortcuts-stored/217310#217310)

---

### Post by LinuxTomB on 2013-05-08
Same problem, more information and fixes for 13.04. My situation is using Ubuntu as VM and then using XRDP to connect. Had to use gnome-fallback. 

There is a new / different place in dconf where it holds the dreaded "show_desktop" parameter. Here is how to fix it for all users:
1. Create a file as root called  *[FONT=courier new] /etc/dconf/db/gdm.d/fixshow_desktop.d [/FONT]*  with the following in it:    [FONT=courier new]
[org/gnome/desktop/wm/keybindings]
show_desktop=''[/FONT]    

2. Run **[FONT=courier new]sudo dconf update **[/FONT] so that **dconf ** can read the changes. Users will have to logout / login to see the change.


This should fix the problem. This is the same as every user going into ***System Setting | Keyboard |Shortcuts*** or ***dconf editor ***and going down the   *org->gnome->desktop->wm->keybindings *  tree.

---

### Post by Weaseal on 2013-10-16
THANK YOU!! This was driving me insane, apparently this is an old bug that had a workaround for a long time that no longer works.  THESE solutions actually do work in Ubuntu 13.04.

I'm not sure which one solved it as I tried both, maybe both are necessary.  REBOOT was required; dconf update and logout-login DID NOT do the trick.

> **LinuxTomB said:**
> There is a new / different place in dconf where it holds the dreaded "show_desktop" parameter. Here is how to fix it for all users:
1. Create a file as root called  *[FONT=courier new] /etc/dconf/db/gdm.d/fixshow_desktop.d [/FONT]*  with the following in it:    [FONT=courier new]
[org/gnome/desktop/wm/keybindings]
show_desktop=''[/FONT]    

2. Run **[FONT=courier new]sudo dconf update **[/FONT] so that **dconf ** can read the changes. Users will have to logout / login to see the change.

> **sudoNebula said:**
> Ok I solved my problem.  Rather than looking it gconf as many answers for older versions of ubuntu have suggested, the solution was to use dconf instead.  The keyboard shortcuts in question were stored in [COLOR=#333333][FONT=Ubuntu Beta]org.gnome.settings-daemon.plugins.media-keys[/FONT][/COLOR]

---

