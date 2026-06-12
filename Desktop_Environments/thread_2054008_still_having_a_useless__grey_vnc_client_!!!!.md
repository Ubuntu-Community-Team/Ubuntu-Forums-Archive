---
title: "still having a useless  grey vnc client !!!!"
date: 2012-09-06
forum: Desktop Environments
---

### Post by sunsei on 2012-09-06
Have the settings below on my ubuntu 10.04 64bits:
----------
admin@serv:~$ cat /etc/init.d/vncserver
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     3 4 5
# Default-Stop:      0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="admin"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="16"

# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
#GEOMETRY="1024x768"
GEOMETRY="1280x1024"

# The name that the VNC Desktop will have.
NAME="serv"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in
start)
log_action_begin_msg "Starting vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;

stop)
log_action_begin_msg "Stoping vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;

restart)
$0 stop
$0 start
;;
esac

exit 0
-------------------------------------------------

admin@serv:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/tightvncserver -geometry 1280x1024

exit 0

admin@serv:~$
--------
admin1@conf:~$ cat .vnc/xstartup
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &
gnome-session &
admin1@conf:~$


--------
     I tried to follow many website's instructions  (such as [http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot](http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot)) in order to configure  "Ultravnc viewer" on a windows vista system (with an intel integrated  graphics card with 32bits color/ 1280x800 / 59HTZ)  in order to manage  an ubuntu 10.04 64bits system  (the desktop amd64 bits install from the  main ubuntu repository).
 went through all the steps but I still have a grey screen on ultravnc viewer which blocks me from using the tool??
 tried to install other tools (clients) such as VNC viewer and tightvnc viewer ,but they all end up with a grey interface!!!
I tried different settings " geometry 800x600/1280x1024/1024x768" ,but still stuck with this grey screen!!


 Any suggestions please??

---

### Post by sunsei on 2012-09-07
I'm strained by this inconvenience since I have to go in front of the console in a different room every time I have to check/change something on the system!!

> **sunsei said:**
> Have the settings below on my ubuntu 10.04 64bits:
----------
admin@serv:~$ cat /etc/init.d/vncserver
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     3 4 5
# Default-Stop:      0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="admin"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="16"

# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
#GEOMETRY="1024x768"
GEOMETRY="1280x1024"

# The name that the VNC Desktop will have.
NAME="serv"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in
start)
log_action_begin_msg "Starting vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;

stop)
log_action_begin_msg "Stoping vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;

restart)
$0 stop
$0 start
;;
esac

exit 0
-------------------------------------------------

admin@serv:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/tightvncserver -geometry 1280x1024

exit 0

admin@serv:~$
--------
admin1@conf:~$ cat .vnc/xstartup
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &
gnome-session &
admin1@conf:~$


--------
     I tried to follow many website's instructions  (such as [http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot](http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot)) in order to configure  "Ultravnc viewer" on a windows vista system (with an intel integrated  graphics card with 32bits color/ 1280x800 / 59HTZ)  in order to manage  an ubuntu 10.04 64bits system  (the desktop amd64 bits install from the  main ubuntu repository).
 went through all the steps but I still have a grey screen on ultravnc viewer which blocks me from using the tool??
 tried to install other tools (clients) such as VNC viewer and tightvnc viewer ,but they all end up with a grey interface!!!
I tried different settings " geometry 800x600/1280x1024/1024x768" ,but still stuck with this grey screen!!


 Any suggestions please??

---

### Post by steeldriver on 2012-09-07
Hi I've never set up the server to run in that mode, however my first guess would be that the problem is your client config - in particular if it is defaulting to a 3d (compiz) gnome-session then you will likely get exactly the grey screen behavior that you are describing (VNC doesn't seem to handle compiz properly right now)

Try the ~/.vnc/startup file from this page (scroll down to 'Customizing your session')

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

or at least change your current startup file so that it is sure to select a 2d session

```
gnome-session** --session=ubuntu-2d **&
```

Let us know if that helps

---

### Post by sunsei on 2012-09-08
Thank you Steeldriver for your enlightenment
the procedure in: [https://help.ubuntu.com/community/VNC/Servers?action=show&redirect=VNCServer](https://help.ubuntu.com/community/VNC/Servers?action=show&redirect=VNCServer)
 worked, but then i got a problem when I rebooted the system ??
I noticed that when I launch #vncserver from my root profil, I got a clear window from my vnc client.
so I copied my .vnc/xstartup file (see below) from my root account to the other account that vncserver uses.
_______--
#!/bin/sh
unset SESSION_MANAGER
sh /etc/X11/xinit/xinitrc
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
______________________

And Its working! (it was a real pain in the ...)
:lolflag:

NB: Still have the error below
[EMAIL="admin@serv:~/.vnc"]admin@serv:~/.vnc[/EMAIL]$ vncserver
xauth:  /var/run/gdm/auth-for-admin-IEycTV/database not writable, changes will be ignored
xauth:  error in locking authority file /var/run/gdm/auth-for-admin-IEycTV/database

New 'X' desktop is serv:1
--------------------------
Is this problem serious / is it going to impede my remote connections??

---

