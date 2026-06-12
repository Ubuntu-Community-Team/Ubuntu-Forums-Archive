---
title: "How to edit a Unity app launcher command?"
date: 2011-11-13
forum: Desktop Environments
---

### Post by calande on 2011-11-13
Hello,

I'm using Unity 2D with 11.10. I have an app shortcut in my left Unity bar, and I'd like to edit the command that's executed when I click the icon. How could I do it?
Thanks,

---

### Post by Docaltmed on 2011-11-13
I think the launchers are all kept here:

~/.local/share/applications/nameoflauncher.desktop

use gedit to make changes to the appropriate file. There's a specific format, you can get more information here:

[http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)

---

### Post by calande on 2011-11-13
Thanks. In this folder, I have a large number of *.desktop* files, but most of them are not related to my Unity sidebar, and Seamonkey (of which icon is on my Unity sidebar) is not listed in this folder. Where could I go from here? Thanks.

---

### Post by mc4man on 2011-11-13
If you did a standard seamonky package install then
```
gksudo gedit /usr/share/applications/seamonkey.desktop
```

The launch command is on the Exec= line, note that not all commands that work from a terminal will work correctly in a .desktop, you may need to test a bit.

---

### Post by calande on 2011-11-13
That's great! Thanks alot :)

---

### Post by David006 on 2011-11-13
> **mc4man said:**
> If you did a standard seamonkey package install then
```
gksudo gedit /usr/share/applications/seamonkey.desktop
```

If is **MUCH** safer to first copy the  *.desktop*  file to your own user area.  Then you can always delete and start over.

Do this first (once):

```
  cp /usr/share/applications/seamonkey.desktop ~/.local/share/applications
```

And then use this to edit:
```
  gedit ~/.local/share/applications/seamonkey.desktop &
```

( The ampersand '&' releases the command line immediately. )


Attached are several of my favorites, for your education or use.  The LibreOffice icon can replace ALL the other ones, and ALL add several right-click options.  Enjoy.

---

### Post by calande on 2011-11-13
Thanks!

---

### Post by David006 on 2011-11-13
Updated, with screenshots.

---

### Post by calande on 2011-11-13
Pretty neat, I didn't know this was possible.

---

### Post by Copper Bezel on 2011-11-14
Yeah, that's some nice use of the Unity quicklist feature. I've done that with the Nautilus launcher in the past and found it quite useful. (Too bad they don't work in Shell. Blech.)

I always have to copy gedit's and Chrome's .desktops to the .local location and add --new-window to the exec line. I can't stand opening a file or a Google search on one workspace and having it pop up as a tab on another.

---

### Post by calande on 2011-11-14
That makes Unity less bad than at 1st sight. Still, I hope we can get the previous interface like the 10.x series, and Unity is slow on my computer. 3D doesn't work anymore with Unity (too damn slow), and even in 2D, the Unity sidebar take a second to pop up. Not to mention the dumbed-down interface where you can't find what you used to at a click...But you heared that before, and I'm diverging from the original topic :)

---

