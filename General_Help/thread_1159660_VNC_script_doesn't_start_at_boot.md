---
title: "VNC script doesn't start at boot"
date: 2009-05-14
forum: General Help
---

### Post by chuugokujin on 2009-05-14
Hi,
Every time I want to connect my ubuntu server after reboot, I have to manually run vncserver command on it. So I googled a script and put it under /etc/init.d/vncserver and chmod +x. However, I tried to reboot and it didn't work. It works when I manually put "/etc/init.d/vncserver start" though.

Could anyone help me?

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="mythtv"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="16"

# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
GEOMETRY="1024x768"
#GEOMETRY="1280x1024"

# The name that the VNC Desktop will have.
NAME="my-vnc-server"

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

---

### Post by KhurramM on 2009-05-14
Put this command:

/etc/init.d/vncserver start

in crontab:

@reboot /etc/init.d/vncserver start

Insha-Allah, this will help s u.

---

### Post by chuugokujin on 2009-05-16
> **KhurramM said:**
> Put this command:

/etc/init.d/vncserver start

in crontab:

@reboot /etc/init.d/vncserver start

Insha-Allah, this will help s u.

I crontab -e to make a file and put the command in.
However I reboot and it didn't work.
Looks like the file is saved under /tmp, is it the right place?

---

### Post by FIONEX on 2009-05-16
Don't do cron - there's no need for it really.  It would work but there's a more proper way to do it.


Put your file under /etc/init.d/YOURFILENAME
then do this:
sudo ln -s /etc/init.d/YOURFILENAME /etc/rc2.d/S99YOURFILENAME

Basically the S99 is to make sure it Starts (capital S is important).  The 99 is to run it last.  And YOURFILENAME can be anything you want.

---

### Post by chuugokujin on 2009-05-16
> **FIONEX said:**
> Don't do cron - there's no need for it really.  It would work but there's a more proper way to do it.


Put your file under /etc/init.d/YOURFILENAME
then do this:
sudo ln -s /etc/init.d/YOURFILENAME /etc/rc2.d/S99YOURFILENAME

Basically the S99 is to make sure it Starts (capital S is important).  The 99 is to run it last.  And YOURFILENAME can be anything you want.

Thanks for reply, I did this:
sudo ln -s /etc/init.d/vncserver /etc/rc2.d/S99vncserver

This is good, I can finally connect it after reboot without log in.
but there is a new problem, you can connect but u can't see the desktop. the graphic is totally spotted and you can only see your mouse as a big X.

However, I manually sudo /etc/init.d/vncserver restart, then it will work.

Anything wrong?

---

### Post by l3iodeez on 2009-06-18
I am experiencing the exact same problem. I was able to get VNC to autostart on boot using basically the technique above with a different script. I am getting the same grey screen with the X cursor. I know I fixed this problem once before but I can't remember what I did.

---

