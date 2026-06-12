---
title: "Installing Counter Strike Source"
date: 2009-08-27
forum: Gaming &amp; Leisure
---

### Post by Strega on 2009-08-27
Hi, I got myself a linux server running Ubuntu.
Here are the specs [http://188.40.79.137/phpsysinfo/](http://188.40.79.137/phpsysinfo/)
Now, I'm trying to install a CSS server but am facing some problems.
This is what I did.

```
mkdir server1
cd server1
wget http://www.steampowered.com/download/hldsupdatetool.bin
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
./steam
./steam -command update -game "Counter-Strike Source" -dir .

```

So normally CSS would be installed right?
Then I need to add the command line, mine is this

```
./srcds_run -console -game cstrike -ip 188.40.79.137 -port 27015 -maxplayers 11 -tickrate 100 +fps_max 300 +map de_dust2 +servercfgfile server.cfg -autoupdate
```

Am I still going in the right way, because if I now add the ip address of the server to my favorites in steam it doesn't show up, and I can't connect to it when typing connect 188.40...
Is it also normal when I go to the cstrike/cfg/ directory, there isn't a server.cfg file?
Please help me out :)

Thx, Strega

---

### Post by beastrace91 on 2009-08-27
Yes it is normal for there not to be a server.cfg (you need to [create one](http://www.cstrike-planet.com/cfgmaker?cfg=srcds) yourself)

Also this is unneeded ```
+servercfgfile server.cfg
``` it is only needed if you are using a CFG file other than the server.cfg (which is executed by default if it exists)

As for it not showing up on your steam list be sure there is no hardware/software fire wall (Ubuntu does not have one by default so check your router) and be sure that the proper port(s) are open to make the server visibile.

~Jeff

---

### Post by Strega on 2009-08-27
> **beastrace91 said:**
> Yes it is normal for there not to be a server.cfg

Thank you for the quick reply.
The ports won't be a problem because the server isn't located at my home.
It's in germany :D
But there is another problem:
Recently I installed some ftp on it and made a user.
I can acces all directory's with it except for the ones in the cstrike folder.
The error is: No such file or directory.
But if I do cd cstrike I do go into the cstrike folder so there has to be one.
Any idea how to solve this problem :p ?

Thx, Strega

---

### Post by beastrace91 on 2009-08-27
Mmm, I've never had to set up FTP sorry. Perhaps check the settings with what ever you used to setup the ftp protocol on the server? And as always - Google is our friend :)

~Jeff

---

### Post by dfreer on 2009-08-27
> **Strega said:**
> Thank you for the quick reply.
The ports won't be a problem because the server isn't located at my home.
It's in germany :D
But there is another problem:
Recently I installed some ftp on it and made a user.
I can acces all directory's with it except for the ones in the cstrike folder.
The error is: No such file or directory.
But if I do cd cstrike I do go into the cstrike folder so there has to be one.
Any idea how to solve this problem :p ?

Thx, Strega

I'd check the permissions on that folder. My bet is that the FTP user account does not have read access to that folder.

I also remember on my local linux machine, that if the user does not also have execute permissions to that folder, it brings up an error as well. Not quite sure why you would need to be able to execute a folder in order to browse it but it seemed to be the case for me, perhaps this might help you.

---

### Post by Strega on 2009-08-28
Hello,

I now managed to get a server online ( thank you :D ) but...
when I close Putty the server shuts down aswell, how do I keep it running whithout me being in the programm all the time ?

Thx , Strega

---

### Post by Strega on 2009-08-28
> **Strega said:**
> Hello,

I now managed to get a server online ( thank you :D ) but...
when I close Putty the server shuts down aswell, how do I keep it running whithout me being in the programm all the time ?

Thx , Strega

There is also this problem that the server set's his port on his own.
In my command line I wrote -port 27015 but it changed to 27018.
Any idea why?

Regards, Strega

---

### Post by beastrace91 on 2009-08-28
Are there other Source servers running off of the box (Or IP adress even) using up the first three ports? I believe they auto adjust if so...

~Jeff

---

### Post by dfreer on 2009-08-28
> **beastrace91 said:**
> Are there other Source servers running off of the box (Or IP adress even) using up the first three ports? I believe they auto adjust if so...

~Jeff

+1. I know that the SRCTV port will always attempt to use port 27020; failing that it will try the next port above (27021, 27022, etc). So that is entirely possible, without knowing more details about your hosting provider it's hard to tell.

Beyond that, I typically used screen to control my CS:S servers. There are several guides on how to launch your SRCDS server with screen, here's a good one:
[http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=](http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=)

If you would like, I can include some of my init start up scripts for SRCDS (they launch your server at start up as a daemon and allows you to start/stop/restart the server as a normal linux daemon; furthermore letting you screen in to view the game console at your leisure).

---

### Post by bear24rw on 2009-08-28
off topic question but just looked at your phpsysinfo what are you caching that is taking up so much ram??

---

### Post by Strega on 2009-08-29
> **bear24rw said:**
> off topic question but just looked at your phpsysinfo what are you caching that is taking up so much ram??

I have absolutely no idea.
A friend of mine told me that the css servers would just overwrite it so there should be no problem

And I tried to run other servers on it but each time I closed Putty they shutdown again and they did have ports like 27015.
How could I "reset" them so I can use 27015 again?

And thank you for the link :D looks like a great tutorial :)

Regards, Strega

---

### Post by Strega on 2009-08-29
I now managed to get some servers online but the ports are not the one's they should be.
How could I fix that?
And what are the stop and restart command that real gamehosts use ?

Regards, Strega

---

### Post by dfreer on 2009-08-29
If you have putty access, try using top (or my favorite htop if you can install it) to see if there are any CS:S servers already running. You can also use netstat to see which processes are listening on which ports (if there's a lot, use grep to filter your results):
```

$ sudo netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:34986           0.0.0.0:*               LISTEN      2153/rpc.statd  
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2142/portmap    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2863/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      3134/exim4      
tcp6       0      0 :::80                   :::*                    LISTEN      3277/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      2863/cupsd      
udp        0      0 0.0.0.0:35745           0.0.0.0:*                           2491/avahi-daemon: 
udp        0      0 0.0.0.0:39732           0.0.0.0:*                           2153/rpc.statd  
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2506/dhclient3  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           2491/avahi-daemon: 
udp        0      0 0.0.0.0:111             0.0.0.0:*                           2142/portmap    
udp        0      0 0.0.0.0:631             0.0.0.0:*                           2863/cupsd      
udp        0      0 0.0.0.0:633             0.0.0.0:*                           2153/rpc.statd  
udp6       0      0 :::55830                :::*                                2491/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                2491/avahi-daemon:
```

I have no idea what professional game servers use, as they generally only allow FTP access to the web directory and the cstrike folder (you use cpanel or some such program to start/stop the server).

Here's what my start up scripts look like:
```
#!/bin/sh
# Source Dedicated Server Init Script

# Server options
TITLE='Source Dedicated Server' 	# Script initialization title
LONGNAME='PUB ROTATION CS:S'        		# Full title of game type
NAME='csspub'                          # Server handle for the screen session
DAEMON='RESTART_srcds_run'                # The server daemon
STEAM='/usr/local/games/steam/csspub'        # STEAM to Steam installation
USER='cssgamer'						# User to run the server as instead of root
									# Make sure to set up sudo correctly for this to work!

# Game options
IP='192.168.1.101'                # IP of the server
PORT='27015'                    # Port number to use
MAP='de_dust2'                    # Initial map to start
GAME='cstrike'              # Game type (tf|cstrike|valve|hl2mp)
SIZE='20'                        # Maximum number of players

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
            $INTERFACE sudo -u $USER $STEAM/$DAEMON $OPTS
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

And here's the modified script used to launch CS:S, if you use the default it (in my experience) will crash upon stopping the server. Use this script and it will allow you to reboot the server:
```
#!/bin/sh
#
#       Copyright (c) 2004, Valve LLC. All rights reserved.
#
#    a wrapper script for the main Source engine dedicated server binary.
#    Performs auto-restarting of the server on crash. You can
#    extend this to log crashes and more.
#

# setup the libraries, local dir first!
export LD_LIBRARY_PATH=".:bin:$LD_LIBRARY_PATH"

init() {
    # Initialises the various variables
    # Set up the defaults
    GAME=""
    DEBUG=""
    RESTART="yes"
    HL=./srcds_i486
    HL_DETECT=1
    TIMEOUT=10 # time to wait after a crash (in seconds)
    CRASH_DEBUG_MSG="email debug.log to [email]linux@valvesoftware.com[/email]"
    GDB="gdb" # the gdb binary to run
    DEBUG_LOG="debug.log"
    PID_FILE="" # only needed it DEBUG is set so init later
    STEAM=""
    PID_FILE_SET=0
    STEAMERR=""
    SIGINT_ACTION="quit 0" # exit normally on sig int
    NO_TRAP=0
    AUTO_UPDATE=""
    STEAM_USER=""
    STEAM_PASSWORD=""
    PARAMS=$*

    # Remove any old default pid files
    # Cant do this as they may be still running
    #rm -f hlds.*.pid

    # use the $FORCE environment variable if its set
    if test -n "$FORCE" ; then
        # Note: command line -binary will override this
        HL=$FORCE
        HL_DETECT=0
    fi

    while test $# -gt 0; do
        case "$1" in
        "-game")
            GAME="$2"
            shift ;;
        "-debug")
            DEBUG=1
            # Ensure that PID_FILE is set
            PID_FILE_SET=1
            if test -z "$PID_FILE"; then
                PID_FILE="hlds.$$.pid"
            fi ;;
        "-norestart")
            RESTART="" ;;
        "-pidfile")
            PID_FILE="$2"
            PID_FILE_SET=1
            shift ;;
        "-binary")
            HL="$2"
            HL_DETECT=0
            shift ;;
        "-timeout")
            TIMEOUT="$2"
            shift ;;
        "-gdb")
            GDB="$2"
            shift ;;
        "-debuglog")
            DEBUG_LOG="$2"
            shift ;;
        "-autoupdate")
            AUTO_UPDATE="yes"
            STEAM="./steam"
            RESTART="yes" ;;
        "-steamerr")
            STEAMERR=1 ;;
        "-ignoresigint")
            SIGINT_ACTION="" ;;
        "-notrap")
            NO_TRAP=1 ;;
        "-steamuser")
            STEAM_USER="$2";
            shift ;;
        "-steampass")
            STEAM_PASSWORD="$2";
            shift ;;
        "-help")
            # quit with syntax
            quit 2
            ;;
        esac
        shift
    done

    # Ensure we have a game specified
    if test -z "$GAME"; then
        GAME="cstrike"
        PARAMS="$PARAMS -game $GAME"
    elif test ! -d "$GAME"; then
        echo "Invalid game type '$GAME' sepecified."
        quit 1
    fi

    if test 0 -eq "$NO_TRAP"; then
        # Set up the int handler
        # N.B. Dont use SIGINT symbolic value
        #  as its just INT under ksh
        trap "$SIGINT_ACTION" 2
    fi

    # Only detect the CPU if it hasnt been set with
    # either environment or command line
    if test "$HL_DETECT" -eq 1; then
        detectcpu
    fi

    if test ! -f "$HL"; then
        echo "Source Engine binary '$HL' not found, exiting"
        quit 1
    elif test ! -x "$HL"; then
        # Could try chmod but dont know what we will be
        # chmoding so just fail.
        echo "Source engine binary '$HL' not executable, exiting"
        quit 1
    fi

    # Setup debugging
    if test -n "$DEBUG" ; then
        #turn on core dumps :) (if possible)
        echo "Enabling debug mode"
        if test "unlimited" != `ulimit -c` && test "`ulimit -c`" -eq 0 ; then
            ulimit -c 2000
        fi
        GDB_TEST=`$GDB -v`
        if test -z "$GDB_TEST"; then
            echo "Please install gdb first."
            echo "goto [http://www.gnu.org/software/gdb/](http://www.gnu.org/software/gdb/) "
            DEBUG="" # turn off debugging cause gdb isn't installed
        fi
    fi

    if test -n "$STEAM_PASSWORD" && test -z "$STEAM_USER"; then
        echo "You must set both the steam username and password."
        quit 1
    fi

    #if test 1 -eq $PID_FILE_SET && test -n "$PID_FILE"; then
    #    HL_CMD="$HL $PARAMS -pidfile $PID_FILE"
    #else
        HL_CMD="$HL $PARAMS"
    #fi
}

