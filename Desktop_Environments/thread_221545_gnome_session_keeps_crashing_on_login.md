---
title: "gnome session keeps crashing on login"
date: 2006-07-23
forum: Desktop Environments
---

### Post by numerodix on 2006-07-23
I installed dapper last week and for some reason my session keeps crashing. When I log in, I get a message saying my session could not be started and I just see one gnome-terminal on the screen.

> $ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "alex"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator


> $ cat /var/log/messages
Jul 23 23:13:37 frasier gconfd (alex-4716): starting (version 2.14.0), pid 4716 user 'alex'
Jul 23 23:13:37 frasier gconfd (alex-4716): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 23 23:13:37 frasier gconfd (alex-4716): Resolved address "xml:readwrite:/home/alex/.gconf" to a writable configuration source at position 1
Jul 23 23:13:37 frasier gconfd (alex-4716): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 23 23:13:37 frasier gconfd (alex-4716): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 23 23:13:37 frasier gconfd (alex-4716): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 23 23:13:37 frasier gconfd (alex-4718): starting (version 2.14.0), pid 4718 user 'alex'
Jul 23 23:13:37 frasier gconfd (alex-4718): Failed to get lock for daemon, exiting: Failed to lock '/tmp/gconfd-alex/lock/ior': probably another process has the lock, or your operating system has NFS file locking misconfigured (Resource temporarily unavailable)
Jul 23 23:14:01 frasier gconfd (alex-4716): Resolved address "xml:readwrite:/home/alex/.gconf" to a writable configuration source at position 0

I get these messages on every login, I've tried to google them without turning up anything and I don't know what they mean. As far as I'm concerned gconf is black magic anyway.

The funny thing is that when I get that one gnome-terminal and I type "gnome-session", I get my desktop just the way it is, no errors appear.

If I log into "gnome failsafe", that works, but I can't make that my default session, so I need to fix this somehow.

My problem seems to be similar (but not identical) to this one: [http://ubuntuforums.org/showthread.php?t=185905](http://ubuntuforums.org/showthread.php?t=185905)

---

