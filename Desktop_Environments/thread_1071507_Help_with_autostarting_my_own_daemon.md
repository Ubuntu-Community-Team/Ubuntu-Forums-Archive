---
title: "Help with autostarting my own daemon"
date: 2009-02-16
forum: Desktop Environments
---

### Post by tl3462 on 2009-02-16
I have an app which I can run fine from the terminal, I'd like to run it automatically on system startup. This is what I've done so far...

Created a really basic script in /etc/init.d/ to run my executable called 'myapp'...

```
#!/bin/bash
#
### BEGIN INIT INFO
# Provides: myapp
# Required-Start:
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start daemon at boot time
# Description: Enable service provided by daemon.
### END INIT INFO

# Source function library.
. /etc/init.d/functions

NAME=myapp

start() {
        echo -n "Starting : "

        /usr/bin/myapp
}

stop() {
        echo -n "Shutting down : "

        killall /usr/bin/myapp
        return
}

case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    status)

        ;;
    restart)
        stop
        start
        ;;
    *)
        echo "Usage:  {start|stop|status|reload|restart[|probe]"
        exit 1
        ;;
esac
exit $?

```

I've run > sudo update-rc.d myapp defaults but I get the message "System startup links for /etc/init.d/myapp already exist". Where would these System startup links be? I've cleared any links I had previously created in /etc/rc?.d/ . 

Am I missing something? What else do I have to do to get this to run at startup?!

NB. this app forks/daemonises and I'm testing if its running using > ps ax | grep myappIf its running as a daemon perhaps it won't even appear using ps? Surely not.

---

### Post by ajgreeny on 2009-02-16
If the script is executable could you simply run it at the start of the gnome session, like any other executable.  Perhaps you want it to run before the desktop starts, however, in which case I don't really know what to suggest, though I would have thought that putting it in /etc/init.d would work, so long as it is executable.  Double check that the .sh file is executable first, but other than that, I'm out of my depth.

---

### Post by tl3462 on 2009-02-16
The script is executable (755) and owned by root.

Weird isn't, I'd have thought so too. I'm out of my depth as well!

---

