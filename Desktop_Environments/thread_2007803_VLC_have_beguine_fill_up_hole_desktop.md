---
title: "VLC have beguine fill up hole desktop"
date: 2012-06-21
forum: Desktop Environments
---

### Post by Azyx on 2012-06-21
On ubuntu 10.04lts and gnome 2x. Until for a month when I started a movie VLC just open a little window, and then when I dubbel-click I get full screen. If you click on the right button in the upper window, the be no diffentet between 'filled hole desktop' and 'medium' or what it is called are the same. I have to make it smaller with 'resize' windows or grab the corner to make it smaller.
Is there a way to fix this?

---

### Post by papibe on 2012-06-21
Hi Azyx.

Tried this:
```
VLC -> Tools -> Preferences
```
There is a button at the bottom that says:
```
Reset Preferences
```
Then restart VLC.

If that doesn't work, you can reset all settings by doing:
```
rm -rf ~/.config/vlc
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by oldos2er on 2012-06-21
Double-click it again.

---

### Post by Azyx on 2012-06-21
> **papibe said:**
> Hi Azyx.

Tried this:
```
VLC -> Tools -> Preferences
```
There is a button at the bottom that says:
```
Reset Preferences
```
Then restart VLC.

If that doesn't work, you can reset all settings by doing:
```
rm -rf ~/.config/vlc
```
I hope that helps, and tell us how it goes.
Regards.

Thanx :)  Remove the config-files in ~/.config/vlc helped.

---

