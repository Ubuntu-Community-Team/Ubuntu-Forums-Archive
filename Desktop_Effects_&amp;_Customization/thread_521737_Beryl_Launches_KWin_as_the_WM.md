---
title: "Beryl Launches KWin as the WM"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by kooseefoo on 2007-08-09
Okay, I just added beryl to my kubuntu feisty install. I used this howto:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

Then, I added a script called startberyl in /usr/bin:
```
#!/bin/sh
export KDEWM="/usr/bin/beryl-manager"
exec startkde
```

Finally, I turned it into a session type with a file in /usr/share/xsessions called beryl.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=Beryl+KDE
Exec=/usr/bin/startberyl
Icon=
Type=Application

```

However, when beryl starts, it loads kwin as the window manager. If I right-click the beryl jewel (or type beryl-manager into a terminal) I can select beryl as the window manager from the pop-up.

Any ideas on why beryl wouldn't choose itself as the default?


Thanks,
Chris

---

### Post by kooseefoo on 2007-08-09
Found the problem. 

For those who might find this via the 'search' function, beryl sometimes crashes when you logout. This can cause it to load the fallback WM when it reloads. Just right-click on the little jewel and deselect "Load Fallback Window Manager if beryl crashes"

That seems to fix the issue.

Another note: with the aforementioned setup, the jewel icon doesn't appear on my system tray. Any ideas on how to fix that?

Thanks,
Chris

---

