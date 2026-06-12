---
title: "gnome3 on ubuntu 11.10 with xscreensaver: lock screen does not work"
date: 2011-10-20
forum: Desktop Environments
---

### Post by alex170872 on 2011-10-20
Hi all, 

I appreciate some help in a problem I have with a not-working lock-screen. 

I am using gnome3 on Ubunto 11.10, and I installed xscreensaver, after removing the gnome-screensaver. If I type 

> xcreensaver

I am able to configure the xscreensaver and everything seems to work. 
However, when I click on 'Lock Screen' from the pull-down menu at it's default location in the top panel on the very right (where you also can choose to lock out, to shut down), nothing happens. The screen is not being locked. And when I try to run it from the command line as follows:

>  xscreensaver-command -lock

I get a message:

xscreensaver-command: no screensaver is running on display :0.0

I have no idea what this message meas, but if anyone has an idea how to 'activate' the 'Lock Screen' that would be really helpful...


Thanks
  Alex

---

### Post by coriolus on 2011-10-20
I get the same exact symptoms, can't seem to figure out why..

Odd thing is, when I turn off my monitor so ppl don't think my workstation in unlocked :P  when I get back and turn on my monitor the screensaver is active and I am prompted to log in..

oddities I tell ya~

---

### Post by r0bo01 on 2011-10-25
if you search "lock" from dash, lock screen app for xscreensaver is shown (just discovered this).  click and lock...

the control lock screen appears to be a gnome-screensaver-command (my ctrl-alt-L fails  complaining about valid command).  so  if gnome-screensaver has been removed (per forum advice), then i imaginge control lock screen  won't work any more.

---

### Post by alex170872 on 2011-10-31
Hi, 

> **r0bo01 said:**
> if you search "lock" from dash, lock screen app for xscreensaver is shown (just discovered this).  click and lock....

I am not sure what is meant by 'search "lock" from dash'. What does it mean? 

> the control lock screen appears to be a gnome-screensaver-command (my ctrl-alt-L fails  complaining about valid command).  so  if gnome-screensaver has been removed (per forum advice), then i imaginge control lock screen  won't work any more.

So I have to re-install gnome-screensaver? Will that be the solution so by clicking on the text ''Lock Screen" in the menu will lock the screen?


Thanks
  Alex

---

### Post by alex170872 on 2011-11-02
Hi again, 

I now installed gnome-screensaver again, and now the  ''Lock Screen" in the menu does lock my screen! However, it just shows a boring blank screen with no screensaver, which is not what I want. 

Is there really no-one who can help me with that issue? Or could give advise what other forum to try? A screensaver forum, a gnome forum, a whatever forum? Or do I have to code my own operating system so things work? I REALLY would appreciate some help! I want to be able to lock the screen by choosing "Lock Screen" from the menu on the top right where one can log out, and to have a screensaver (preferably one of the xscreensaver) running then!


Thanks
  Alex

---

### Post by phDaemon on 2011-11-02
So a few things i discovered... it seems that in the gnome js it specifically calls the dbus for the gnome-screensaver so it doesnt matter if you create a dynamic link to xscreensaver. Following the instructions here:

[Things to tweak after installing ubuntu 11.10](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Specifically
> 
No screensaver in GNOME 3.2

GNOME 3 doesn't have a screensaver, just a black screen. If you want to use a screensaver, you can use Xscreensaver - install it using the following commands (this will also remove gnome-screensaver):

sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

Then search for "Screensaver" in the menu and tweak its settings to your needs.

To add Xscreensaver to startup, open Startup Applications and add "xscreensaver -nosplash".

Let's also make the lock screen work (CTRL + ALT + L):

sudo ln -s /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command


However, that still leaves the menu. Since that is looking for a dbus entry, we will have to create our own...(That part i kinda had to figure out on my own)

create a script called screenLock.py with the following code in it
```

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

```

I placed mine in
```

~/.local/share/gnome-shell/customExtensions/screenLock.py

```

give it execute permissions (chmod +x) and run it after you've done all of the above...now the menu entry should work.

Hope that helps everyone out!

---

### Post by alex170872 on 2011-11-02
Hi, 

this finally seems to work out! Great, thanks a lot!!!

However, a couple of questions:

- I had to create the customExtensions directory by myself. Is that directory supposed to have existed before?

- Do I have to run the python script every time I log-in or reboot the computer? Or is this taken care of automatically? 

Thanks a lot for your great and well-explained help on this issue. 


Cheers
  Alex

---

### Post by phDaemon on 2011-11-02
You can add it to the autorun menu using the same method you would to add xscreensaver. Just make sure xscreensaver is already running before this runs.

So in the gnome-shell search for startup applications and add it under there (just like they explain for the xscreensaver -nosplash command).... easy!

Also, i created the customExtensions directory myself.... since gnome-shell tries to autoload everything inside the actual extensions/ dir i did not want to mess with it by adding a python script in there.

---

### Post by phDaemon on 2011-11-02
You should change the status of this topic to "SOLVED".

Also, IT IS NOT OK to PM me about the script. If you have any problems with it, open a thread or just follow the instructions here (As they seem to be working for everyone else).

---

### Post by sammXuser on 2011-11-24
Damn it,It Worked after giving me hell.Thanx

---

### Post by jornand on 2011-11-24
A major "thumbs up" for this tread. It made my life a whole lot easier when Oneiric hit me! :)