syntax () {
    # Prints script syntax

    echo "Syntax:"
    echo "$0 [-game <game>] [-debug] [-norestart] [-pidfile]"
    echo "    [-binary [srcds_i486]"
    echo "    [-timeout <number>] [-gdb <gdb>] [-autoupdate]"
    echo "    [-steamerr] [-ignoresigint] [-steamuser <username>]"
    echo "    [-steampass <password>] [-debuglog <logname>]"
    echo "Params:"
    echo "-game <game>            Specifies the <game> to run."
    echo "-debug                  Run debugging on failed servers if possible."
    echo "-debuglog <logname>    Log debug output to this file."
    echo "-norestart              Don't attempt to restart failed servers."
    echo "-pidfile <pidfile>      Use the specified <pidfile> to store the server pid."
    echo "-binary <binary>        Use the specified binary ( no auto detection )."
    echo "-timeout <number>       Sleep for <number> seconds before restarting"
    echo "            a failed server."
    echo "-gdb <gdb>              Use <dbg> as the debugger of failed servers."
    echo "-steamerr               Quit on steam update failure."
    echo "-steamuser <username>    Use this username for steam updates."  
    echo "-steampass <password>    Use this password for steam updates"
    echo "            (-steamuser must be specified as well)."
    echo "-ignoresigint           Ignore signal INT ( prevents CTRL+C quitting"
    echo "            the script )."
    echo "-notrap                 Don't use trap. This prevents automatic"
    echo "            removal of old lock files."
    echo ""
    echo "Note: All parameters specified as passed through to the server"
    echo "including any not listed."
}

