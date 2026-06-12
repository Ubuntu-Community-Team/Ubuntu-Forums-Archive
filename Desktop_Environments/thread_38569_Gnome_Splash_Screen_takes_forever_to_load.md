---
title: "Gnome Splash Screen takes forever to load"
date: 2005-06-01
forum: Desktop Environments
---

### Post by vinoo_v on 2005-06-01
Hi,
I just installed Ubuntu Hoary and the Gnome (not GDM) splash screen takes a long time to come on screen. 'top' shows all the gnome related processes are sleeping  and the disk isn't spinning. Could it be something is waiting for a timeout? Thanks

Vinoo

---

### Post by dsine on 2005-06-01
is ur network functional ?

---

### Post by vinoo_v on 2005-06-02
Yes the network comes up immediately. I'm able to ping google from a text mode console while I wait.

---

### Post by NeoChaosX on 2005-06-02
Try loading a Failsafe GNOME session, and check your start up programs in Preferences > Sessions. Perhaps one of them is casuing your boot-up to stall.

---

### Post by vinoo_v on 2005-06-02
The Failsafe session took the same amount of time. However since the last post I went on a settings changing spree and now everything works   :???: Oops. I'm sorry I didn't apply the changes one at a time. Anyway the things I did were:

1. run 'prelink'
2. disable Sound Server from Settings -> Sound.
3. change the default source and sink in the Multimedia Systems Selector to 'alsasink ' and silence respectively from 'esdsink'.
4. Install the beep-media-player (which IMHO should be shipping instead of XMMS)

The latter three changes were not related to solving the startup problem but trying to get a DVD playing in 'mplayer'. Anyway, for whatever reason things are working. Thanks for all the help.

Vinoo

---

