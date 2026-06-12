---
title: "Gnome 3 on 12.10 issues."
date: 2013-01-21
forum: Desktop Environments
---

### Post by Insert Cool Username Here on 2013-01-21
I have a few issues with Ubuntu 12.10 and Gnome 3, first is the screen saver automatically kicking in after 10 minutes regardless of disabling all powersaving/screensaver settings. I've had to resort to installing Xscreensaver and disabling that everytime I log on to get around this.

It's not such an issue with Unity or Gnome 2 but with Gnome 3 when putting my mouse to the bottom left or right corner a dock pops up, how can I disable this? I've tried installing something called "unclutter" to autohide my mouse after X amount of seconds but it doesn't work.

I'd really like to eliminate this screensaver problem and pop up dock permanently.

Any help would really be appreciated thanks.

---

### Post by Insert Cool Username Here on 2013-01-24
Does anyone know how to disable the panel/dock at the bottom of gnome 3 when you put your mouse to the bottom left or right corner?

---

### Post by markbl on 2013-01-24
I dislike that auto popup also.
```

sudo vim /usr/share/gnome-shell/js/ui/messageTray.js

```
and comment out the following (around line 1519 for current gnome shell in ubuntu 12.10):
```

// pointerWatcher.addWatch(TRAY_DWELL_CHECK_INTERVAL, Lang.bind(this, this._checkTrayDwell));

```
Then restart gnome-shell. You can still see the message tray using the normal activities view (via super/mouse) or via super+m.

---

### Post by Insert Cool Username Here on 2013-01-24
sudo: vim: command not found

:(

---

### Post by markbl on 2013-01-24
Sorry, use vi instead of vim.

---

### Post by Frogs Hair on 2013-01-25
You must have installed Xscreen saver because there is none by default with gnome 3.6. Can you link the instructions ?

---

