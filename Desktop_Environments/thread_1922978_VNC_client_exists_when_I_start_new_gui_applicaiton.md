---
title: "VNC client exists when I start new gui applicaiton"
date: 2012-02-09
forum: Desktop Environments
---

### Post by jm23 on 2012-02-09
I am using Ubuntu 11.10 server.  I installed the desktop and can get connected from my windows box to the Ubuntu server using Real VNC 4.1.3.  Everything seems to work. However often after I have started a second application the vnc client exits. I checked with top and it seems I have enough free RAM.  

I have looked in my vnc log file in ~/.vnc/dragon:5.log and it seems the vnc server is exiting too.  See part of the log below:


09/02/12 15:44:27 Xvnc version TightVNC-1.3.9
...

** (gnome-control-center:8137): WARNING **: Could not find icon

(gnome-control-center:8137): screen-cc-panel-WARNING **: Error getting brightness: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.Power.Screen' on object at path /org/gnome/SettingsDaemon/Power

(gnome-terminal:7861): Gdk-WARNING **: gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.

(gdu-notification-daemon:8115): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.

polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.
gnome-session[7863]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.

Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':5'.

(bluetooth-applet:7992): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.


(nm-applet:7994): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.

unity-2d-panel: [WARNING] unity-2d-panel: Fatal IO error: client killed
unity-2d-launcher: [WARNING] unity-2d-launcher: Fatal IO error: client killed
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-installer", line 22, in <module>
    from gi.repository import Gtk, GLib
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module

---

### Post by deonis on 2012-02-09
if you can't connect you can always kill it.

 vncserver -kill :1

---

### Post by jm23 on 2012-02-09
I am sorry for not being clear. The issue is that the vncserver instance shuts down and this in turn closes the vnc client.  This also closes my applications in gnome. So I need to restart vncserver, client and applications.  This is not hard to reproduce, all I need to do is open firefox and just about any other application and immediately it happens.

---

### Post by deonis on 2012-02-09
My bad. I usually use tight vncserver and never had any problems with it. Don't have much experience with real vnc, though. BTW, I am using it on my desktop with Ubuntu 11.10, so it should work for you. 

cheers

---

### Post by jm23 on 2012-02-17
Any ideas on this. This problem makes the Gnome desktop useless.

This is my ~/.vnc/xstartup file:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
/usr/bin/gnome-session &

                                        1,1           All

---

### Post by jm23 on 2012-02-18
I have been trying to get this to work for some time without success.  So today I took a different approach. Since I will be connecting from a Windows7 box I decided to see if I can get remote desktop to work.  Boy was it easy. These are the steps I took:

sudo apt-get install xrdp


Then just open the remote desktop client on the windows box and connect.  It worked the first time.  There were other posts that said that you need to do the following as well. 

echo "gnome-session --session=ubuntu-2d" > .xsession
sudo /etc/init.d/xrdp restart

I will note there was one problem. When I terminate the Remote desktop on the Windows7 side and reconnect. It does not reconnect back to your session.  And I could not get back to the running applications.  In fact if I start the browser chrome once reconnecting, the browser windows does not even appear.  Even after I restarted using;
sudo /etc/init.d/xrdp restart

It still would not work.  I had to reboot the linux box in order to make things work.  

Maybe someone knows how to fix that. Anyway This works well enough for me to get work done.

---

### Post by esm2 on 2013-02-27
I hate to "me too", but I've got this problem as well with 12.04.2 xfce4 and tightvnc

everything is wonderful for awhile, the the VNC server barfs (from ~/.xsession-errors):
```
xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":8.0"
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.0.
xfce4-cpugraph-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.0.
```

my first guess was ecryptfs killing the mount or something, but I can even stay logged in via SSH and the session still eats it

---

