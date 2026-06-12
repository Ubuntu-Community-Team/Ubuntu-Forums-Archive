---
title: "gnome-app-installer disappearing"
date: 2006-07-10
forum: Desktop Environments
---

### Post by m_bridge on 2006-07-10
Ciao, 
gnome-app-installer stopped working from a couple of days and i can't figure out what's wrong

```
[>bridge< ~/] gnome-app-install
Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:20152): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 171, in __init__
    self.updateCache()
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 667, in updateCache
    progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 124, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 269, in refresh
    menu = xdg.Menu.parse(os.path.join(self.menudir, "applications.menu"))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 518, in parse
    __postparse(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 667, in __postparse
    __postparse(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 678, in __postparse
    menuentry = MenuEntry(directory, dir)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __init__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 74, in parse
    raise ParsingError("[%s]-Header missing" % headers[0], filename)
xdg.Exceptions.ParsingError: ParsingError in file '/home/bridge/.local/share/desktop-directories/Games.directory', [Desktop Entry]-Header missing

```

The gui opens after but while checking the dependancies gives the rest of the error (after the empty line) and quits
synaptics works fine


The file that gives error in the last line (~/.local/share/desktop-directories/Games.directory) is in fact an empty file, is that normal? :confused: 

if found some similar errors around but none of the proposed solution worked
[http://Add-remove not working showthread.php?t=202134]("http://www.ubuntuforum.org/showthread.php?t=202134")
[add remove programs showthread.php?t=201491]("http://www.ubuntuforum.org/showthread.php?t=201491")

Any idea????
Cheers
M

---

### Post by aysiu on 2006-07-10
[This thread](http://ubuntuforums.org/showthread.php?t=184657) might help.

---

### Post by m_bridge on 2006-07-10
sudo apt-get remove --purge gnome-app-install
sudo apt-get install --reinstall gnome-app-install

that didn't work (i mean, it worked but the problem is unchanged..)

I didn't install firefox recently the only things that i changed to my configuration on the day it broke were
installing sun java 5 and make it default (for azureus)
the auto-update of july 6/7 (packages were ppp, login, passwd and a couple of other)

---

