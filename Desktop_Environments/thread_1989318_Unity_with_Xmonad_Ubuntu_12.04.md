---
title: "Unity with Xmonad Ubuntu 12.04"
date: 2012-05-28
forum: Desktop Environments
---

### Post by zym0 on 2012-05-28
So I'm more familiar with tiling windows manager but after seeing the Ubuntu for Android preview I thought i'll give Unity on my Laptop another try.
So i tried to imply Xmonad into it.
An followed those two descriptions.
[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Unity_2D](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Unity_2D)
[http://askubuntu.com/questions/128997/how-to-troubleshoot-failed-to-load-session-errors](http://askubuntu.com/questions/128997/how-to-troubleshoot-failed-to-load-session-errors)

But now the Session starts like this
[IMG]http://s15.postimage.org/vdd9g64nd/2012_05_28_211145_1920x1080_scrot.png[/IMG]

here are my relevant files:

xmonad.hs
```

import XMonad
import XMonad.Config.Gnome
import XMonad.Layout.Gaps

myManageHook = composeAll (
    [ manageHook gnomeConfig
    , className =? "unity-2d-panel" --> doIgnore
    , className =? "unity-2d-shell" --> doIgnore
    ])

main = xmonad gnomeConfig { manageHook = myManageHook }
```


/usr/share/applications/xmonad.desktop 
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Xmonad
Exec=xmonad
NoDisplay=true
X-GNOME-WMName=Xmonad
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
X-GNOME-Autostart-Notify=true
```

/usr/share/gnome-session/sessions/xmonad.session 
```
[GNOME Session]
Name=Xmonad/GNOME
RequiredComponents=unity-2d-shell;unity-2d-panel;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=xmonad
```

/usr/share/xsessions/xmonad-gnome-session.desktop
```
[Desktop Entry]
Name=Xmonad GNOME
Comment=Tiling window manager
TryExec=/usr/bin/gnome-session
Exec=gnome-session --session=xmonad
Type=XSession

```

---

