---
title: "This is all I want. For xscreensaver to come on after 10 minutes or so"
date: 2012-06-16
forum: Desktop Environments
---

### Post by Cobbleybabbins on 2012-06-16
Well,  I have lurked around trying to solve this one on my own, HOWEVER...

I have xscreensaver installed, but it does not come on when it is  supposed to. This is all I want.  For xscreensaver to come on after 10  minutes or so

It does work with the CNTRL+ALT+L or using "xscreensaver-command - activate"

It does not lock screen from menu bar, hence my finding this thread.

I am running Pangolin 12.04

I thought if I could have gnome-screensaver linked to activate the xscreensaver that would work, but still havent found a fix.  

Need professional help,

Thanks!
                                                                                                  [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/rebrand/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12031870")

---

### Post by Cobbleybabbins on 2012-06-17
Bump

---

### Post by Cobbleybabbins on 2012-06-17
I found this on a bug report on launchpad.net and it looks like maybe a lead?  I am not sure anything about python scripts and it needs to be updated for 12.10?  Im lost.

Here:
**lock screen fails with xscreensaver**

[https://bugs.launchpad.net/indicator-session/+bug/528094](https://bugs.launchpad.net/indicator-session/+bug/528094)




 [cpaul (chainpaul)]("https://launchpad.net/%7Echainpaul")             wrote             on 2010-11-29:                                                            [ #31]("https://bugs.launchpad.net/indicator-session/+bug/528094/comments/31")                                                               Since you have disabled the gnome-screensaver, the dbus object org.gnome.ScreenSaver is not created while the Gnome starts.
 We need to create the dbus object org.gnome.ScreenSaver and implement the Lock method.
 I use the below python script to create the org.gnome.ScreenSaver.
 ----------- myscreen-dbus.py --------
#!/usr/bin/python
 import dbus
import dbus.service
import dbus.glib
import gobject
import os
 class ScreenDbusObj(dbus.service.Object):
    def __init__(self):
        session_bus = dbus.SessionBus()
        bus_name=dbus.service.BusName("org.gnome.ScreenSaver",bus=session_bus)
        dbus.service.Object.__init__(self,bus_name, '/org/gnome/ScreenSaver')
     @dbus.service.method("org.gnome.ScreenSaver")
    def Lock(self):
        os.system( "xscreensaver-command -lock" )
 if __name__ == '__main__':
    object=ScreenDbusObj()
    gobject.MainLoop().run()
 You should keep this script running on the background. The 'Lock  Screen' button will call the method Lock and the method Lock will  execute the xscreensaver-command -lock.
 To automatically start this script, you need to add the command, i.e. /path-to-the-script/myscreen-dbus.py & in the System/Preferences/Sessions.

---

### Post by zombifier25 on 2012-06-17
This worked for me:

Remove gnome-screensaver completely, add xscreensaver -no-splash to startup, and run this command to link gnome-screensaver-command to xscreensaver-command:
```
sudo ln /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```
Ctrl + Alt + L will lock the screen, but for some reason Power > Lock won't.

---

### Post by Cobbleybabbins on 2012-06-17
```
-ThinkPad-T60:~$ sudo ln /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
ln: failed to create hard link `/usr/bin/gnome-screensaver-command': File exists


```

Heres what I get.  I think I have it setup, however the screensaver will not start automatically.  It works fine with CNTRL + ALT + L.

meh.

---

### Post by zombifier25 on 2012-06-18
In that case,
```
sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

also, try opening xscreensaver's configuration tool (xscreensaver-demo, if you want to launch from command line) and see if the settings are set. Also, check if any warnings show up.

---

### Post by Cobbleybabbins on 2012-06-19
That worked!  Thanks a bunch, I knew someone here could help.  

Problem SOLVED :KS

---