(Stay away from Oneiric screensaver 0.7.0 - it has nothing to do with Ubuntu. It is win32!)

---

### Post by yellowcrash10 on 2011-12-05
I couldn't believe it when there was no screensaver options in Ubuntu 11.10! The the whole purpose of a screensaver is to _save your screen_, which helps if you don't want your screen to permanently look like whatever you left open on it for the past 10 hours or so :)
Anyways, this thread helped me SO MUCH! Thanks a lot! :D

---

### Post by cybergalvez on 2011-12-06
I made a small change to the python script. Now rather then load xscreensaver and the dbus script I just autorun my screensaver.py script. Here is the script with the small mod

```

#!/usr/bin/env python

import dbus
import dbus.service
import dbus.glib
import gobject
import subprocess

def launchScreenSaver():
    subprocess.Popen(['xscreensaver', '-nosplash'])
 
class ScreenDbusObj(dbus.service.Object):
    def __init__(self):
        session_bus = dbus.SessionBus()
        bus_name=dbus.service.BusName("org.gnome.ScreenSaver",bus=session_bus)
        dbus.service.Object.__init__(self,bus_name, '/org/gnome/ScreenSaver')
 
    @dbus.service.method("org.gnome.ScreenSaver")
    def Lock(self):
        # os.system( "xscreensaver-command -lock" )
        subprocess.call(['xscreensaver-command', '-lock'])
 
 
if __name__ == '__main__':
    launchScreenSaver()
    object=ScreenDbusObj()
    gobject.MainLoop().run()


```

---

### Post by gemeinschaft on 2011-12-08
> **phDaemon said:**
> So a few things i discovered... it seems that in the gnome js it specifically calls the dbus for the gnome-screensaver so it doesnt matter if you create a dynamic link to xscreensaver. Following the instructions here:

