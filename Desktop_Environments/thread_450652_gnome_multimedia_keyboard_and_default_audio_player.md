---
title: "gnome: multimedia keyboard and default audio player"
date: 2007-05-21
forum: Desktop Environments
---

### Post by Einaudi on 2007-05-21
I use Ubuntu7.04 and i have a Bluetooth DiNovo multimedia keyboard. It
works perfectly in gnome. I set the multimedia button in "keyboard
shortcuts" menu and they show as "XF86AudioPlay/Media/Stop/ecc..".

My problem is that the media key always starts Rythmbox while i use
another media player (quod libet but this is not the point). I search,
even in gconf-editor, but dont' find any way to change the default
player linked with the "media player key" on my keyboard.

"Default Apps Menu" (dont' know the exact name in english) only shows
default browser and mail application.

Thanks in advance.

Bye

---

### Post by sc00ter on 2007-05-24
This looks like it's been fixed in Gutsy, follow the link for more info:

**[https://bugs.launchpad.net/control-center/+bug/4265](https://bugs.launchpad.net/control-center/+bug/4265)**

Hopefully it will find its way into the Feisty updates soon. As a work-around you can create a symbolic link (as detailed in the launchpad entry).

I use Banshee as my preferred player, so I ran the following command :

```
sudo ln -s /usr/bin/banshee /usr/local/bin/rhythmbox
```

Now when I hit the media key on my keyboard for "Music" I'm greeted with the Banshee window :D

**NOTE: **When you attempt to launch RhythmBox from the Applications menu, your "linked" media player will launch instead.

To remove the symbolic link, just use the following:

```
sudo unlink /usr/local/bin/rhythmbox
```

---

