---
title: "How to resize the KDE-Starter in 16.04 permanently?"
date: 2016-04-24
forum: Desktop Environments
---

### Post by Bambasty on 2016-04-24
Hello!

In the past versions of KDE (before Plasma5 I believe) this was easily possible, just by grabbing the upper right corner of that starter and dragging it around. 

Now this can still be done by pressing left ALT while using the right mouse button at the same spot, but it is not saved. So if I want so have all my favorites accessible without scrolling this needs to be repeated after every launch. Not really comfortable. 

Does someone know some trick how to make any size changes to the KDE-Starter permanent or is it just a bug? 

Thanks! :KS

---

### Post by Rog131 on 2016-04-25
If Kickoff: [https://bugs.kde.org/show_bug.cgi?id=361859](https://bugs.kde.org/show_bug.cgi?id=361859)

The default minimum size can be set at /usr/share/plasma/plasmoids/org.kde.plasma.devicenotifier/contents/ui/FullRepresentation.qml

There are:
```

    Layout.minimumWidth: units.gridUnit * 26
    Layout.minimumHeight: units.gridUnit * 34

```

Set bigger factor ( 34 -> 40 ) and restart the plasmashell - log out - log in.

---

