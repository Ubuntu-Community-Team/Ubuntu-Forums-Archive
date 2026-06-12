---
title: "Is notify-osd working with Compiz in 16.10?"
date: 2017-01-17
forum: Desktop Environments
---

### Post by Taemojitsu on 2017-01-17
(Copied from askubuntu.com)

I recently upgraded to 16.10. notify-osd, which shows  volume or screen brightness changes when using a keyboard hotkey, is not  working. It isn't running, and when I try to launch it (for me it's at '/usr/lib/x86_64-linux-gnu/notify-osd'), I get this error message:


  ** (notify-osd:7147): WARNING **: Another instance has already registered org.freedesktop.Notifications


  ** (notify-osd:7147): WARNING **: Could not register instance


  If you prefix the file name with 'dbus-launch', it won't give an error, but notifications still don't show up. Edit: this time it did give an error:

** (notify-osd:32195): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

 ...but that could be because I moved /usr/share/dbus-1/services/org.freedesktop.Notifications.service to see what would happen? However, I also get this message when starting Totem from command line yet Totem runs properly, so it might be the result of uninstalling some other package.


  Unity is the default interface (desktop manager?) for Ubuntu, not  Compiz. Are other people using Compiz in 16.10 encountering this  problem?


  Additional information: I have uninstalled some packages due to a  lack of space. I was previously using the outdated 15.10 installation,  in which notify-osd would start working with compiz if I [killed another notification program]("http://askubuntu.com/questions/367961/no-notifications-from-notify-osd-on-13-10")  that was automatically started (that didn't show volume changes). After  upgrading to 16.04, notify-osd was working (in Compiz) without having  to kill the other program. I didn't check if it was working in 16.10  before I uninstalled some programs. I tried reinstalling the programs I  uninstalled, but notify-osd still didn't work. I didn't reinstall some  programs that seemed irrelevant like ones about document printing.


  Even with notify-osd not working in Compiz, it does work if I log in  with the "Unity" default interface. (The main reasons I don't use it are  the system-monitor applet I can put on the GNOME panel, and being able  to zoom in with Compiz.) That is, notifications show up as expected, and  the 'notify-osd' process is running. Logging in with just the Gnome  desktop manager has a different way of displaying volume changes that  doesn't use notify-osd; metacity has the same problem as compiz.


I should note that  'notify-send test' causes the message to show up  in a white bubble, same colour as a 'lack of disk space' message. But  there's still no 'notify-osd' process, and 'cat /usr/share/dbus-1/services/org.freedesktop.Notifications.service'  lists notify-osd if that's important. If logging in with Unity,  notifications including volume have a dark background as in previous  versions of Ubuntu. So maybe there is a notification service running,  but what is it and how do I disable it since it doesn't show volume  changes?

     

Not sure if I tagged this right as 'gnome', should it be 'UbuntuGnome'? This is Ubuntu+Gnome+Compiz.

---

