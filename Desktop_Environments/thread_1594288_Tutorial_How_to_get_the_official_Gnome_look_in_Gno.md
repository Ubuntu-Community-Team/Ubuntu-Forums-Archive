---
title: "Tutorial: How to get the official Gnome look in Gnome apps while using KDE"
date: 2010-10-12
forum: Desktop Environments
---

### Post by James78 on 2010-10-12
Hello, have you ever been in the situation where you use GTK based apps a lot in KDE, but the app looks pretty ugly, or not how you wish it would look? Anything's better than QTCurve if you ask me, even the regular Gnome theme. This guide will show you how to see your Gnome theme in all your Gnome apps, while using KDE.

Before you begin, please note that my method requires you actually have Gnome installed first, which is located in the ubuntu-desktop package, so install that first if you haven't already.

It's really simple! For KDE 4.5:
1. Open System Settings.
2. Click Startup and Shutdown.
3. Click Add Program, input "gnome-settings-daemon" (no quotes!), and press ok.

That's it! You probably want this to start only in KDE, so in addition to the earlier steps, select the "gnome-settings-daemon" entry you just created, click the Advanced button, and select "Autostart only in KDE".

Please note that this will override the default KDE option for "GTK+ Appearance", but I'd suggest selecting your current Gnome theme for this option anyways. This also, in some of my apps (like the command line subversion client), caused them to ask for the Gnome password manager, but it was never a big deal for me either; if you don't have a password set on the Gnome password manager, it should load seamlessly, otherwise you might get that annoying "What's your password?" popup.

Additionally, if you want to change the theme displayed, just execute "gnome-control-center" from the terminal (or press Alt+F2 and do it from there; it's faster), select Appearance, and change the theme.

Hope this helped someone out! :)

As a side note: Yes, I know that KDE4 already skins Gnome apps with the GTK option thing, however, if you do something like starting up Synaptic, you'll notice that KDE can't skin that app, and other similar apps. Doing the things mentioned in this topic will get programs like Synaptic skinned also. Of course, doing this also makes all your Gnome apps obey your Gnome settings as well.

---

