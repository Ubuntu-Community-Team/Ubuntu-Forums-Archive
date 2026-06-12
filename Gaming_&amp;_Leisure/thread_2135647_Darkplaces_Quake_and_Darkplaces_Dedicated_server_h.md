---
title: "Darkplaces Quake and Darkplaces Dedicated server howto"
date: 2013-04-14
forum: Gaming &amp; Leisure
---

### Post by scar3crow on 2013-04-14
## This howto is for installing the most awesome darkplaces engine and server for the old
FPS game quake on ubuntu 12.04 - 12.10

sudo apt-get install darkplaces darkplaces-server

sudo mkdir -p /usr/share/games/quake

sudo mkdir -p /usr/share/games/quake/id1

## mount Quake CDROM and navigate to the id1 folder

sudo cp pak0.pak pak1.pak /usr/share/games/quake/id1

## (or copy paste with your favorite file manager)

## mission packs, ctf and maps go in their corresponding folders

## /usr/share/games/quake/hypnotic
## /usr/share/games/quake/rogue
## /usr/share/games/quake/ctf
## /usr/share/games/quake/maps

## start the game with:

darkplaces -basedir /usr/share/games/quake

## to set up a dedicated server that loads automatically on boot do the following:

sudo gedit /etc/init.d/darkplaces-server

## and add the following:

#! /bin/sh
    ### BEGIN INIT INFO
    # Provides:          darkplaces-server
    # Required-Start:    $remote_fs $syslog
    # Required-Stop:     $remote_fs $syslog
    # Default-Start:     2 3 4 5
    # Default-Stop:      0 1 6
    # Short-Description: Example initscript
    # Description:       This file should be used to construct scripts to be
    #                    placed in /etc/init.d.
    ### END INIT INFO
     
    # Author: anonymous user <foo@bar.com>
    #
    # Please remove the "Author" lines above and replace them
    # with your own name if you copy and modify this script.
     
    # Do NOT "set -e"
     
    # PATH should only include /usr/* if it runs after the mountnfs.sh script
    PATH=$PATH:/usr/games
    DESC="Darkplaces Dedicated Server"
    NAME=darkplaces-server
    DAEMON=/usr/games/darkplaces-server
    DAEMON_ARGS="-basedir /usr/share/games/quake/ +exec debian_server.cfg"
    PIDFILE=/var/run/$NAME.pid
    SCRIPTNAME=/etc/init.d/$NAME
     
    # Exit if the package is not installed
    [ -x "$DAEMON" ] || exit 0
     
    # Read configuration variable file if it is present
    [ -r /etc/default/$NAME ] && . /etc/default/$NAME
     
    # Load the VERBOSE setting and other rcS variables
    . /lib/init/vars.sh
     
    # Define LSB log_* functions.
    # Depend on lsb-base (>= 3.2-14) to ensure that this file is present
    # and status_of_proc is working.
    . /lib/lsb/init-functions
     
    #
    # Function that starts the daemon/service
    #
    do_start()
    {
            # Return
            #   0 if daemon has been started
            #   1 if daemon was already running
            #   2 if daemon could not be started
            start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
                    || return 1
            start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
                    $DAEMON_ARGS \
                    || return 2
            # Add code here, if necessary, that waits for the process to be ready
            # to handle requests from services started subsequently which depend
            # on this one.  As a last resort, sleep for some time.
    }
     
    #
    # Function that stops the daemon/service
    #
    do_stop()
    {
            # Return
            #   0 if daemon has been stopped
            #   1 if daemon was already stopped
            #   2 if daemon could not be stopped
            #   other if a failure occurred
            start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
            RETVAL="$?"
            [ "$RETVAL" = 2 ] && return 2
            # Wait for children to finish too if this is a daemon that forks
            # and if the daemon is only ever run from this initscript.
            # If the above conditions are not satisfied then add some other code
            # that waits for the process to drop all resources that could be
            # needed by services started subsequently.  A last resort is to
            # sleep for some time.
            start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
            [ "$?" = 2 ] && return 2
            # Many daemons don't delete their pidfiles when they exit.
            rm -f $PIDFILE
            return "$RETVAL"
    }
     
    #
    # Function that sends a SIGHUP to the daemon/service
    #
    do_reload() {
            #
            # If the daemon can reload its configuration without
            # restarting (for example, when it is sent a SIGHUP),
            # then implement that here.
            #
            start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
            return 0
    }
     
    case "$1" in
      start)
            [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
            do_start
            case "$?" in
                    0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                    2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
            esac
            ;;
      stop)
            [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
            do_stop
            case "$?" in
                    0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                    2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
            esac
            ;;
      status)
           status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
           ;;
      #reload|force-reload)
            #
            # If do_reload() is not implemented then leave this commented out
            # and leave 'force-reload' as an alias for 'restart'.
            #
            #log_daemon_msg "Reloading $DESC" "$NAME"
            #do_reload
            #log_end_msg $?
            #;;
      restart|force-reload)
            #
            # If the "reload" option is implemented then remove the
            # 'force-reload' alias
            #
            log_daemon_msg "Restarting $DESC" "$NAME"
            do_stop
            case "$?" in
              0|1)
                    do_start
                    case "$?" in
                            0) log_end_msg 0 ;;
                            1) log_end_msg 1 ;; # Old process is still running
                            *) log_end_msg 1 ;; # Failed to start
                    esac
                    ;;
              *)
                    # Failed to stop
                    log_end_msg 1
                    ;;
            esac
            ;;
      *)
            #echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
            echo "Usage: $SCRIPTNAME {start|stop|status|restart|force-reload}" >&2
            exit 3
            ;;
    esac
     
    :

## and open up port 26000 in your firewall(s)

## be sure to edit debian_server.cfg in /usr/share/games/quake/id1

(if this file does not exist, and it probably doesn't; create it and add the following
for a most basic server that runs on localhost:26000 and internet:26000)

// Example Quake server configuration for Debian
// This is installed into /etc/quake-server/server.cfg and symlinked into
// the game directory as debian_server.cfg, so you can run it via:
//
//     exec debian_server.cfg

deathmatch 1
hostname "An Anonymous Debian Server"
timelimit 15
fraglimit 30
map dm1

// Various options depend on the server version you're using.
// When using darkplaces-server, you can use "sv_public 1" to advertise
// your server to the "master servers"
sv_public 1

## enjoy ;)

--scarrs

---

