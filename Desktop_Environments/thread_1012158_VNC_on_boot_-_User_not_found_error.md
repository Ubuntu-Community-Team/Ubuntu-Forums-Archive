---
title: "VNC on boot - User not found error"
date: 2008-12-15
forum: Desktop Environments
---

### Post by sideshowmel on 2008-12-15
I followed instructions at the link below for multiple VNC sessions on bootup.  This procedure worked fine in Debian Etch 4.0, and I just installed Ubuntu 8.10 for some other reasons, but I can't get this working on 8.10.  I basically copied the files verbatim from my old Debian machine, so I'm not sure why I'm getting these errors.  I've attached the errors and the init scripts being run.

[http://colinux.wikia.com/wiki/VNC_On_Bootup]("http://colinux.wikia.com/wiki/VNC_On_Bootup")

here's the init script:

root@kaya:/var/log# cat /etc/init.d/vncstart
shows this:
```
#! /bin/sh
# Multiple VNC Servers added by Max Gaukler
# Modified by Alfonso Reyes (07MAY06) to allow multiple servers for multiple users
# Comment the USER assignment because we need multiple users
# export USER="root"
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/var/run/vncserver"
NAME="vncstart"

#Add all your users:
USER[1]="towlie"
USER[2]="fun"
#USER[3]="janet"
# add more as required ...

#VNCPARAMS: set your parameters here:
VNCPARAMS[1]="-name ${USER[1]} -geometry 1024x768 -localhost"
VNCPARAMS[2]="-name ${USER[2]} -geometry 1024x768 -localhost"
#VNCPARAMS[3]="-name ${USER[3]}"
# add more as required ...

start()
{
        for ((num=1; $num <= ${#VNCPARAMS[*]}; num=$num+1));
        do
                # one new environment per user
                export USER=${USER[$num]}
                # some messages
                echo Applying to user: ${USER[$num]}
                echo these parameters: ${VNCPARAMS[$num]}
                # start individual VNC server session for every user
                su ${USER[$num]} -c "vncserver ${VNCPARAMS[$num]} :$num"
        done
}
stop()
{
        for ((num=1; $num <= ${#VNCPARAMS[*]}; num=$num+1));
        do
                # stop the VNC server sessions for all users
                su ${USER[$num]} -c "vncserver -clean -kill :$num"
        done
}
case "$1" in
    start)
        echo -n "Starting Xvnc servers: "
        start
        ;;
    stop)
        echo -n "Stopping Xvnc "
        stop
        ;;
    restart)
        echo -n "Restarting Xvnc "
        stop
        start
        ;;
****)
        echo "Usage: /etc/init.d/$NAME {start|stop|restart}"
        exit 1
        ;;
esac
exit 0

```

This is what I get when I try to run the init script (the two users listed DO exist on the system, and have passwords enabled for each account).
```
root@kaya:/var/log# /etc/init.d/vncstart restart
/etc/init.d/vncstart: 10: USER[1]=towlie: not found
/etc/init.d/vncstart: 11: USER[2]=fun: not found
/etc/init.d/vncstart: 16: Bad substitution

```

I'm not getting anything in syslog or messages. Also, here is the xstartup file for user "towlie" located at "/home/towlie/.vnc"
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP
Desktop" &
gnome-session &

```

So why would it be telling me User Not Found? It's a mystery... I mucked with this for a wihle to get it working in Debian Etch, so I'm thinking there's something I'm missing, hence this post.  Help is appreciated... I prefer this route for VNC for several reasons, but if I have to go one of the other routes in the forum I might look into that, but as far as I know, to enable VNC to start an X session automatically on bootup, this is the only way I know how. Thanks.

---

### Post by sideshowmel on 2008-12-15
UPDATE:
Just FYI, I'm currently remote over SSH, and just for giggles, I did:

```
# su towlie
$ vncserver
```

and it appears to work fine.  So really the only thing I have left is: how do I make it do that automatically on bootup? and for 2 users instead of just 1? Thanks.

---

### Post by sideshowmel on 2008-12-15
===========RESOLVED=================

I just learned that Ubuntu doesn't use bash as the default shell.  Who knew? I thought this whole time I was troubleshooting a VNC-specific issue!  Changing from #!/bin/sh to #!/bin/bash fixed my problem!  Learn something new everyday...

```
#!/bin/bash
# Multiple VNC Servers added by Max Gaukler
# Modified by Alfonso Reyes (07MAY06) to allow multiple servers for multiple users
# Comment the USER assignment because we need multiple users
# export USER="root"
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/var/run/vncserver"
NAME="vncstart"

#Add all your users:
USER[1]="towlie"
USER[2]="fun"
#USER[3]="janet"
# add more as required ...

#VNCPARAMS: set your parameters here:
VNCPARAMS[1]="-name ${USER[1]} -geometry 1024x768 -localhost"
VNCPARAMS[2]="-name ${USER[2]} -geometry 1024x768 -localhost"
#VNCPARAMS[3]="-name ${USER[3]}"
# add more as required ...

start()
{
        for ((num=1; $num <= ${#VNCPARAMS[*]}; num=$num+1));
        do
                # one new environment per user
                export USER=${USER[$num]}
                # some messages
                echo Applying to user: ${USER[$num]}
                echo these parameters: ${VNCPARAMS[$num]}
                # start individual VNC server session for every user
                su ${USER[$num]} -c "vncserver ${VNCPARAMS[$num]} :$num"
        done
}
stop()
{
        for ((num=1; $num <= ${#VNCPARAMS[*]}; num=$num+1));
        do
                # stop the VNC server sessions for all users
                su ${USER[$num]} -c "vncserver -clean -kill :$num"
        done
}
case "$1" in
    start)
        echo -n "Starting Xvnc servers: "
        start
        ;;
    stop)
        echo -n "Stopping Xvnc "
        stop
        ;;
    restart)
        echo -n "Restarting Xvnc "
        stop
        start
        ;;
****)
        echo "Usage: /etc/init.d/$NAME {start|stop|restart}"
        exit 1
        ;;
esac
exit 0

```

Hopefully this helps out somebody down the road...

---

