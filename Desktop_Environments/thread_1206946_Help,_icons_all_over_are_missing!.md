---
title: "Help, icons all over are missing!"
date: 2009-07-07
forum: Desktop Environments
---

### Post by Fzang on 2009-07-07
I don't know how or when it started, but all over the system icons seem to be missing. I've already reinstalled the hicolor from synaptic multiple times but it doesn't help at all. I have no idea what to do so any help would be appreciated.

It looks like this:

[IMG]http://i29.tinypic.com/2573ddz.png[/IMG]

---

### Post by Fzang on 2009-07-08
Bump :/

---

### Post by Jonnox on 2009-07-08
Go into the folder via console and they should be called```
keyboard.desktop
``` etc I believe. If they are, just open them in a text browser like vim or pico and see where the icon reference is. ie

```
...
Exec=gnome-keyboard-properties
Icon=gnome-dev-keyboard
...
```

You then have to check which theme you are using and make sure that the theme has that icon. So in mine, I use Human I believe, so there is a file:

```
/usr/share/icons/Human/<size>/devices/gnome-dev-keyboard
```

If the icons are in different themes, find out by using:

```
locate gnome-dev-keyboard
```

You can just copy the missing icons from other themes into your current and they should show up.

I hope that makes sense :popcorn:

---

### Post by Fzang on 2009-07-08
Sorry, it doesn't work. Usually, if the system can't find the icons it uses the fallback theme which is hicolor. But it doesn't work and now it only accepts icons from the icon theme. Even the default "human" icon theme can't fill up the missing icons.

Isn't there anything I can reinstall or fix or anything? This goes deeper than a lacking icon set, because usually an icon set shouldn't do this.

---

### Post by Fzang on 2009-07-10
Dam, no solutions? seems like a free reinstall for me...

---

