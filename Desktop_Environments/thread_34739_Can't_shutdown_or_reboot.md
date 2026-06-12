---
title: "Can't shutdown or reboot"
date: 2005-05-16
forum: Desktop Environments
---

### Post by gort on 2005-05-16
Hi, I'm not sure what I did (I don't believe I did anything command line requiring root or sudo), but now when I first boot into Ubuntu it stops at the command prompt and I have to manually type in username, password, and startx to get to
the desktop. When I want to reboot or shutdown, I no longer have those options in the logout box. I have to use the terminal and give the halt command. Does anyone have an idea how to fix this?
Thanks, Gary

---

### Post by lao_V on 2005-05-16
are you using gnome with KDM as your login manager or vice versa? You will only get the the shutdown/reboot options for the DE corresponding to the login manager you used to login.

---

### Post by gort on 2005-05-16
Hi, I'm using gnome, everything is default install. All worked fine until I changed a setting somewhere!!
Thanks, Gary

---

### Post by Maestro23 on 2005-05-16
[QUOTE=gort]Hi, I'm not sure what I did (I don't believe I did anything command line requiring root or sudo), but now when I first boot into Ubuntu it stops at the command prompt and I have to manually type in username, password, and startx to get to
the desktop. When I want to reboot or shutdown, I no longer have those options in the logout box. I have to use the terminal and give the halt command. Does anyone have an idea how to fix this?
Thanks, Gary[/QUOTE]

If you didn't do anything in command line, try this from the GUI in Gnome:  [http://ubuntuguide.org/#automaticlogingnome](http://ubuntuguide.org/#automaticlogingnome)

I use Kubuntu myself, but this might work for ya...

---

### Post by stepore on 2005-05-17
[QUOTE=gort]Hi, I'm not sure what I did (I don't believe I did anything command line requiring root or sudo), but now when I first boot into Ubuntu it stops at the command prompt and I have to manually type in username, password, and startx to get to
the desktop. When I want to reboot or shutdown, I no longer have those options in the logout box. I have to use the terminal and give the halt command. Does anyone have an idea how to fix this?
Thanks, Gary[/QUOTE]
 you've probably disabled gdm and are now using xdm. 
go to /etc/init.d/ and do 'ls -la gdm' (no quotes). 
make sure it's:
-rwxr-xr-x  1 root root 2256 2005-03-28 15:37 gdm

'apt-get install rcconf' -  run rcconf and make sure gdm is a service starting with boot.

then 'dpkg-reconfigure gdm'
then either reboot or just '/etc/init.d/gdm restart

something there should fix it for ya.

---

### Post by Vin_L on 2005-05-27
How can you change your log in manager to KDE? I have the same problem and I believe it must be because I am using the Ubuntu default log in screen to login to KDE desktop. Although when i was trying the XFCE Desktop that had the reboot shutdown option from the log out.

Thanks

---

### Post by stepore on 2005-05-27
[QUOTE=Vin_L]How can you change your log in manager to KDE? I have the same problem and I believe it must be because I am using the Ubuntu default log in screen to login to KDE desktop. Although when i was trying the XFCE Desktop that had the reboot shutdown option from the log out.

Thanks[/QUOTE]
 kdm is a display manager, if that's what you mean? it'll work with kde or gnome, as will gdm.
if you don't have it and want it, then get it.
sudo apt-get install kdm
once you have it installed:
sudo dpkg-reconfigure kdm (it'll ask you if you want to use kdm or gdm)
then either reboot or just sudo /etc/init.d/kdm restart
and you'll have kdm as your display manager. whether you choose kde or gnome, that's up to you.

---

### Post by lmo on 2007-01-01
I am using xdm and there is no Shutdown or Reboot buttons. Apparently, when gnome sees that something other than gdm is the display manager, it won't allow those options. This is silly. Anyone can do ctrl-alt-F1 and then do ctrl-alt-del and reboot the system.Most people probably just turn off the power (making an awful mess.)

I did these hacks to get a shutdown option on the gnome menu. This is a script that also explains what else must be done (i.e., you must create the /usr/share/applications/Shutdown.desktop file, edit the /etc/xdg/menus/applications.menu file, and add your username to sudoers to allow shutdown with no password. Be sure to cp /etc/xdg/menus/applications.menu /etc/xdg/menus/applications.menu.bak in case you need to recover it.

Copy/paste the code to a file named shutdown.sh in /usr/bin or some place in path:
```

#!/bin/sh
# shutdown.sh
#
# SETUP
#   Modify sudoers to let non-root user shutdown:
#   sudo visudo
#   YourUsername  ALL = NOPASSWD: /sbin/shutdown
#
#   Test that xmessge is installed with "xmessage hello"
#   If not installed, install xmessage package
#
#   Copy this shutdown.sh to /usr/bin (or other location on path)
#
#   Create the following /usr/share/applications/Shutdown.desktop file:
#      [Desktop Entry]
#      Comment=Shutdown Menu
#      Name=Shutdown
#      Exec=shutdown.sh
#      Icon[en_US]=/usr/share/icons/hicolor/48x48/apps/xfsm-shutdown.png
#      Encoding=UTF-8
#      Terminal=false
#      Comment[en_US]=Shutdown Menu
#      Type=Application
#      Name[en_US]=Shutdown
#      Icon=/usr/share/icons/hicolor/48x48/apps/xfsm-shutdown.png
#      Categories=Application;
#
#   Copy /etc/xdg/menus/applications.menu 
#   to   /etc/xdg/menus/applications.menu.bak
#
#   Insert these lines below the end of System Tools Menu
#   in /etc/xdg/menus/applications.menu:
#      <Include>
#        <Filename>Shutdown.desktop</Filename>
#      </Include>
#
#
# Note: -g0 is the old way of specifying time-to-wait ... shutdown honors this
# Note: -y is the old way of specifying yes-I-mean-yes ... shutdown allows this
# Note: can substitute the word 'now' for '-g0' if desired, and the '-y' is unnecessary.
# Note: Messages apparently only sent to logged in text console screens :(
xmessage -buttons Shutdown:20,Reboot:21,Cancel:23,Test:22 -default Cancel -geometry +20-50 -bg grey90 -bd grey33 " Shutdown Menu " ;
CONTROL=$?;
case "$CONTROL" in
  20)
  sudo shutdown -g0 -y -h 
  ;;
  21)
  sudo shutdown -g0 -y -r 
  ;;
  22)
  sudo shutdown -g0 -k -h This is only a test ...
  ;;
  23)
  ;;
esac

```

After doing the work,I needed to logout and log back in to refresh the menu.

---

