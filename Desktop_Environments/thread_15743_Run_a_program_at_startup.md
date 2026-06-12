---
title: "Run a program at startup?"
date: 2005-02-16
forum: Desktop Environments
---

### Post by mattack on 2005-02-16
I installed the no-ip client according to the directions [here](http://www.no-ip.com/tips.php/id/13?sid=89bac89b6c578660bbc8eef6b781b1f7) and everything went fine. In order to run it i just type in a termainal
```
sudo noip2
``` 
and it runs.
How can I run this program automatically everytime I login?
I tried putting it as a startup program in the Computer->Desktop Preferences->Sessions but when I restart it's not listed as a process in the system monitor...
oh, I also tried the command in the above link to get it to run on startup and I got persmission denied. and yes, I put sudo before the command....

Any help would be appreciated.

---

### Post by lao_V on 2005-02-16
[QUOTE=mattack]...
 oh, I also tried the command in the above link to get it to run on startup and I got persmission denied. and yes, I put sudo before the command....
 
 Any help would be appreciated.[/QUOTE]
 
 Try putting gksudo in front

---

### Post by mendicant on 2005-02-16
Is there some reason you don't want it to run at startup, but only when you log in?

---

### Post by mattack on 2005-02-16
[QUOTE=mendicant]Is there some reason you don't want it to run at startup, but only when you log in?[/QUOTE]

either one would be fine... I rarely start my computer witout logging in. Whichever is easier...

I just tried this:
```
matt@mattack:~ $ gksudo echo '/usr/local/bin/noip2' >> /etc/rc.local
bash: /etc/rc.local: Permission denied
``` 
same result with just sudo echo '/usr/local/bin/noip2' >> /etc/rc.local

---

### Post by mendicant on 2005-02-16
Typically, you would create a file /etc/init.d/noip, based off of /etc/init.d/skeleton which would start and stop the process for you.  Then, you would just run update-rc.d:

% sudo update-rc.d noip defaults 90

Edit the file using a new gnome-terminal:

% sudo gnome-terminal

and do everything in there.

The permission denied errors you get are  because the redirect is happening as you, not root.  The sudo'd gnome-terminal would solve this.

---

### Post by mattack on 2005-02-16
Alrighty....
This is all new to me. Scripting...  yeah.
So what goes in the file /etc/init.d/noip ?
Something like this?

```
#! /bin/sh
# /etc/init.d/noip2.sh

# Supplied by no-ip.com
# Modified for Debian GNU/Linux by Eivind L. Rygge <eivind@rygge.org>

# . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc

DAEMON=/usr/local/bin/noip2
NAME=noip2

test -x $DAEMON || exit 0

case "$1" in
    start)
    echo -n "Starting dynamic address update: "
    start-stop-daemon --start --pidfile /var/run/noip2.pid \
	--make-pidfile --exec $DAEMON
    echo "noip2."
    ;;
    stop)
    echo -n "Shutting down dynamic address update:"
    start-stop-daemon --stop --pidfile /var/run/noip2.pid \
	--oknodo --retry 30 --exec $DAEMON
    echo "noip2."
    ;;

    restart)
    echo -n "Restarting dynamic address update: "
    start-stop-daemon --stop --pidfile /var/run/noip2.pid \
			    --oknodo --retry 30 --exec $DAEMON
    start-stop-daemon --start --pidfile /var/run/noip2.pid \
			    --exec $DAEMON
    echo "noip2."
    ;;

    *)
    echo "Usage: $0 {start|stop|restart}"
    exit 1
esac
exit 0


```

It's a file called debian.noip2.sh that came with the package...
Could I copy it over to etc/init.d and rename it noip2.sh, run those commands you suggested and be done with it?

---

### Post by mendicant on 2005-02-16
That looks right.  Just make sure you have noip2 in /usr/local/bin.  You would then run the command:

% sudo update-rc.d noip2.sh defaults 90

---

### Post by mattack on 2005-02-16
This seems to work. I just rebooted and checked the running processes and noip2 is there.
Thanks!

---

### Post by iBix on 2006-03-11
do i need to enter the no-ip username/password information somewhere on this file or are they handled automatically ?

---

