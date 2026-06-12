---
title: "Procon for BattleField 4 hosting"
date: 2014-04-05
forum: Gaming &amp; Leisure
---

### Post by russ2 on 2014-04-05
Hey guys,

I am trying to host a procon layer that will allow me to moderate a game server and also allow members of my community to log into it as well.  The procon is a windows based program and it uses mono to run.  I have installed mono and I can get the program to run using a command line in terminal or putty.  The developer also created a script that allows the system to start the program upon server reboot or to use an /etc/init.d/procon start command.  I have set the program file location permissions to 777 and chmod the /etc/init.d/procon.  When I attempt to issue the start command I get this error:

> 
Executing /etc/init.d/procon start ..
 
/bin/sh: /etc/init.d/procon: /: bad interpreter: Permission denied

Here is the script that I use to start the program:
> 
#! / Bin / sh# # # BEGIN INIT INFO
# Provides: Procon server installation
# Required-Start: $ network $ local_fs
# Required-Stop: $ remote_fs $ local_fs
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Procon Service
# Description: Procon is an administration software for games
# # # END INIT INFO

# # # # # # Script Name
NAME = procon

# # # Script name with path # # #
SCRIPT NAME = / etc / init.d / $ NAME

# # # # # # Procon main directory
HOME = / home/procon/procon_1.4.0.6

# # # Procon perform the following user root is not recommended to get # # #
USER = procon

# # # # # # Script description
DESC = "Procon Frostbite"

do_start () {
  su $ USER-c "cd $ HOME; mono-service2-l / proconservice.lock PRoCon.Service.exe."
}

do_stop () {
  su $ USER-c "kill` cat $ HOME / proconservice.lock `"
}

case "$ 1" in
    start)
        if [$ USER = "root"] then
            echo WARNING! As a safety: DO NOT THROW YOUR SERVER TO PROCON ROOT..
            c = 1
            while ["$ c"-le 10] do
                echo-n "!"
                sleep 1
                c = $ ((+ + c))
            done
            echo "!"
        fi
        echo "Starting $ DESC"
        do_start
        ;;
    stop)
        echo "Stopping $ DESC"
        do_stop
        ;;
    restart)
        echo "Stopping $ DESC"
        do_stop
        sleep 3
        echo "Starting $ DESC"
        do_start
        ;;
    *)
        echo "Usage: $ SCRIPT NAME {start | stop | restart}"
esac
 exit 0

I am not any good at writing scripts as of yet.  Still need to learn how to.  If anybody can take a look and see if there any errors or typos,
it would be greatly appreciated.

Thank you

---

