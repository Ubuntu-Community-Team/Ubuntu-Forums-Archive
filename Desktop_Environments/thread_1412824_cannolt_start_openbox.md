---
title: "cannolt start openbox"
date: 2010-02-21
forum: Desktop Environments
---

### Post by Post Monkeh on 2010-02-21
please see [this]("http://ubuntuforums.org/showthread.php?t=1412420") thread.

i was having a few issues with different services and whatnot starting when running different desktop environments, but i got that sorted. 

now i'm still having a more specific problem with getting openbox running.
i can start an openbox session by making a new user and logging in, but that isn't really ideal.

i can do an "openbox --replace" in gnome and openbox works. i can login to an xterm session and do an "openbox-session" it works.

when i try to log in from the gdm, it just kicks me back out into the login screen again.

my xsession-errors file looks like this

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(openbox:4372): Openbox-WARNING **: Openbox is configured for 4 desktops, but the current session has 1.  Overriding the Openbox configuration.
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"

(gnome-settings-daemon:4426): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
gnome-settings-daemon: Fatal IO error 2 (No such file or directory) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1488 requests (1488 known processed) with 0 events remaining.
```


i've downloaded fluxbox, and it runs with no problems, so i guess the problem is specific to openbox.

---

### Post by urukrama on 2010-02-22
The first error (openbox:4372) is nothing serious. It just means that Openbox wants to use 4 desktops, but gnome-settings-daemon overrides this and so now you only use one.

It seems gnome-settings-daemon messes up the rest though. You most likely have some settings configured with that in Gnome that conflict with Openbox (since it works fine with a new user that does not changed the settings with gnome-settings-daemon yet).

Can you try and launch Openbox without loading that? By default, Openbox checks if you have gnome-settings-daemon installed and if you do, it launches that. This is easily disabled though.

Create a new autostart.sh file at ~/.config/openbox/autostart.sh (or copy the default one at /etc/xdg/openbox/autostart.sh there and delete the section that deals with gnome-settings-daemon). To give you some ideas of what to put in that file, have a look at the Openbox guide I wrote (linked to in my signature); it has a section on autostarting applications.

Unless you have some complex Gnome settings you would also like to use in Openbox, you can easily do without gnome-settings-daemon. Your GTK themes and icons, wallpapers, fonts, mouse cursors, etc. are all easily configured in Openbox without it. Again, my Openbox guide has a section on those things.

---

### Post by Post Monkeh on 2010-02-22
> **urukrama said:**
> The first error (openbox:4372) is nothing serious. It just means that Openbox wants to use 4 desktops, but gnome-settings-daemon overrides this and so now you only use one.

It seems gnome-settings-daemon messes up the rest though. You most likely have some settings configured with that in Gnome that conflict with Openbox (since it works fine with a new user that does not changed the settings with gnome-settings-daemon yet).

Can you try and launch Openbox without loading that? By default, Openbox checks if you have gnome-settings-daemon installed and if you do, it launches that. This is easily disabled though.

Create a new autostart.sh file at ~/.config/openbox/autostart.sh (or copy the default one at /etc/xdg/openbox/autostart.sh there and delete the section that deals with gnome-settings-daemon). To give you some ideas of what to put in that file, have a look at the Openbox guide I wrote (linked to in my signature); it has a section on autostarting applications.

Unless you have some complex Gnome settings you would also like to use in Openbox, you can easily do without gnome-settings-daemon. Your GTK themes and icons, wallpapers, fonts, mouse cursors, etc. are all easily configured in Openbox without it. Again, my Openbox guide has a section on those things.

consider yourself added to my christmas card list. good man.

---

### Post by urukrama on 2010-02-22
I'm glad the problem is solved. :)

---

