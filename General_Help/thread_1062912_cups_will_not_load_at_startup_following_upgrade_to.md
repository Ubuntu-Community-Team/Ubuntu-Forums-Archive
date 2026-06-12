---
title: "cups will not load at startup following upgrade to Intrepid"
date: 2009-02-07
forum: General Help
---

### Post by w1zard on 2009-02-07
Hi
   Having spent several frustrating hours battling with CUPS, which is no longer working after an upgrade to Intrepid, I need a bit of help for the final part.

   CUPS was not running at all, could not be started manually, as there were no entries for cups or cupsys in the init.d directory. I tried

```
sudo apt-get remove cups
sudo apt-get clean cups
```

...This made no difference. On searching about for CUPS references, I stumbled upon a file named 'cupsd' in the /usr/sbin directory. Simply running
```

sudo /usr/sbin/cupsd
```

fixes the printing. But only for that session. My question is: how do I make this run automatically (as sudo if necessary) on every boot? There's no entry for CUPS in Services under Administration. It won't work if added to Sessions Preferences (because it needs sudo). How do I get this to work?

Any help much appreciated :)

---

### Post by cmnorton on 2009-02-07
You need to get the startup scripts set for cupsd. You do this with update-rc.d

 sudo update-rc.d cups defaults

---

### Post by w1zard on 2009-02-07
> **cmnorton said:**
> You need to get the startup scripts set for cupsd. You do this with update-rc.d

 sudo update-rc.d cups defaults


Thank you for the reply - unfortunately I get the following when running this command:

```
sudo update-rc.d cups defaults
update-rc.d: /etc/init.d/cups: file does not exist
```

---

### Post by cmnorton on 2009-02-07
You cleaned cups in your original post. I did not see you re-install it. Your error suggests the cups daemon is not there.


Here's my cups daemon. You can put it in the right place manually, but that's not a substitute for finding out why the daemon is not there in the first place. I would suggest playing with the install before resorting to putting this file in as a replacement.

--------------------------- begin cups daemon ---------------------------------
#! /bin/sh
### BEGIN INIT INFO
# Provides:          cups
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $network avahi
# Should-Stop:       $network
# X-Start-Before:    samba
# X-Stop-After:      samba
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: CUPS Printing spooler and server
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/cupsd
NAME=cupsd
PIDFILE=/var/run/cups/$NAME.pid
DESC="Common Unix Printing System"

unset TMPDIR

test -x $DAEMON || exit 0

if [ -r /etc/default/cups ]; then
  . /etc/default/cups
fi

. /lib/lsb/init-functions

# Get the timezone set.
if [ -z "$TZ" -a -e /etc/timezone ]; then
    TZ=`cat /etc/timezone`
    export TZ
fi

restart_xprint() {
    if [ -n "$success" ] && [ -x /etc/init.d/xprint ]; then
        invoke-rc.d xprint force-reload || true
    fi

--------------------------- end cups daemon --------------------------

---

### Post by w1zard on 2009-02-08
Thanks for the reply. I did indeed reinstall cups after the remove/clean, and this went through fine, so I'm unsure why the cups daemon has disappeared.

I added your version of cups using

```
sudo gedit /etc/init.d/cups
```

and pasting the code from your version.

I then did a 

```
sudo chmod +x /etc/init.d/cups
```

and restarted, but still no cups service automatically running.

---

### Post by cmnorton on 2009-02-08
and then you've go to "chkconfig" it using the program in my first response.

---

### Post by w1zard on 2009-02-08
The system appears to think this is already in place:
```

sudo update-rc.d cups defaults
System startup links for /etc/init.d/cups already exist.
```

Restarting the system still results in no printers within the 'printer configuration' window. If I type

```
sudo /etc/init.d/cups
```

and 

```
sudo /usr/sbin/cupsd
```

This fixes it for the session. Any ideas?

---

