---
title: "What's drawing my background, and how can I stop it?"
date: 2010-06-29
forum: Desktop Environments
---

### Post by noahlt on 2010-06-29
I want to be able to draw my background using a program like xscreensaver.

I've already tried to tell Nautilus/Gnome to stop drawing my desktop:


```
noah@aries:~$ gconftool-2 -g /desktop/gnome/background/draw_background
false
noah@aries:~$ gconftool-2 -g /apps/nautilus/preferences/show_desktop
false

```

These seem to have no effect.  Neither of the following commands are able to redraw my desktop:

```
$ /usr/lib/xscreensaver/galaxy -root
^C
$ xsetroot -grey

```

When I log out, the grey background from xsetroot is visible briefly, which makes me think that Gnome is simply drawing over it.

When I use gconf-editor to change /desktop/gnome/background/picture_filename to point at a different image file, my background is redrawn using the new image file, so whatever is drawing my desktop is still reading from my Gnome configuration.

I am running Karmic with Compiz.

Any tips?

---

### Post by dino99 on 2010-06-29
some ideas here:

[http://www.khattam.info/2010/02/15/howto-video-wallpaper-on-ubuntu-10-04-lucid-lynx/](http://www.khattam.info/2010/02/15/howto-video-wallpaper-on-ubuntu-10-04-lucid-lynx/)

---

