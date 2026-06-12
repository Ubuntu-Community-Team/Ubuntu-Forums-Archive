---
title: "no valid session found after installing edubuntu-desktop"
date: 2011-07-04
forum: Desktop Environments
---

### Post by wlee on 2011-07-04
I've had two workstations for over two years now running ubuntu and going through the progression of upgrades. These workstations are for my kids to use so I decided I wanted to install edubuntu-desktop. Before taking the leap, I cloned a VBox natty VM from my PC and installed edubuntu-desktop and all related packages. Everything went fine so I felt confident enough to go ahead and install the packages on my kids' workstations.

On the very first attempt everything installed without error, but on reboot, I was able to get the new splash screen and login screen, but on my attempt to login, I get a message box that says 'no valid session found'. I click the OK button and the message box goes away, but the PC doesn't do anything. I'm left with nothing but the wallpaper and no allowable interaction. I'm able to go to tty1 and when I checked the .xsession-errors file I see the following...

> MainThread 2011/07/01 08:52:49.0993 (sabayon-apply): No profile for user 'thekids' found
No profile for user 'thekids' found
MainThread 2011/07/01 08:52:49.0994 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/07/01 08:52:49.0996 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2011/07/01 08:52:49.0993 (sabayon-apply): No profile for user 'thekids' found
MainThread 2011/07/01 08:52:49.0994 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/07/01 08:52:49.0996 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2011/07/01 08:52:49.0993 (sabayon-apply): No profile for user 'thekids' found
MainThread 2011/07/01 08:52:49.0994 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/07/01 08:52:49.0996 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~//etc/sabayon/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
No default user directories
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1738]: Gtk-CRITICAL: IA__gtk_main_quit: assertion `main_loops != NULL' failed

I've tried uninstalling/reinstalling ubuntu-desktop, edubuntu-desktop, gdm, gnome, gnome-sessions, even sabayon, but nothing. I'm essentially left with a fully functioning system with the exception of the GUI. This happens irregardless of user or desktop environment chosen.

My next option is to rebuild this workstation and I'll probably have to install from scratch for the other workstation. I would prefer not doing this so any help would be great.

---

