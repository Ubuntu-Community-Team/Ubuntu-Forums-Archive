---
title: "incron doesn't work after rebooting"
date: 2009-03-16
forum: General Help
---

### Post by tezer on 2009-03-16
Hi
I have a problem with the incron: after I restart my computer it doesn't work. I have to run: *incrontab -d* to start it moving.
The service must be running ok (*/etc/init.d/incron* exists)
Do you have any idea what's wrong?
Thanks in advance.
PS I run Mint 6 which is almost the same as Ububntu 8.10

---

### Post by pennacook on 2009-03-16
I would recommend checking if it is listed in /etc/rc2.d or /etc/rc3.d, symlinked from init.d with an S## similar to below:

```
lrwxrwxrwx   1 root     root           16 May 23  2008 S56xinetd -> ../init.d/xinetd

```
This will ensure that the service starts on boot.

---

### Post by tezer on 2009-03-16
Thank you. I will try this.
There is an update to the problem description:

if I do 

```
sudo /etc/init.d/incron start
```

nothing happens (it still doesn't work)

but

```
sudo /etc/init.d/incron restart
```

makes it work.

What might it be? Does incron hang up somehow?

---

### Post by pennacook on 2009-03-16
can you post the incron script that is init.d? Strange that it starts on a restart, but not with start.

---

### Post by tezer on 2009-03-16
This is the */etc/init.d/incron* script. I never edited it.

```
#! /bin/sh
#
# incron       This init.d script is used to start incron
#

### BEGIN INIT INFO
# Provides:          incron
# Required-Start:    $local_fs $syslog
# Required-Stop:     $local_fs $syslog
# Should-Start:
# Should-Stop:
# Default-Start:     S 2 3 4 5
# Default-Stop:      0 6
# Short-Description: File system events scheduler
### END INIT INFO

PATH=/sbin:/bin:/usr/sbin:/usr/bin
INCROND=/usr/sbin/incrond
NAME=incron
DESC="File system events scheduler"
INCROND_PID=/var/run/incrond.pid
INCROND_CONF=/etc/incron.conf

[ -x $INCROND ] || exit 0

# loading lsb functions
. /lib/lsb/init-functions

case "$1" in
    start)
        log_daemon_msg "Starting $DESC"
        log_progress_msg "$NAME"
        start_daemon -p $INCROND_PID $INCROND -f $INCROND_CONF
        log_end_msg "$?"
        ;;

    stop)
        log_daemon_msg "Stopping $DESC"
        log_progress_msg "$NAME"
        killproc -p $INCROND_PID $INCROND
        log_end_msg "$?"
        ;;

    reload)
        log_daemon_msg "Reloading $DESC"
        log_progress_msg "$NAME"
        echo -n
        log_end_msg "$?"
        ;;

    restart|force-reload)
        $0 stop
        sleep 1
        $0 start
        ;;

    *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```

---

### Post by tezer on 2009-03-16
I had a look at my syslog.
There is no any *incron* related lines after a start of the system. 
*sudo /etc/init.d/incron start* also generates no lines with *incron*.

After *sudo /etc/init.d/incron restart*
I found:
```
Mar 16 18:32:45 desktop incrond[3966]: stopping service
Mar 16 18:32:46 desktop incrond[8679]: starting service (version 0.5.7, built on Oct 30 2007 05:35:47)
Mar 16 18:32:46 desktop incrond[8680]: loading system tables
Mar 16 18:32:46 desktop incrond[8680]: loading user tables
Mar 16 18:32:46 desktop incrond[8680]: loading table for user username
Mar 16 18:32:46 desktop incrond[8680]: cannot create watch for user username: (16) Device or resource busy
Mar 16 18:32:46 desktop incrond[8680]: ready to process filesystem events 
```

---

### Post by tezer on 2009-03-16
If it is not possible to find what the problem is, where should I put the restart command to run it automatically every time I boot?

---

### Post by tezer on 2009-03-16
> **pennacook said:**
> I would recommend checking if it is listed in /etc/rc2.d or /etc/rc3.d, symlinked from init.d with an S## similar to below:

```
lrwxrwxrwx   1 root     root           16 May 23  2008 S56xinetd -> ../init.d/xinetd

```
This will ensure that the service starts on boot.

Yes, it's listed in  */etc/rc2.d* and in */etc/rc3.d* as  *S20incron*

---

### Post by tezer on 2009-03-17
Any ideas?
Please!

---

### Post by tezer on 2009-03-17
The output of *sudo update-rc.d -f incron defaults* is:
*System startup links for /etc/init.d/incron already exist.*

I checked */var/run* and found *incrond.pid*, deleted it rebooted, but it still doesn't work.
Tried *sudo /etc/init.d/incron stop* and *incrond.pid* disappeared.
After *sudo /etc/init.d/incron start* I can see *incrond.pid* again and incrontab started working ok.
I can't understand why it doesn't work right from the beginning.

---

### Post by pennacook on 2009-03-17
maybe add a set -x at the top of your incron startup script so that it logs what all it is doing on reboot. Quite strange that it would start from command line with start, but not on boot.

---

### Post by tezer on 2009-03-17
> **pennacook said:**
> maybe add a set -x at the top of your incron startup script so that it logs what all it is doing on reboot. 
Could you indicate the exact place where (and what exactly) I should put? The script file is on the previous page.
Thank you.

---

### Post by pennacook on 2009-03-18
```

#! /bin/sh
[COLOR="Red"]set -x[/COLOR]
#
# incron       This init.d script is used to start incron
#

### BEGIN INIT INFO
# Provides:          incron
# Required-Start:    $local_fs $syslog
# Required-Stop:     $local_fs $syslog
# Should-Start:
# Should-Stop:
# Default-Start:     S 2 3 4 5
# Default-Stop:      0 6
# Short-Description: File system events scheduler
### END INIT INFO

PATH=/sbin:/bin:/usr/sbin:/usr/bin
INCROND=/usr/sbin/incrond
NAME=incron
DESC="File system events scheduler"
INCROND_PID=/var/run/incrond.pid
INCROND_CONF=/etc/incron.conf

[ -x $INCROND ] || exit 0

# loading lsb functions
. /lib/lsb/init-functions

case "$1" in
    start)
        log_daemon_msg "Starting $DESC"
        log_progress_msg "$NAME"
        start_daemon -p $INCROND_PID $INCROND -f $INCROND_CONF
        log_end_msg "$?"
        ;;

    stop)
        log_daemon_msg "Stopping $DESC"
        log_progress_msg "$NAME"
        killproc -p $INCROND_PID $INCROND
        log_end_msg "$?"
        ;;

    reload)
        log_daemon_msg "Reloading $DESC"
        log_progress_msg "$NAME"
        echo -n
        log_end_msg "$?"
        ;;

    restart|force-reload)
        $0 stop
        sleep 1
        $0 start
        ;;

    *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

---

### Post by tezer on 2009-03-18
Thank you.
I did as you said, restarted the computer, and looked into /var/log/syslog
There is NOTHING about incrond.
*ps aux|grep incron|grep -v grep* shows that the daemon started:

*root      3956  0.0  0.0   3276  1180 ?        Ss   13:29   0:00 /usr/sbin/incrond -f /etc/incron.conf*

Is there any other log that I should look into?
after I restarted (incrontab -d) I found in the log (User is my account):

```
Mar 18 13:41:33 desktop incrond[3956]: table for user User changed, reloading
Mar 18 13:41:33 desktop incrond[3956]: cannot create watch for user User: (16) Device or resource busy
Mar 18 13:41:37 desktop incrond[3956]: (User) CMD (unison Notecase -batch)

```

---

### Post by pennacook on 2009-03-18
Then it is running as expected from your output of ps. If you want it to run with the "-d", you would need to change the start portion to run it as such.

---

### Post by tezer on 2009-03-18
> **pennacook said:**
> If you want it to run with the "-d", you would need to change the start portion to run it as such.
"-d" means restart. But the question is why it does not start properly and needs restarting to run.

---

### Post by pennacook on 2009-03-19
I would recommend going to 0.5.8. I did find some other references out in the wild about 0.5.7 having bugs where it wouldn't daemonize on initial start.

---

### Post by tezer on 2009-03-19
> **pennacook said:**
> I would recommend going to 0.5.8. I did find some other references out in the wild about 0.5.7 having bugs where it wouldn't daemonize on initial start.

Thank you. But I failed to compile the source:
Tried ./config:

```
bash: ./configure: No such file or directory
```

Tried make:

```
g++ -c  -O2 -g0 -Wall -pipe -o icd-main.o icd-main.cpp
make: g++: Command not found
make: *** [icd-main.o] Error 127

```

SUDO doesn't change anything

I searched internet for the error explanation but found nothing...

---

### Post by pennacook on 2009-03-23
It doesn't come with a configure script. You should be able to compile using gcc. Edit your Makefile to change the following to gcc (assuming you have gcc installed).

```
CXX = g++
```

Then run your make, etc.

---

