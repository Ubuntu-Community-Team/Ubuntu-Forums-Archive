---
title: "Autorun x0vnc4server after user login"
date: 2016-04-12
forum: Desktop Environments
---

### Post by CrewDK on 2016-04-12
Hey. I'm running Xubuntu  14.04 with installed vnc4server. In my /etc/init.d/ i created script which starts x0vnc4server. 

```
#!/bin/sh
### BEGIN INIT INFO
# Provides: vnc0
# Required-Start: $all
# Required-Stop: $all
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: vnc4launcher
# Description:
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

USER=`ps aux | grep xfce4-session | grep -v grep | awk '{print $1}'`
ADDR=`ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | cut -d: -f2 | awk '{printf $1"\n"}'`

# The display that VNC will use
DISPLAY="0"

OPTIONS="-display :${DISPLAY} -PasswordFile ~/.vnc/passwd"

. /lib/lsb/init-functions

case "$1" in

start)
    log_action_begin_msg "Starting vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
    su ${USER} -c "x0vnc4server ${OPTIONS} &"
    ;;

stop)
    log_action_begin_msg "Stoping vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
    killall x0vnc4server
    ;;

restart)
    $0 stop
    $0 start
    ;;
*)
    echo "Usage: /etc/init.d/vnc4 {start|stop|restart}"
    exit 1
esac

exit 0
```

If i running it manualy after user login - it works like charm. But is there any way to autorun this script after user login into XFCE?

---

### Post by CrewDK on 2016-04-13
Nvm. Working solution. This script installs and sets up vnc4 server with autostart right services with or without user logon, and with opportunity to connect to remote host with dispaly :1+ and with display :0. 

