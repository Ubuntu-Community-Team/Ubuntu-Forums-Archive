---
title: "Normal gnome session won't start [INTREPID STABLE]"
date: 2008-11-01
forum: Desktop Environments
---

### Post by mobiler on 2008-11-01
Hello,

I just upgraded from 8.04.1 to 8.10, and even though many packages produced errors during the upgrade, the installation went through and the resulting system seems to work fine (and also there are no updates available) except from one serious thing: As soon as I login, a message box appears saying that that the session lasted less than 10 seconds. When I click OK, it goes back to the login screen. I am only able to login in failsafe gnome.

The ~/.session-errors file is as follows:

```

/etc/gdm/Xsession: Beginning session setup...
No profile for user 'nikos' found
===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2008/11/02 01:19:34.3127 (sabayon-apply): No profile for user 'nikos' found
MainThread 2008/11/02 01:19:34.3130 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/11/02 01:19:34.3135 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 107, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2008/11/02 01:19:34.3127 (sabayon-apply): No profile for user 'nikos' found
MainThread 2008/11/02 01:19:34.3130 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/11/02 01:19:34.3135 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 107, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Couldn't exec /usr/bin/pulse-session: No such file or directory

```

Any ideas?

---

### Post by turtleclock on 2008-11-04
I experienced the same problem. I ran the following:

sudo apt-get purge pulseaudio 

This fixed it for me. It removes the file /etc/X11/Xsession.d/70pulseaudio thus allowing X to start.

---

### Post by edyeeh on 2008-11-09
> **turtleclock said:**
> I experienced the same problem. I ran the following:

sudo apt-get purge pulseaudio 

This fixed it for me. It removes the file /etc/X11/Xsession.d/70pulseaudio thus allowing X to start.

I am experiencing the same problem

I'm sorry I'm a noob at this, but how do I enter that command at startup if X can't start in the first place? is there something have to press? or mode I have to choose? I set the GRUB menu at auto and can't call up the recovery mode menu. I'm in a lot of trouble :D

---

### Post by fotherington on 2008-11-10
Have a look at [this answer]("http://www.linuxquestions.org/questions/linux-newbie-8/setting-grub-default-timeout-duration-434882/"). Basically, from the login screen you want to start a Gnome default or terminal session by clicking on the gears icon in the bottom left of the screen and selecting the appropriate option, then once logged in open /boot/grub/menu.lst and edit the timeout value so it's something more than 0. If your configuration is like mine, it's right at the top of the file and easy to see.

---

