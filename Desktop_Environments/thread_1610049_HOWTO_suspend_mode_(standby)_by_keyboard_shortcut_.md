---
title: "HOWTO: suspend mode (standby) by keyboard shortcut (Ubuntu 10.10)"
date: 2010-10-31
forum: Desktop Environments
---

### Post by pro1 on 2010-10-31
Hi!

I've written a small script to bring my Desktop PC into suspend (standby) mode by keyboard shortcut. You could use it like that:

[LIST]
[*]make a directory in your home-dir called "bin"
[*]copy the following script into ~/bin/gnome-suspend.sh and make it executable (chmod +x gnome-suspend.sh)
[*]associate a keyboard shortcut in your Gnome preferences
[/LIST]
Best regards, pro...

```
#!/bin/bash

# avoid multiple execution
[ $(pgrep -c "gnome-suspend") -ne 1 ] && exit 0

# countdown to suspend mode in seconds
TIMEOUT=30

(
  for i in $(seq 1 $TIMEOUT); do
    let "p=100*i/TIMEOUT"
    echo $p
    let "t=TIMEOUT-i"
    echo "# System is brought to suspend mode in $t seconds ..."
    sleep 1
  done
) | zenity --progress --title="System shutdown" --percentage=0 --auto-close

# shutdown aborted
[ "$?" -ne 0 ] && exit 0

# suspend mode
gnome-screensaver-command --lock
dbus-send --print-reply --system --dest=org.freedesktop.UPower \
    /org/freedesktop/UPower org.freedesktop.UPower.Suspend 

```

---

### Post by shakma on 2010-10-31
Hi Pro!

Just wanted to say thanks for an excellent script.  It works exactly as advertised!  I reduced the countdown timer, and removed the password protection, and it still worked beautifully.

As a quick side note, apparently as of 10.10, the Fn+F1 combo on the ASUS Eee PC 1005HA-PU17 works just fine for standby now...  When I mapped this script that combo, the "natural" standby actually over-rode this script, much to my suprise (suddenly no countdown-that's the only way I could tell).

But thanks again, pro1.  This script is 100% effective for mapping standby to a keyboard shortcut.

Peace.

---

### Post by elitenoobboy on 2011-03-12
Your "-ne 1" part should probably be "-gt 0", otherwise a zero will be sent back the first time it runs which will exit it prematurely.

The problem is that during the zenity timeout part, gnome-suspend is not running yet, so it can't exit if the timeout only is running. Do you know how to make it exit when just the timeout part is running?

---

### Post by rgstrator on 2011-04-29
Pro1, how did you find the actual command and its arguments that are invoked for a suspend?

---

