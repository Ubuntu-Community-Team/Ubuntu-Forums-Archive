---
title: "LXDE and Gnome Screensaver"
date: 2014-04-19
forum: Desktop Environments
---

### Post by temporos on 2014-04-19
Just finished a clean install of Lubuntu 14.04, and I can't seem to find any screensavers. I can't believe one didn't come packaged with Lubuntu. :confused: In any case, I installed gnome-screensaver from the package manager, but I still can't get it to show up in the applications menu. I've tried logging out and back in again, and even restarting, but no Gnome Screensaver entry in the applications menu. Any ideas?

I think it installed fine.
```
$ gnome-screensaver --version
gnome-screensaver 3.6.1

```

---

### Post by Dennis N on 2014-04-19
Lubuntu 14.04 and Xubuntu 14.04 both come with Light Locker, which is a screen saver (providing blank screen only) and screen lock for the login screen. xscreensaver isn't installed by default anymore. I noticed the Light Locker settings app in the main Lubuntu menu (not using Lubuntu right now, so can't be more specific).

Since you installed gnome-screensaver as well, you would now have two screen savers. I would uninstall gnome-screensaver. 

If you want xscreensaver, you can disable light locker as a startup application, or just uninstall it, then install xscreensaver (and optionally xscreensaver-gl and rss-glx), and the data packages.

---

### Post by temporos on 2014-05-04
Hi, Dennis. Thanks for the reply (despite its tardiness). :)

I uninstalled gnome screensaver, disabled lightbox, and installed xscreensaver as you suggested. It seems to be working fine now, just as it did in Lubuntu 13.04.

The reason I had installed gnome screensaver, though, was because it is supposed to be the "lubuntu supported" screensaver over xscreensaver. That's what the Synaptic Package Manager says, anyway. I find it less than amusing that the Lubuntu team would tell its users to use a new package that doesn't work instead of the tried-and-true package. :facepalm: It's always something with Lubuntu...

---

### Post by SonnyE on 2014-05-07
You can have any screensaver you want in gnome-screensaver, as long as it's black.

The screensaver time setting when using gnome-screensaver in LXDE or Lubuntu is the xset command in ~/.config/autostart/screensaver-settings.desktop

To test it, I tried `xset s 10` in a terminal, and that made the screen black after 10 seconds of inactivity. See `man xset` for more details.

The background for gnome-screensaver's locker password screen is the same as the Ubuntu desktop wallpaper if you have Ubuntu, or you can set it by dconf under: org.gnome.desktop.background

Different screensavers and screen lockers aren't compatible. You don't have to uninstall the one you don't want to use. You can check under "Default applications for LXSession" that only one is an entry, and use `ps -ef | grep screen` to check that only one is running.

---

### Post by temporos on 2014-05-07
[quote="SonnyE"]You can have any screensaver you want in gnome-screensaver, as long as it's black.[/quote]

So, really, you can't have *any* screen*savers* in gnome-screensaver. You can have one screen* blanker*. :-s Seems like a pretty big step backward from xscreensaver to me.

---

### Post by SonnyE on 2014-05-07
I made a 100% black full-screen png image to compare with  gnome-screensaver, and found out gnome-screensaver was actually turning the screen  off, it wasn't just my monitor detecting no picture. So you can get that  blank screensaver. 

Then there's another screensaver you can get from gnome-screensaver, using the command:

xset s noblank s 20 2

That gives me, after waiting 20 seconds a black & white fine herringbone pattern, that shifts every 2 seconds to avoid burn-in.

That is a screen saver, technically.

---

