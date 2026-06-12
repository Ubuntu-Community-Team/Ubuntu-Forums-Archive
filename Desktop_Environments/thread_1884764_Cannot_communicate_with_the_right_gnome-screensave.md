---
title: "Cannot communicate with the right gnome-screensaver"
date: 2011-11-21
forum: Desktop Environments
---

### Post by effigies on 2011-11-21
I have a script which grabs the DISPLAY my user is on, and runs `gnome-screensaver-command -d` as my user. When I plug my phone in to my computer, the script is run.

Unfortunately, there seems to be a disconnect between the gnome-screensaver run by hitting Ctrl-Alt-L and the one accessed by gnome-screensaver-command... except when run directly from a terminal in gnome.

I am running 11.10 (dist-upgraded from 11.04, which was a clean install), with classic GNOME. To reproduce:

```
$ gnome-screensaver-command -l && sleep 10s && gnome-screensaver-command -d
```

Running my script as root in the intervening 10 seconds does not work.

```
$ sudo su effigies
$ gnome-screensaver-command -l && sleep 10s && gnome-screensaver-command -d
```

Running my script as root in the intervening 10 seconds does work.

```
$ ps aux | grep gnome-screensaver
effigies    10167  0.0  0.3 290264 12896 ?        Sl   20:27   0:00 /usr/bin/gnome-screensaver --no-daemon
effigies    30536  0.0  0.3 290208 13868 ?        Sl   22:19   0:00 /usr/bin/gnome-screensaver --no-daemon
```

As you can see, there are multiple instances of gnome-screensaver, one which is accessible from the normal collection of terminals in my X session, and one which is accessible otherwise. Killing these processes or restarting the computer does not fix the problem.

The script in question is:

```
#!/bin/sh
export DISPLAY=`who | grep ^effigies | grep \(: | sed -e 's/.*(\(\:.*\)).*/\1/' | head -n 1`
sudo -u effigies gnome-screensaver-command -d

```

I have a suspicion that the problem lies in a dbus namespace or something of the sort, but that's a bit beyond my depth/spare time. Anybody have any insight?

---

### Post by effigies on 2011-11-22
Okay, solved.

Apparently in older versions of Ubuntu, knowing the X session (e.g :0.0) was enough, but now you need to know the DBUS_SESSION_BUS_ADDRESS. So:

~/bin/dbs
```
#!/usr/bin/perl

my $key = "DBUS_SESSION_BUS_ADDRESS";
my $file = "$ENV{HOME}/.dbus_session";
open DBUS_SESSION, ">$file";
print DBUS_SESSION "export $key=\"$ENV{$key}\"\n";
close DBUS_SESSION;
chmod 0600, $file;
```

~/bin/unlock
```
#!/bin/bash
source ~/.dbus_session
gnome-screensaver-command -d
```

/usr/local/bin/unlock
```
#!/bin/bash
sudo -u effigies /home/effigies/bin/unlock
```

/etc/udev/rules.d/90-unlockdev.rules
```
ACTION=="add", SUBSYSTEM=="block", ATTRS{serial}=="ABJKLCJXKJDSLFSERIALKJLFAJSD", RUN+="/usr/local/bin/unlock"
```

Finally, add ~/bin/dbs as a startup program with gnome-session-properties.

---