[Things to tweak after installing ubuntu 11.10](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Specifically


However, that still leaves the menu. Since that is looking for a dbus entry, we will have to create our own...(That part i kinda had to figure out on my own)

create a script called screenLock.py with the following code in it
```

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

```

I placed mine in
```

~/.local/share/gnome-shell/customExtensions/screenLock.py

```

give it execute permissions (chmod +x) and run it after you've done all of the above...now the menu entry should work.

Hope that helps everyone out!


Thank you so much for solving this for me... I was very disappointed that this was not built into 11.10

You Rock :guitar:

---

### Post by trueluck3 on 2012-02-14
The script to make the System Menu (upper right hand corner) lock link work, does not work for me.  I tried both the original script and the modified script.  I tried loading it with the startup applications list, no go.  What do we need to do once we save the script?  How do we link the menu selection to that script (not that it does anything when run manually).:confused:

---

### Post by alfonso78 on 2012-02-29
> **trueluck3 said:**
> The script to make the System Menu (upper right hand corner) lock link work, does not work for me.  I tried both the original script and the modified script.  I tried loading it with the startup applications list, no go.  What do we need to do once we save the script?  How do we link the menu selection to that script (not that it does anything when run manually).:confused:

apparently this makes two of us.

I created the script and to test I try to run it from a terminal:

```
.local/share/gnome-shell/customExtensions/screenLock.py
```

but if I click on "Lock Screen" in the top right of the screen, the lock doesn't start...

---

### Post by nbartolome on 2012-05-17
Just want to add that I couldn't get the screen lock to work either using the python script.   (I truly appreciate the effort though.)
 
What I did was add the "Lock Screen"  launcher into my unity sidebar.   This should launch "xscreensaver-command -lock"

Then i removed the "Lock Screen   CTRL+ALT+L" from the menu item by doing:

gsettings set org.gnome.desktop.lockdown disable-lock-screen true

You may need to reboot for it to see the changes.

To revert the changes, simply run:
gsettings set org.gnome.desktop.lockdown disable-lock-screen false

---

### Post by Cobbleybabbins on 2012-06-16
Well, I have lurked around trying to solve this one on my own, HOWEVER, this is the closest thread I can find to my particuliar problem.

I have xscreensaver installed, but it does not come on when it is supposed to. This is all I want.  For xscreensaver to come on after 10 minutes or so

It does work with the CNTRL+ALT+L or using "xscreensaver-command - activate"

It does not lock screen from menu bar, hence my finding this thread.

I am running Pangolin 12.04

I thought if I could have gnome-screensaver linked to activate the xscreensaver that would work, but still havent found a fix.  

Need professional help,

Thanks!

---

### Post by balar on 2012-06-27
I have just installed Fedora 17, and I ran into the same issues outlined here.

I made small changes for autostart of xscreensaver and the screenLock.py

1. Edit /etc/xdg/autostart/gnome-screensaver.desktop

replace the line starting with EXEC=gnome-screensaver 
with:
EXEC=/usr/bin/xscreensaver -nosplash

2. Create a file in /etc/X11/xinit/xinitrc.d directory: eg. /etc/X11/xinit/xinitrc.d/screenLock.sh with a line to invoke the screenLock.py program:

eg.

#! /bin/sh
<path to the python program>/screenLock.py &

All other steps remain the same - eg setting up the symbolic linke for <Ctrl-Alt-L> shortcut to lock the screen, disabling gnome lock screen in system settings etc.

You do not have to uninstall the gnome-screensaver package.

If you logout and log back in, these two programs will be running when  the gnome session is established. Now, the 'Lock Menu' on the top right  works.

Thanks a lot to the original poster for coming up with the python script. It saved me a lot of grief.

---

### Post by falcogw on 2012-07-02
> **balar said:**
> I have just installed Fedora 17, and I ran into the same issues outlined here.

I made small changes for autostart of xscreensaver and the screenLock.py

1. Edit /etc/xdg/autostart/gnome-screensaver.desktop

replace the line starting with EXEC=gnome-screensaver 
with:
EXEC=/usr/bin/xscreensaver -nosplash

2. Create a file in /etc/X11/xinit/xinitrc.d directory: eg. /etc/X11/xinit/xinitrc.d/screenLock.sh with a line to invoke the screenLock.py program:

eg.

#! /bin/sh
<path to the python program>/screenLock.py &

All other steps remain the same - eg setting up the symbolic linke for <Ctrl-Alt-L> shortcut to lock the screen, disabling gnome lock screen in system settings etc.

You do not have to uninstall the gnome-screensaver package.

If you logout and log back in, these two programs will be running when  the gnome session is established. Now, the 'Lock Menu' on the top right  works.

Thanks a lot to the original poster for coming up with the python script. It saved me a lot of grief.

Hi, I followed this thread and finished with the settings you did in your post.

My button still does not work.
After creating the file in /etc/X11/xinit/xinitrc.d (I had to manually add the folder xinitrc.d) I could not load my desktop after rebooting...

I pressed ctrl-alt-f1 and removed the dir xinitrc.d and I am back at my desktop now. 

Is it possible something went wrong? 

Help would be appreciated  ;)

---

### Post by balar on 2012-07-09
> **falcogw said:**
> Hi, I followed this thread and finished with the settings you did in your post.

My button still does not work.
After creating the file in /etc/X11/xinit/xinitrc.d (I had to manually add the folder xinitrc.d) I could not load my desktop after rebooting...

I pressed ctrl-alt-f1 and removed the dir xinitrc.d and I am back at my desktop now. 

Is it possible something went wrong? 

Help would be appreciated  ;)

You must have the /etc/X11/xinit/xinitrc.d directory already. It has files like:
00-start-message-bus.sh, 50-xinput.sh etc.

For example,
rpm -q -f /etc/X11/xinit/xinitrc.d/00-start-message-bus.sh gives:

dbus-x11-1.4.10-4.fc17.x86_64

I have fedora 17 installed, and this RPM was installed as a part of Fedora 17.

Although this forum is primarily for Ubuntu, I chose to post here as I found the solution for the "Lock Screen" button here that I was able to get to work with Fedora.

---