debugcore () {
    # Debugs any core file if DEBUG is set and
    # the exitcode is none 0

    exitcode=$1

    if test $exitcode -ne 0; then
        if test -n "$DEBUG" ; then
            echo "bt" > debug.cmds;
            echo "info locals" >> debug.cmds;
            echo "info sharedlibrary" >> debug.cmds
            echo "info frame" >> debug.cmds;  # works, but gives an error... must be last
            echo "----------------------------------------------" >> $DEBUG_LOG
            echo "CRASH: `date`" >> $DEBUG_LOG
            echo "Start Line: $HL_CMD" >> $DEBUG_LOG

            # check to see if a core was dumped
            if test -f core ; then
                CORE="core"
            elif test -f core.`cat $PID_FILE`; then
                CORE=core.`cat $PID_FILE`
            elif test -f "$HL.core" ; then
                CORE="$HL.core"
            fi
            
            if test -n "$CORE"; then
                $GDB $HL $CORE -x debug.cmds -batch >> $DEBUG_LOG
            fi
        
            echo "End of Source crash report" >> $DEBUG_LOG
            echo "----------------------------------------------" >> $DEBUG_LOG
            echo $CRASH_DEBUG_MSG
            rm debug.cmds
        else
            echo "Add \"-debug\" to the $0 command line to generate a debug.log to help with solving this problem"
        fi
    fi
}

