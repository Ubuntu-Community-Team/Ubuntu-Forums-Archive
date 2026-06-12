---
title: "unable to start gnome-settings-daemon"
date: 2008-12-13
forum: General Help
---

### Post by Zim Zelen on 2008-12-13
Hello,

This morning my computer took much longer to boot, and i had lost the regular "human" theme, and the volume slider disappeared from it's toolbar.

When i start the System > Preferences > Appearance, i get the following message :

[I]"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."[/I]

It seems that this problem is rather common, and i've had a look around the forums and tried various workarounds from these threads 

[http://ubuntuforums.org/archive/index.php/t-579167.html](http://ubuntuforums.org/archive/index.php/t-579167.html)
[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)
[http://ubuntuforums.org/showthread.php?p=6014481](http://ubuntuforums.org/showthread.php?p=6014481)

So i've already tried the following :
- re-installing dbusX11 , and dbus
- Patching the session files in X.session.d ( as suggested in the thread) - reverted afterwards
- installing the new, improved libvisual-0.4-plugins.0.4.0.dfsg.1-2ubuntu4. (note that i didn't have a plugin at all in the first place...)
- removing actor_nastyfft.so - reverted afterwards

And nothing works. However if i run it gnome-settings-daemon in the command line, the theme comes back, but not the volume slider... and eventually the theme goes away again. I don't know what other things might not be working. Am i the only one to get this problem? 

BTW i'm running an old Dell Inspiron 1150, and it might have started to behave weirdly since the last update.

Cheers

---

### Post by Zim Zelen on 2008-12-15
Removing both /usr/lib/gstreamer-0.10/libgstlibvisual.so and /usr/lib/libvisual-0.4/actor/actor_nastyfft.so , make it get the themes at startup but it lasts under a minute.

Also i've found out additional problems :
-Power management is gone with in the top right bar. and takes ages to start.
-Add/Remove programs does not start anymore, synaptic does, and seems to work.
-Pidgin does not start
-I haven't seen a new update for a couple of days, i'm wondering if the update manager is working

Anyone?.... Help?.... Is a reinstall the next thing to do???

---

### Post by yonexFactory on 2008-12-16
I'm having basically the same problem. Sorry I can't offer you any advice, but I'm clueless!

---

### Post by rfurman24 on 2008-12-16
I have the same problem. Nothing on my system has changed. At the same time this started Firefox window border disappeared.

---

### Post by rfurman24 on 2008-12-16
How do I debug gnome-settings-daemon?

---

### Post by rfurman24 on 2008-12-16
I can run gnome-settings-daemon as root and it will use my root settings but the normal user is broke.

---

### Post by rfurman24 on 2008-12-16
My problem seemed to be related to the fact that I had changed the alt-control-delete key binding to open gnome system monitor. I have always set my system up this way. This particular system has been like that since install but all of a sudden it broke my system.

---

