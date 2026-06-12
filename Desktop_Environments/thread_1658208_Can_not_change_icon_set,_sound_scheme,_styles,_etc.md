---
title: "Can not change icon set, sound scheme, styles, etc."
date: 2011-01-02
forum: Desktop Environments
---

### Post by Michael Moffitt on 2011-01-02
I just installed a fresh copy of Ubuntu on my small 64GB SSD alongside my main drive for storage. I got everything set up just how I like it (customized clearlooks with Ubuntu Mono Light icons) the same as I have it on my laptop. I disabled all system sound effects.

This morning, I wake up to it having a different icon set, and the menus having an identical grey scheme. In addition, the Ubuntu system sound effects are playing, even though in the settings it says they are disabled.

I'm not really sure what's wrong! It's the same in both compiz and metacity.

Here's a screenshot. Note how the boring old-style theme is applied in the update window and the menu at the top, yet the customizing themes window has the correct appearance for the buttons (funny coincidence)

EDIT: I think I've narrowed it down to gnome-settings-daemon. When I try to initialize it via the terminal I get this:

** (gnome-settings-daemon:3852): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3852): WARNING **: Could not acquire name


[IMG]http://mikejmoffitt.com/img/ubuntu.png[/IMG]

---

### Post by Frogs Hair on 2011-01-02
Check this and see if it applies.[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

---

