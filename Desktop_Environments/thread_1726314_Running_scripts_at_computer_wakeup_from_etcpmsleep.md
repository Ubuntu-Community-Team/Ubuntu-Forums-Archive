---
title: "Running scripts at computer wakeup from /etc/pm/sleep.d .. limitations? ( gnome )"
date: 2011-04-11
forum: Desktop Environments
---

### Post by rocuan on 2011-04-11
Are there limitations on what can be started from /etc/pm/sleep.d after system wakeup?

I wrote a perl script to randomly change my gnome desktop background [http://ubuntuforums.org/showthread.php?p=10654538](http://ubuntuforums.org/showthread.php?p=10654538)
I want to run that script when my laptop wakes up.
I followed this guide : [http://ubuntuforums.org/showthread.php?t=1484156](http://ubuntuforums.org/showthread.php?t=1484156)
and wrote this code
```

#!/bin/bash
. /usr/lib/pm-utils/functions
case "$1" in
    hibernate|suspend) ;;
    thaw|resume)
        echo "woke up `date`" >> /var/log/wakeup.log
        /usr/bin/perl /home/me/bin/perlscript 2> /var/log/wakeup_error.log ;;
    *) ;;
esac
exit $?

```I saved the script as 00_user_script in the /etc/pm/sleep.d folder & made it root executable

The wakeup.log file gets filled correctly so I think the code is solid
but
my perl script refuses to run.

[COLOR=Indigo]To debug,[COLOR=Black] I tried substituting[/COLOR] pidgin [COLOR=Black]to auto-load after wakeup[/COLOR].[/COLOR]
```
/usr/bin/pidgin 2> /var/log/wakeup_error.log ;;
```I caught this error> (Pidgin:26174): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed

** (Pidgin:26174): WARNING **: cannot open display: unsetThis lead me to believe that it was calling pidgin too early, before gnome had "woken up"
So I thought maybe the sleep.d/script should call another shell script( startpidgin.sh ) that sleeps for a bit
```

#!/bin/bash
sleep 7
/usr/bin/pidgin 2>> /var/log/wakeup_error.log

```but still get the same error.

I figured the sleep.d/00_user_script was waiting for startpidgin.sh to exit, so I installed dtach [http://manpages.ubuntu.com/manpages/natty/man1/dtach.1.html](http://manpages.ubuntu.com/manpages/natty/man1/dtach.1.html) 
and tried again.
```
dtach -n /tmp/foo /home/me/bin/startpidgin 2> /var/log/wakeup_error.log

```still throws same error

- If I run ps -e immediately after waking I see the startpidgin process is running & waiting, but pidgin fails to start
- I have varied the sleep time
- I have varied the script name : 99_user.sh, 60_user, 00_user, etc
but no love.

I assume the GDK environment is still undefined somehow so the script fails.
Thoughts? Options? Answers?
-puzzled

---

### Post by Kremlin on 2011-05-25
There are two problems that you can be encountering.

The main one is that the DISPLAY is not defined when running boot scripts as root. 

The second is that you might want to be running commands as the logged in user when interacting with their display (e.g., launching pidgin as a non-privileged user).

Here is my script that I wrote yesterday for the purpose of switching the behaviour of two and three finger taps on the touchpad:

```

#!/bin/bash
#
# Script to interact with running X server after waking from sleep
#

. /usr/lib/pm-utils/functions
case "$1" in
    hibernate|suspend) ;;
    thaw|resume)
	echo "woke up `date`" >> /var/log/wakeup.log
	export DISPLAY=:0
#	su -c - <username> <commandtorun> 2>> /var/log/wakeup_error.log ;;
    *) ;;
esac
exit $?

```

You could probably do some fancier things to make it more robust (like parsing the output of grep for the local display number that X is bound to, and working out who owns the currently-logged-in session) but it works as is for me. And now whenever the computer wakes from sleep, it restores the desired behaviour for touchpad clicks!

---

