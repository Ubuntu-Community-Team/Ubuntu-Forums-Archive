---
title: "Widget list in Kubuntu 15.04 is truncated on right"
date: 2015-05-17
forum: Desktop Environments
---

### Post by pwabrahams on 2015-05-17
If I want to add a widget to my desktop in Kubuntu 15.04, clicking on the "Add Widgets" button brings up a list of available widgets.  The trouble is that the descriptions, and in some cases even the names, of the widgets are truncated on the right with "...".   That wouldn't be so bad if I could expand the list window to the right, but that doesn't seem to be possible, and I can't find any other way to view the full descriptions.  Is this a designer goof, or what?

---

### Post by Rog131 on 2015-05-18
Do you see something like this ?

[http://i.imgur.com/40mKGja.png](http://i.imgur.com/40mKGja.png)

I get this by editing the /usr/share/plasma/shells/org.kde.plasma.desktop/contents/explorer/WidgetExplorer.qml line:
```
width: Math.max(heading.paintedWidth, units.gridUnit * 16)
```


The normal, at here, is:
[http://i.imgur.com/RP8ny0S.png](http://i.imgur.com/RP8ny0S.png)

Maybe a place of a bug report ;) [https://bugs.kde.org](https://bugs.kde.org)

---

### Post by pwabrahams on 2015-05-18
yes, I get pretty much what you've shown in the upper picture.  I'm confused, though: which is the correct text for qml.line?  Can I fix the problem by changing that line until the fire department arrives -- and if so, to what?

---

### Post by Rog131 on 2015-05-18
You could 'hardcode' the width same way as the height is.

Something like:

```
Item {
    id: main

    width: 320
    height: 800//Screen.height
```

[http://i.imgur.com/WQ6kTGz.png](http://i.imgur.com/WQ6kTGz.png)


After edit - shut the plasmashell:
```
kquitapp5 plasmashell
```
and restart the plasma:
```
plasmashell
```
or simply log out - log in.

---

### Post by wildmanne39 on 2015-05-18
Please use url's or thumbnails when posting images.
Thanks

---

### Post by pwabrahams on 2015-05-18
Generally it's possible to enlarge (or shrink) the boundaries of a window by dragging its edges.  This is the case in practically any windowed system.  The real problem here is that the window in question has inflexible dimensions.  It ought to be possible to enlarge it.

I will probably file a bug report about this if I can figure out what to file the bug against.

---

