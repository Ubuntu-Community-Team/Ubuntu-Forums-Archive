---
title: "Native GNOME Apps (and their icons) in KDE"
date: 2007-02-19
forum: Desktop Environments
---

### Post by DizzyTech on 2007-02-19
No, this isn't the standard n00bish request.  I know that KDE apps can run in GNOME and vice-versa.  I know KDE apps look good even non-natively, and with KDE running Clearlooks on GTK apps GNOME apps look tons better.  I've even played around and got my favorite Tango icons in KDE.  Now, here's my problem:  even with my own GNOME system configured to run Tango, and KDE as well, GNOME apps still use the same old icons.

Is there any possible way to get GNOME apps (running under KDE) to detect their native icon configuration and, more specifically, run Tango?

NOTE:  I'm running Ubuntu Edgy Eft with kubuntu-desktop installed.  I use gdm, if it matters.  KDE is using the Tango icon set.  All of my GNOME apps are configured to use ClearLooks, while KDE runs Plastik (Windows XP mode).  Firefox looks pretty darn cool with Mostly Crystal. :KS

---

### Post by DizzyTech on 2007-02-20
Hello...?

---

### Post by getaceres on 2007-02-20
I haven't been able to do that. There's some gnome daemon (i don't remember its name) that applies configuration options to gnome so theorically it could be possible to get the icons working running this daemon at startup.

---

### Post by DizzyTech on 2007-02-20
Would this daemon, by any change, be as plaintext as the rest of the items in GNOME? Say, gnome-settings-daemon?

---

### Post by DizzyTech on 2007-02-21
Sorry for the double post, but I think I have it!  Ironically, the app is gnome-settings-daemon, and here's how you go about it:

Run the following command:
```

kdesu kate ~/.kde/Autostart/gnome-settings-daemon

```

Paste the following in the Kate window that opens (after entering your password):
```

#!/bin/bash
gnome-settings-daemon

```

Close the window (make sure it saves), and then go back to Konsole (or another terminal) and enter the following command:
```

sudo chmod +x ~/.kde/Autostart/gnome-settings-daemon

```

Ta-da!  This works for applications that only implement the system's icon set, and should only work with GNOME installed and icons set.  Note that apps that use non-native icons (or explicit defaults), like radios in Rhythmbox and Apply in Synaptic, will still be ugly, but things like Evolution (when using omething like Clearlooks for GTK+ Apps in KDE) will look exactly like native.

Be careful when following this.  If gnome-settings-daemon ends somehow in KDE, all GTK+ apps will freeze and close, just like in GNOME.  (I thought it was fair warning, even though it's like killing Explorer in Windows).

:popcorn:

---

