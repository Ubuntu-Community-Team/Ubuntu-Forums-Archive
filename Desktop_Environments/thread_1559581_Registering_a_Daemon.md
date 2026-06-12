---
title: "Registering a Daemon"
date: 2010-08-23
forum: Desktop Environments
---

### Post by DeathRabbit on 2010-08-23
Hey guys, what's the best way to register a daemon to start up at boot time in lucid? I have tried registering the following script using "sudo update-rc.d"```
#!/bin/bash
#Start/stop opentftpd
#Originally Contributed by sharne, slightly modified.
#######################################################################################################
#######################################################################################################
## This file daemonizes the opentftpd to start automatically when system starts
##
## Please do the following (todo)
##
##  1) Add the following lines to /etc/rc.d/rc.inet2, at the end. Alternatively You can also add
##     these lines to rc.local or inittab files.
##
##    # Start the opentftp daemon:
##    if [ -x /etc/rc.d/rc.opentftp ]; then
##      /etc/rc.d/rc.opentftp start
##    fi
##
##  2) Modify the opentftpd_start() function in line 29 below, setting the file locations.
##
##  3) Change the permissions of this file rc.opentftp to 755 after installing it in /etc/rc.d
##
#######################################################################################################
#######################################################################################################
pidnum=$( ps -eaf | grep -v grep | grep -v rc.opentftp | grep opentftpd | awk '{ printf("%s %s\n",$3,$2) }' | sort | head -1 | awk '{ print $2 }' )

# Start opentftp:
opentftpd_start() {
##### Modify line below for location of executive and other files #####
/home/lab/Desktop/opentftp/opentftpd -i /etc/opentftpd.ini -l /home/lab/Desktop/opentftp/opentftpd.log
echo "Server opentftpd started"
}

# Stop opentftp:
opentftpd_stop() {
kill $pidnum  
while [ true ]
do
pidnum=$( ps -eaf | grep -v grep | grep -v rc.opentftp | grep opentftpd | awk '{ print $2 }' | head -1 )
if [ -z "$pidnum" ]
then
break
fi
done
echo "Server opentftp stopped"
}

case "$1" in
'start')
if [ -z "$pidnum" ]
then
opentftpd_start
RETVAL=0
else
echo "Server opentftp is already running - Try restart"
RETVAL=1
fi
;;
'stop')
if [ -z "$pidnum" ]
then
echo "Server opentftp is not running"
RETVAL=1
else
opentftpd_stop
RETVAL=0
fi
;;
'restart')
if [ -z "$pidnum" ]
then
echo "Server opentftp is not running"
opentftpd_start
else
opentftpd_stop
opentftpd_start
fi
RETVAL=0
;;
'status')
if [ -z "$pidnum" ]
then
echo "Server opentftp is not running"
RETVAL=1
else
echo "Server opentftp is running - Pid : $pidnum"
RETVAL=0
fi
;;
*)
echo "Usage $0 { start | stop | restart | status }"
RETVAL=1
;;
esac
exit $RETVAL

# Enjoy!
```

This is supposed to get the daemon for opentftp started, but it does nothing, although I can see the results of the  "echo 'Server opentftpd started' " in the boot log in /var/log .Any thoughts or general help on what the best way to accomplish such a task is? Anybody done this with opentftp before? Thanks.

---

### Post by DeathRabbit on 2010-08-24
Just for kicks and grins, I tried using the "Startup Applications" utility in the system menu. As I expected, no luck.:(

---

