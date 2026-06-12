---
title: "[SOLVED] Help w/fluxbox"
date: 2007-11-14
forum: Desktop Environments
---

### Post by voteforpedro36 on 2007-11-14
Question: How can I get fluxbox to display things like my battery and update notification and volume? I know to add them to the file (~/.fluxbox/startup), because I already added nm-applet. So how do I start these in fluxbox?

---

### Post by RedSquirrel on 2007-11-14
If you have update-notifier installed, you can add it to your startup file.

```
update-notifier &
```

I'm not sure about the other two (volume and battery). I've never used them.

---

### Post by cknight on 2007-11-15
Remaining battery life and volume information can be 'shown' on-screen via a utility called 'osdsh' and controlled by its companion 'osdctl'.  I think these are installed by default, but if not its in the repositories.  Within the next week I'll be posting a how-to for fluxbox keys.  Part of this how-to will cover the use of osdsh and how it can be used to display volume changes on the screen.  Stay tuned...

---

### Post by spupy on 2007-11-15
For the battery I used gnome-power-manager. It stays in the system tray.
Now i use conky and a custom battery monitoring script (to notify me when the battery is low).

---

### Post by jviscosi on 2007-11-15
For volume, you could run one of the system tray volume applets from the desktops, like kmix.  If there's a battery-notification applet (I don't use one) you could run that as well.  If you want to go the dockapp route, I use wmix for volume control.  There are simpler ones that just do volume, like volume.app, and then there are a ton of dockapps that monitor battery life.  I normally get them from [www.dockapps.org]("http://www.dockapps.org/") but it looks like that site is hosed at the moment.  (There are also plenty of dockapps in the repositories.)  You would put any of these into your startup file as others have indicated.

There are also various [desklets]("http://www.gdesklets.de/") that do monitoring and volume control.

---

### Post by voteforpedro36 on 2007-11-15
Thanks guys. I don't like the on-screen thing really, if you mean like what DSL does. Apparently update-notifier also opened the battery applet, because one came up one the other one did. Does anyone know the command for the defualt GNOME volume applet?

And also the buttons on the side if my laptop don't control it anymore (maybe they never did in flubox...), and I currently have no way to turn down the volume (maybe somehow CLI, a command for alsa maybe?).

Thanks for the help. (32 updates since I logged into GNOME btw)

---

### Post by Linicks on 2007-11-15
> **voteforpedro36 said:**
> And also the buttons on the side if my laptop don't control it anymore (maybe they never did in flubox...), and I currently have no way to turn down the volume (maybe somehow CLI, a command for alsa maybe?).


Did they work in Gnome?  If so, what I do using Fluxbox is run (as already said) gnome-power-manager (this also sorts out the suspend, battery applet, and shortcut keys on the laptop for suspending etc. exactly as in Gnome, and for the other keys (sound control, eject etc.) gnome-settings-daemon.

In .fluxbox/startup:

```
gnome-power-manager 
gnome-settings-daemon &
```

Nick

---

### Post by RedSquirrel on 2007-11-16
> **voteforpedro36 said:**
>  And also the buttons on the side if my laptop don't control it anymore (maybe they never did in flubox...), and I currently have no way to turn down the volume (maybe somehow CLI, a command for alsa maybe?).

This is what I use to control the volume:

```
XF86AudioMute :Exec amixer set PCM toggle > /dev/null
XF86AudioLowerVolume :Exec amixer set PCM 1%- > /dev/null 
XF86AudioRaiseVolume :Exec amixer set PCM 1%+ > /dev/null 

```

**man amixer**

---

### Post by voteforpedro36 on 2007-11-16
Ok, I think I got everything sorted. Turns out gnome-power-manager and gnome-settings-daemon got the volume button working. Thanks for all the help!

---

### Post by Linicks on 2007-11-17
I also run:

/usr/bin/nm-applet &

in the startup file - this then gives you the network applet on the taskbar - very handy.

Nick

---

