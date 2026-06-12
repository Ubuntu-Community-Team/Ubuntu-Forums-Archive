---
title: "can you emulate 2 desctops in wine"
date: 2009-02-03
forum: Desktop Environments
---

### Post by gillbilliee on 2009-02-03
hi im learnin to use all this and im wonderin if there is a way to emulate 2 virtual desktops at once in wine. spent a while lookin on the internet and i cant fid any 1 who knows.

---

### Post by sedawk on 2009-02-03
More or less a workaround that works.
Replace "user" with your username:

```

mkdir /home/user/wine_desktop_001
export WINEPREFIX="/home/user/wine_desktop_001"
winecfg # Go to graphics, set emulate virtual desktop
nohup wine winefile &
mkdir /home/user/wine_desktop_002
export WINEPREFIX="/home/user/wine_desktop_002"
winecfg # See above 
nohup wine winefile &

```

This way you get two different wine's running.
If you want to "share" drive_c you might try to use a symbolic link
in desktop_002 pointing to drive_c of desktop_001.

Actually I try to install every windows application in its own
environment (another WINEPREFIX) because it doesn't waste much space and
removing an application is easy, by simply removing the directory
defined by WINEPREFIX.

---

