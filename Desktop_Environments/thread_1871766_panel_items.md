---
title: "panel items"
date: 2011-10-29
forum: Desktop Environments
---

### Post by precluder on 2011-10-29
hey all
i recently installed ubuntu 11.10 so the default interface was unity

then i installed gnome shell and tried changing themes , now i ended up in a blue theme without the original backup theme. however that was not my problem. indeed it is kool.

but in all the themes i install,
i see file,view,bookmarks, help in the background on the panel.They look as if my panel overlapped on them. They are inactive and pretty much upset my mood. I am attaching a screenshot.

Plz help!
precluder

---

### Post by stinkeye on 2011-10-29
This command will stop the Unity global menu from appearing in all 
sessions except Ubuntu.
```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

---

### Post by precluder on 2011-10-30
Thanks buddy

Seems like applying the fix further distorted the screen. 
the words on the panel screen look destroyed.looks like old chinese tv video game

Could you fix this...?

---

### Post by stinkeye on 2011-10-30
> **precluder said:**
> Thanks buddy

Seems like applying the fix further distorted the screen. 
the words on the panel screen look destroyed.looks like old chinese tv video game

Could you fix this...?

No problem buddy,
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
Fixed back the way it was, buddy.


The original fix was for all sessions **except** ubuntu.
Are you logging in to the GNOME session.
```
echo $DESKTOP_SESSION
```

Another way is to use gnome-tweak-tool to stop the file manager handling the desktop.
Cya later buddy.
[-(

---

### Post by BlinkinCat on 2011-10-30
What is your graphics card?

There have been problems with AMD drivers and gnome 3

---

