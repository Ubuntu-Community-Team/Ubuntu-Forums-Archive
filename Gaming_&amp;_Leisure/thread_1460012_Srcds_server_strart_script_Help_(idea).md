---
title: "Srcds server strart script Help (idea)"
date: 2010-04-22
forum: Gaming &amp; Leisure
---

### Post by zhelev81 on 2010-04-22
Hello,i'm looking for some help to debug my server.

I have Counter Strike source server (srcds) and i need to start it with different user than root in a named screen + running in gdb to find out what is causing it to crash and hang so often.

Can someone write for me a script that will help me 

1. Start in screen (with the server name)

2. run in gdb ,and as soon as the server crash or hang to print the "bt" to a log file 

3. Quit and reastart the server in gdb again 

can someone help me how to do this ?

---

### Post by zhelev81 on 2010-04-22
no one knows ? :(

---

### Post by dfreer on 2010-04-22
```
#!/bin/sh
# Source Dedicated Server Init Script

# Server options
TITLE='Source Dedicated Server' 	# Script initialization title
LONGNAME='CAL MATCH SERVER CS:S'        		# Full title of game type
NAME='cssmatch'                          # Server handle for the screen session
DAEMON='RESTART_srcds_run'                # The server daemon
STEAM='/usr/local/games/steam/cssmatch'        # STEAM to Steam installation
USER='cssgamer'

# Game options
IP='192.168.1.101'                # IP of the server
PORT='27017'                    # Port number to
MAP='de_dust2'                    # Initial map to start
GAME='cstrike'                        # Game type (tf|cstrike|valve|hl2mp)
SIZE='10'                        # Maximum number of players

# Server options string
OPTS="-game $GAME -console +map $MAP -ip $IP -port $PORT \
    +maxplayers $SIZE -pidfile $STEAM/$GAME/$NAME.pid -tickrate 100 +fps_max 0"

# Screen command
INTERFACE="/usr/bin/screen -A -m -d -S $NAME"

service_start() {
    # Check if the pid files currently exist
    if [ ! -f $STEAM/$GAME/$NAME.pid ] && [ ! -f $STEAM/$GAME/$NAME-screen.pid ]; then
        if [ -x $STEAM/$DAEMON ]; then
            echo "Starting $TITLE - $LONGNAME on $(date)"
            echo "Server IP: $IP"
            echo "Server port: $PORT"
            echo "Server size: $SIZE players"
            cd $STEAM
            $INTERFACE sudo -u cssgamer $STEAM/$DAEMON $OPTS
            # Prevent race condition on SMP kernels
             sleep 1
            # Find and write current process id of the screen process
            ps -ef | grep SCREEN | grep "$NAME" | grep -v grep | awk '{ print $2}' > $STEAM/$GAME/$NAME-screen.pid
            echo "$TITLE screen process ID written to $STEAM/$GAME/$NAME-screen.pid"
            echo "$TITLE server process ID written to $STEAM/$GAME/$NAME.pid"
            
            echo "$TITLE started."
        fi
    else
        echo -e "Cannot start $TITLE.  Server is already running."
        #exit 1
    fi
}

service_stop() {
    if [ -f $STEAM/$GAME/$NAME.pid ] && [ -f $STEAM/$GAME/$NAME-screen.pid ]; then
        echo "Stopping $TITLE..."
        # Get the process ID from the pid file we created earlier
        for id in `cat $STEAM/$GAME/$NAME-screen.pid`
            do kill -9 $id
            echo "Killing process ID $id"
            echo "Removing $TITLE - $LONGNAME screen pid file"
            rm -rf $STEAM/$GAME/$NAME-screen.pid
            break
        done
        # Remove server pid file
        echo "Removing $TITLE pid file"
        rm -rf $STEAM/$GAME/$NAME.pid
        # Wipe all old screen sessions
        screen -wipe 1> /dev/null 2> /dev/null
        echo "$TITLE stopped."
    else
        echo -e "Cannot stop $TITLE.  Server is not running."
        #exit 1
    fi    
}    

service_update() {
    service_stop
    sleep 1
    # Prepend -autoupdate to the rest of the options
    	OPTS="-autoupdate $OPTS"
    service_start
}

case "$1" in
    'start')
        service_start
        ;;
    'stop')
        service_stop
        ;;
    'restart')
        service_stop
        sleep 1
        service_start
        ;;
    'update')
        service_update
	;;

    *)
        echo "Usage $0 start|stop|restart|update"
esac

```

This should get you halfway there, it starts SRCDS as a different user using sudo, and launches it under a screen session. I've never used gdb myself so I dunno what commands you need to use it, but hopefully this will help.

---

### Post by dfreer on 2010-04-23
Ok, so here's what I've got so far:

First, you'll want a modified srcds_run bash script. Why modified? Because the default script (as of approx 2008 when I was running SRCDS) failed to correctly restart the server after it crashes. I've attached my copy, renamed to "RESTART_srcds_run". 

The only differences between this and the original (besides 2 lines where it adds HTML tags to a website and email address) is the following section:
srcds_run
```
	if test -n "$RESTART" ; then
		**echo "Server will auto-restart if there is a crash."**


		#loop forever
		while true
		do
			# Update if needed
			update

			# Run the server
			$HL_CMD
			retval=$?
			[B]if test $retval -eq 0 && test -z "$AUTO_UPDATE"; then
				break; # if 0 is returned then just quit
			fi[/B]

			debugcore $retval

			echo "`date`: Server restart in $TIMEOUT seconds"

			# don't thrash the hard disk if the server dies, wait a little
			sleep $TIMEOUT
		done # while true 
	else
```

RESTART_srcds_run
```
    if test -n "$RESTART" ; then

        echo "Auto-restarting the server on crash"

        #loop forever
        while true
        do
            # Update if needed
            update

            # Run the server
            $HL_CMD
            retval=$?




            debugcore $retval

            echo "`date`: Server restart in $TIMEOUT seconds"

            # don't thrash the hard disk if the server dies, wait a little
            sleep $TIMEOUT
        done # while true
    else
```

I got this *somewhere* on the internet (probably the srcds forums), don't quite know what it changes. As far as I can tell, it removes a check to see if autoupdate argument has been set and if a debug core dump has been made. Now it just restarts no matter what IIRC.

Ok, so that will allow SRCDS to restart upon crashes. Now, as for running gdb and as a different user using screen:

You'll want to make sure that the user has the appropriate permissions and ownership of your steam installation folder, which I believe you already did via our discussion on skype. Assuming your username to be firegate, then to run it once you could do the following:
```
sudo -u firegate screen -A -m -d -S debugsrcds gdb RESTART_srcds_run
(gdb) -> run -game cstrike -console +map de_dust2 +maxplayers 20 -tickrate 66
```

And do what you need to do.

As for a script to do all of this as a system service or daemon, here's one I use to use modified to debug:
```
#!/bin/sh
# Source Dedicated Server Init Script
# Customized by Daniel A. Freer
# Original Author Unknown
# Provides an additional service command to run SRCDS in the gdb debugger

### MODIFY THIS SECTION AS NEEDED ###
# Server options
TITLE='Source Dedicated Server' 	# Script initialization title
LONGNAME='CAL MATCH SERVER CS:S'        		# Full title of game type
NAME='cssmatch'                          # Server handle for the screen session
DAEMON='RESTART_srcds_run'                # The server daemon/executable file
STEAM='/usr/local/games/steam/cssmatch'        # Path to Steam installation
USER='firegate'								# User to run SRCDS under
DEBUG_FILE="/var/log/srcds/$NAME.log"		# Debug Filename

# Game options
IP='192.168.1.101'                # IP of the server
PORT='27015'                    # Port number to
MAP='de_dust2'                    # Initial map to start
GAME='cstrike'                        # Game type (tf|cstrike|valve|hl2mp)
SIZE='10'                        # Maximum number of players

# Server options string
OPTS="-game $GAME -console +map $MAP -ip $IP -port $PORT \
    +maxplayers $SIZE -pidfile $STEAM/$GAME/$NAME.pid -tickrate 100 +fps_max 0"

# Screen command
INTERFACE="/usr/bin/screen -A -m -d -S $NAME"
### DO NOT MODIFY FURTHER ###


service_start() {
    # Check if the pid files currently exist
    if [ ! -f $STEAM/$GAME/$NAME.pid ] && [ ! -f $STEAM/$GAME/$NAME-screen.pid ]; then
        if [ -x $STEAM/$DAEMON ]; then
            echo "Starting $TITLE - $LONGNAME on $(date)"
            echo "Server IP: $IP"
            echo "Server port: $PORT"
            echo "Server size: $SIZE players"
            cd $STEAM
            $INTERFACE sudo -u $USER $STEAM/$DAEMON && run $OPTS
            # Prevent race condition on SMP kernels
             sleep 1
            # Find and write current process id of the screen process
            ps -ef | grep SCREEN | grep "$NAME" | grep -v grep | awk '{ print $2}' > $STEAM/$GAME/$NAME-screen.pid
            echo "$TITLE screen process ID written to $STEAM/$GAME/$NAME-screen.pid"
            echo "$TITLE server process ID written to $STEAM/$GAME/$NAME.pid"
            
            echo "$TITLE started."
        fi
    else
        echo -e "Cannot start $TITLE.  Server is already running."
        #exit 1
    fi
}

service_stop() {
    if [ -f $STEAM/$GAME/$NAME.pid ] && [ -f $STEAM/$GAME/$NAME-screen.pid ]; then
        echo "Stopping $TITLE..."
        # Get the process ID from the pid file we created earlier
        for id in `cat $STEAM/$GAME/$NAME-screen.pid`
            do kill -9 $id
            echo "Killing process ID $id"
            echo "Removing $TITLE - $LONGNAME screen pid file"
            rm -rf $STEAM/$GAME/$NAME-screen.pid
            break
        done
        # Remove server pid file
        echo "Removing $TITLE pid file"
        rm -rf $STEAM/$GAME/$NAME.pid
        # Wipe all old screen sessions
        screen -wipe 1> /dev/null 2> /dev/null
        echo "$TITLE stopped."
    else
        echo -e "Cannot stop $TITLE.  Server is not running."
        #exit 1
    fi    
}    

service_debug() {
	service_stop
	sleep 1
	# Prepend -debug and -debugfile to rest of options
		OPTS="-debug -debuglog $DEBUG_FILE $OPTS"
	service_start
}

service_update() {
    service_stop
    sleep 1
    # Prepend -autoupdate to the rest of the options
    	OPTS="-autoupdate $OPTS"
    service_start
}

case "$1" in
    'start')
        service_start
        ;;
    'stop')
        service_stop
        ;;
    'restart')
        service_stop
        sleep 1
        service_start
        ;;
	'debug')
		service_debug
		;;
    'update')
        service_update
	;;

    *)
        echo "Usage $0 start|stop|restart|debug|update"
esac

```

I've also attached it. You'll want to change the variables at the top, because I don't know for sure where your installation is. You'll also want to change the game options as needed, like maxplayers and default map etc.

To install the script:
```
sudo cp cssdebug /etc/init.d/
sudo update-rc.d cssdebug defaults
```

To start the script:
```
sudo /etc/init.d/cssdebug start
```

To start the debug just replace start with debug. It controls otherwise like a normal daemon with start/stop/restart/update commmands. It should automatically run a BT and dump a log file for you in /var/log/srcds/ by default, you can change this in the configuration section.

EDIT: O yeah, you need to add your user firegate to the sudoers file to allow him to run the script IIRC. you can limit it so the only file he can execute is the init script. I believe i did this because my user had no password or something, we will see if you actually need it.

---