detectcpu() {
    # Attempts to auto detect the CPU
    echo "Auto detecting CPU"

    if test -e /proc/cpuinfo; then
        CPU_VERSION="`grep "cpu family" /proc/cpuinfo | cut -f2 -d":" | tr -d " " | uniq`";
        if test $CPU_VERSION -lt 4; then
            echo "Error: srcds REQUIRES a 486 CPU or better";
            quit 1
        elif test $CPU_VERSION -ge 6; then
            FEATURES="`grep 'flags' /proc/cpuinfo`";
            SSE2="`echo $FEATURES |grep -i SSE2`"
            AMD="`grep AMD /proc/cpuinfo`";
            if test -n "$AMD"; then
                OPTERON="`grep Opteron /proc/cpuinfo`";
                PLATFORM="`uname -m`"
                if test -z "$OPTERON"; then
                    OPTERON="`grep "Athlon HX" /proc/cpuinfo`";
                    if test -z "$OPTERON"; then
                        OPTERON="`grep "Athlon(tm) 64" /proc/cpuinfo`";
                    fi
                fi

                if test -n "$OPTERON" && test "x86_64" = "$PLATFORM"; then
                    echo "Using AMD-Opteron (64 bit) Optimised binary."
                    HL=./srcds_amd
                else
                    echo "Using AMD Optimised binary."
                    HL=./srcds_amd
                fi
            elif  test -n "$SSE2"; then
                # CPU supports SSE2 P4 +
                echo "Using SSE2 Optimised binary."
                HL=./srcds_i686
            else
                echo "Using default binary."
            fi        
        else
            echo "Using default binary."
        fi

    elif test "FreeBSD" = `uname`; then
        CPU="`grep 'CPU:' /var/run/dmesg.boot`"
        FEATURES="`grep 'Features=' /var/run/dmesg.boot`"
        AMD="`echo $CPU |grep AMD`"
        I686="`echo $CPU |grep 686`"
        SSE2="`echo $FEATURES |grep -i SSE2`"
        if test -n "$AMD"; then
            echo "Using AMD Optimised binary."
            HL=./srcds_amd
        elif test -n "$SSE2" ; then
            echo "Using SSE2 Optimised binary."
            HL=./srcds_i686
        else
            echo "Using default binary."
        fi
    else
        echo "Using default binary."
    fi
}

update() {
    updatesingle
}