```
#!/bin/bash

############################
## &#1055;&#1077;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1099;&#1077;

PASS=12345678
#USER=crew

###########################
## &#1059;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1077; &#1080; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072;

apt-get purge vino -y
apt-get install vnc4server -y

##########################
## &#1056;&#1072;&#1089;&#1082;&#1080;&#1076;&#1099;&#1074;&#1072;&#1077;&#1084; &#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1080; &#1080; &#1087;&#1072;&#1088;&#1086;&#1083;&#1080; &#1085;&#1072; &#1074;&#1089;&#1077;&#1093; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1077;&#1081;

for h in `ls /home | grep -v "lost+found" |  grep -v iso | grep -v grep`;
    do
    mkdir -p /home/${h}/.vnc/
    echo -e "${PASS}\n${PASS}\n\n" | vncpasswd /home/${h}/.vnc/passwd 2>&1 > /dev/null

    cat <<- "EOF" > /home/${h}/.vnc/xstartup
        #!/bin/bash
        # Uncomment the following two lines for normal desktop:
        unset SESSION_MANAGER
        exec /etc/X11/xinit/xinitrc
        [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
        [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
        #xsetroot -solid grey
        #vncconfig -iconic &
        #xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
        #twm &
    EOF

    chmod +x /home/${h}/.vnc/xstartup
    chown -R ${h}: /home/${h}/.vnc/
    done

##########################
## &#1050;&#1086;&#1087;&#1080;&#1088;&#1091;&#1077;&#1084; &#1074; &#1088;&#1091;&#1090;&#1072; &#1080; &#1074; &#1089;&#1082;&#1077;&#1083;&#1077;&#1090;
cp -R /home/crew/.vnc/ /root/.vnc
cp -R /home/crew/.vnc/ /etc/skel/.vnc


##########################
## &#1044;&#1077;&#1083;&#1072;&#1077;&#1084; &#1086;&#1073;&#1097;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099;&#1084; &#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;
chmod 777 /etc/X11/xinit/xinitrc

#########################
## &#1057;&#1086;&#1079;&#1076;&#1072;&#1105;&#1084; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1099; &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; &#1080; &#1072;&#1074;&#1090;&#1086;&#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;

#####################
# &#1076;&#1083;&#1103; display:1+


cat <<- "EOF" > /etc/init.d/vnc4
    #!/bin/sh
    ### BEGIN INIT INFO
    # Provides: vnc4
    # Required-Start: $all
    # Required-Stop: $all
    # Default-Start: 2 3 4 5
    # Default-Stop: 0 1 6
    # Short-Description: vnc4launcher
    # Description:
    ### END INIT INFO
    
    PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
    # Addres
    ADDR=`ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | cut -d: -f2 | awk '{printf $1"\n"}'`

    # The Username:Group that will run VNC
    export USER="crew"
    
    # The display that VNC will use
    DISPLAY="1"
    
    # Color depth (between 8 and 32)
    DEPTH="16"
    
    # The Desktop geometry to use.
    #GEOMETRY="x"
    #GEOMETRY="800x600"
    GEOMETRY="1200x900"
    #GEOMETRY="1280x1024"
    
    # The name that the VNC Desktop will have.
    NAME="vnc4server"
    
    OPTIONS="-name '${NAME} from ${USER}' -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"
    
    . /lib/lsb/init-functions
    
    case "$1" in
    
    start)
        log_action_begin_msg "Starting vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
        su ${USER} -c "vnc4server ${OPTIONS}"
        ;;
    
    stop)
        log_action_begin_msg "Stoping vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
        su ${USER} -c "vnc4server -kill :${DISPLAY}"
    #    vnc4server -kill :${DISPLAY}
        ;;
    
    restart)
        $0 stop
        $0 start
        ;;
    *)
        echo "Usage: /etc/init.d/vnc4 {start|stop|restart}"
        exit 1
    esac
    
    exit 0
EOF

chmod +x /etc/init.d/vnc4

update-rc.d vnc4 start 70 2 3 4 5 . stop 20 0 1 6 .

#####################
# &#1076;&#1083;&#1103; display 0: 

cat <<- "EOF" > /etc/init.d/vnc0
### BEGIN INIT INFO
# Provides: vnc0
# Required-Start: $all
# Required-Stop: $all
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: vnc4launcher
# Description:
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

USER=`ps aux | grep xfce4-session | grep -v grep | awk '{print $1}'`
ADDR=`ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | cut -d: -f2 | awk '{printf $1"\n"}'`

# The display that VNC will use
DISPLAY="0"

OPTIONS="-display :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in

start)
    sleep 5
    log_action_begin_msg "Starting vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
    su ${USER} -c "x0vnc4server ${OPTIONS} -PasswordFile ~/.vnc/passwd &"
    sleep  5
    ps aux | grep x0vnc4 | grep -v grep
    if [ $? -ne 0 ]; then
        x0vnc4server ${OPTIONS} -PasswordFile ${HOME}/.vnc/passwd &
    fi
    ;;

stop)
    log_action_begin_msg "Stoping vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
    killall x0vnc4server
    ;;

restart)
    $0 stop
    $0 start
    ;;
*)
    echo "Usage: /etc/init.d/vnc0 {start|stop|restart}"
    exit 1
esac

exit 0
EOF

chmod +x /etc/init.d/vnc0

##############################
## &#1056;&#1072;&#1089;&#1082;&#1080;&#1076;&#1099;&#1074;&#1072;&#1077;&#1084; &#1074; &#1093;&#1086;&#1084;&#1103;&#1082;&#1080; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1077;&#1081;

for HM in `ls -R -a /home/ | grep autostart: | grep -v grep | rev | cut -c 2- | rev`;
    do
    cd ${HM}
    OWN=`ls -l .. | grep autostart | grep -v grep | awk '{print $3}'`
    cat <<- EOF > ${HM}/vnc0.desktop
    [Desktop Entry]
    Encoding=UTF-8
    Version=0.9.4
    Type=Application
    Name=vnc0
    Comment= 
    Exec=/etc/init.d/vnc0 start
    OnlyShowIn=XFCE;
    StartupNotify=false
    Terminal=false
    Hidden=false
    EOF
    
    chown ${OWN}: ${HM}/vnc0.desktop
    done
```


100% works for Xubuntu 14.04. IDK about other DE.

---

