---
title: "can't silence gtk audible alerts in kde4"
date: 2009-09-09
forum: Desktop Environments
---

### Post by ireneshusband on 2009-09-09
In KDE4, whenever I use a a GTK application, such as audacious, firefox etc, it produces audible notifications when I do things like open a file dialogue. This happens irrespective of the settings chosen in Gnome (via gnome-panel).

I have another problem which may have some bearing on this. Regardless of the settings in KDE for displaying GTK widgets, GTK applications, with the exception of Thunderbird and Firefox, all appear in that really ugly blocky default appearance during each session until I open whichever Gnome tool it is for changing these settings. Firefox and Thunderbird look OK apart from messed up scroll bars, despite my having checked the box in KDE to fix this. However no fiddling with the settings gets rid of those awful audible notifications.

Does anyone know how I can kill those alerts?

Many thanks in advance.

---

### Post by krazyd on 2009-09-10
is this a native kubuntu install, or have you installed kde over ubuntu?

if the noise you are hearing is coming from your internal pc speaker, then you can disable it completely by unloading the pcspkr driver.
```
sudo modprobe -r pcspkr
```

you can also edit your /etc/modprobe.d/blacklist.conf to make this change permanent (ie. don't even load the driver module when booting). just add this line:
```
blacklist pcspkr
```

---

### Post by ireneshusband on 2009-09-10
Thanks very much for replying, I really appreciate it.

> **krazyd said:**
> is this a native kubuntu install, or have you installed kde over ubuntu?

It's KDE over Vanilla Ubuntu.


> **krazyd said:**
> if the noise you are hearing is coming from your internal pc speaker, then you can disable it completely by unloading the pcspkr driver.

The sounds are the standard Gnome alert samples (the conga roll etc) coming through the primary sound device (laptop speakers/headphone jack). I have PulseAudio running, so I assume they are routed through that.

---

### Post by Francis Upton on 2009-09-19
I started the session with Gnome and turned off all notifications with the preferences there and it fixed the Firefox notifications.

Ecllipse however is still doing annoying notifications, can't figure out what's different about that.  Maybe that it runs on Java.

---

### Post by Francis Upton on 2009-09-19
> **Francis Upton said:**
> I started the session with Gnome and turned off all notifications with the preferences there and it fixed the Firefox notifications.

Ecllipse however is still doing annoying notifications, can't figure out what's different about that.  Maybe that it runs on Java.

Um, actually not, the firefox sounds are still there, so this did not really have any effect.

I'm Ubuntu + KDE,  not kubuntu.  Does this make a difference?  And should I just switch in hopes that life for me will improve?

---

### Post by krazyd on 2009-09-19
try a kubuntu live cd and see if you have the issue..

---

### Post by VCoolio on 2009-09-19
For both the sound and ugly theme you can run 'gnome-settings-daemon' to use gnome settings (it will use your gnome theme and sound preferences). If you don't want to run an extra process:

1. for the sound issue try this: in /etc/X11/Xsession.d/ there should be something like 52-libcanberra-gtk-module_add-to-gtk-modules. (Re)move that.
2. for the themes: either install and use lxappearance if you want easy or create a file named .gtkrc-2.0 yourself (with the dot to make it hidden) in your home folder with your favourite text-editor and make it look like this:

```
gtk-theme-name="Whatevertheme"
gtk-icon-theme-name="Whatevericons"
gtk-font-name="Sans 10"
gtk-toolbar-style=2
include "$HOME/.gtkrc-2.0.mine"
```

Use the exact theme names. The 'include' part is for if you want to make specific changes in your theme; it's like changing the gtkrc inside the theme folder. Not necessary.

Edit: I [found]("https://bugs.launchpad.net/bugs/343677") that for the sound issue you can add the line 
gtk-enable-event-sounds= 0
to ~/.gtkrc-2.0 (and maybe also the line gtk-error-bell=0 ).

---

### Post by Rounin on 2010-09-19
See this thread as well:

[http://forum.kde.org/viewtopic.php?f=19&t=11847](http://forum.kde.org/viewtopic.php?f=19&t=11847)

---