updatesingle() {
    # Run the steam update
    # exits on failure if STEAMERR is set

    if test -n "$AUTO_UPDATE"; then
        if test -f "$STEAM"; then
            echo "Updating server using Steam."
        
            if test "$GAME" = "cstrike"; then
                GAME="Counter-Strike Source";
            fi
            if test "$GAME" = "dod"; then
                GAME="dods";
            fi

            CMD="$STEAM -command update -dir .";
            if test -n "$STEAM_USER"; then
                CMD="$CMD -username $STEAM_USER";
            fi
            if test -n "$STEAM_PASSWORD"; then
                CMD="$CMD -password $STEAM_PASSWORD";
            fi

            $CMD -game "$GAME"
            if test $? -ne 0; then
                if test -n "$STEAMERR"; then
                    echo "`date`: Steam Update failed, exiting."
                    quit 1
                else
                    echo "`date`: Steam Update failed, ignoring."
                    return 0
                fi
            fi
        else
            if test -n "$STEAMERR"; then
                echo "Could not locate steam binary:$STEAM, exiting.";
                quit 1
            else
                echo "Could not locate steam binary:$STEAM, ignoring.";
                return 0
            fi
        fi
    fi

    return 1
}
    
run() {
    # Runs the steam update and server
    # Loops if RESTART is set
    # Debugs if server failure is detected
    # Note: if RESTART is not set then
    # 1. DEBUG is set then the server is NOT exec'd
    # 2. DEBUG is not set the the server is exec'd

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
        # Update if needed
        update

        # Run the server
        if test -z "$DEBUG"; then
            # debug not requested we can exec
            exec $HL_CMD
        else
            # debug requested we can't exec
            $HL_CMD
            debugcore $?
        fi
    fi
}

quit() {
    # Exits with the give error code, 1
    # if none specified.
    # exit code 2 also prints syntax
    exitcode="$1"

    # default to failure
    if test -z "$exitcode"; then
        exitcode=1
    fi

    case "$exitcode" in
    0)
        echo "`date`: Server Quit" ;;
    2)
        syntax ;;
    *)
        echo "`date`: Server Failed" ;;
    esac

    # Remove pid file
    if test -n "$PID_FILE" && test -f "$PID_FILE" ; then
        # The specified pid file
        rm -f $PID_FILE
    fi

    # reset SIGINT and then kill ourselves properly
    trap - 2
    kill -2 $$
}

# Initialise
init $*

# Run
run

# Quit normally
quit 0

```

Disclaimer: I edited some of the above code using examples found online, but nothing is originally mine.

---

### Post by Strega on 2009-08-31
> **dfreer said:**
> If you have putty access, try using top (or my favorite htop if you can install it) to see if there are any CS:S servers already running.

Thanks, that worked.
I got all my servers offline.
But I have still 1 problem, setting up my ftp right.
This is what I did
```
sudo apt-get install proftpd
nano /etc/shells
```
I added the /bin/false line
```
sudo useradd strega -p 12345 -d /home/strega -s /bin/false
sudo passwd strega
```
After doing this I tried to login with my ftp programm.
It gave me this error :
```
Resolving 188.40.79.137...  
188.40.79.137 connecting...  
220 ProFTPD 1.3.1 Server (Debian) [::ffff:188.40.79.137]  
SFTP connection error - The current connection has timeout
Can't establish connection --> 188.40.79.137:21 @ Mon Aug 31 12:06:59 2009   (0-1460)
```
Any idea why?

Regards, Strega

---

### Post by dfreer on 2009-08-31
Sounds like you are using a guide to setup proftp? If this is the case it would be useful to link to the guide in question. This is also a seperate question from your original, not really related, and as such would be better served in a new thread.

As for me, I've always used SSH to transfer files since it's already installed rather than install a new service like FTP. But that's just me, and so I don't really have any experience installing proftp.

---

### Post by Strega on 2009-08-31
> **dfreer said:**
> Sounds like you are using a guide to setup proftp? If this is the case it would be useful to link to the guide in question. This is also a seperate question from your original, not really related, and as such would be better served in a new thread.

As for me, I've always used SSH to transfer files since it's already installed rather than install a new service like FTP. But that's just me, and so I don't really have any experience installing proftp.

Sorry about posting it in this thread :p
This is the link to the tuttorial :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
I need the FTP to up and download files for my gameservers.

Regards, Strega

---

### Post by dfreer on 2009-08-31
Have you edited your /etc/proftpd/proftpd.conf yet as the guide says? Also, not knowing your hosting provider, it could be that they already have a FTP solution set up (most do), and port 21 could also already be in use. 

I would suggest that you create a new thread in the appropriate section concerning this FTP problem, including a link to this one, so that users who are familiar with proftp can see it and help you much better than I could.

---

### Post by Strega on 2009-09-01
I'll do that :D
Thank you !

---

