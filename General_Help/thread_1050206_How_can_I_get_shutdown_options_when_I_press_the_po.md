---
title: "How can I get shutdown options when I press the power button?"
date: 2009-01-25
forum: General Help
---

### Post by Chris Musampa on 2009-01-25
When I press the power button on my laptop I used to get the option to shutdown, suspend, logout, etc, now when I press it it just shuts down.  Its really annoying having to go through the menu to suspend (either to disk or ram).

'Confirm logout' and 'offer shutdown options' are both checked in session manager settings.

I have this repo enabled so I could try KDE4.2:
[http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu)

After much googling I found no solution but I did find that the following script should be called:
```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If gnome-power-manager, kpowersave or klaptopdaemon are running, let
# them handle policy This is effectively the same as 'acpi-support's
# '/usr/share/acpi-support/policy-funcs' file.

if pidof gnome-power-manager kpowersave > /dev/null ||
* (pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop kded kded loadedModules | grep -q klaptopdaemon) ; then
* * exit
fi

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && pidof dcopserver > /dev/null && test -x /usr/bin/dcop ; then
* * KDESES=`pidof dcopserver | wc -w`
* * if [ $KDESES -eq 1 ] ; then
* * * * # single KDE session -> ask user
* * * * /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0
* * * * exit 0
* * else
* * * * # more than one KDE session - just send shutdown signal to all of them
* * * * /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
* * fi
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

```


Can anyone tell if that script is wrong or am I on totally the wrong track?

Thanks in advance.

---

### Post by hansdown on 2009-01-25
Hi  Chris Musampa.

If you go to KDE Control Panel->Display->Power Control is there a shut down option when power button is pressed?

---

### Post by Chris Musampa on 2009-01-25
No Hansdown there isn't, should there be?

---

### Post by hansdown on 2009-01-25
I wasn't sure if kde has that, I use gnome.

---

