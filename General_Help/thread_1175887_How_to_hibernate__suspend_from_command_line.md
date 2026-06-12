---
title: "How to hibernate / suspend from command line?"
date: 2009-06-01
forum: General Help
---

### Post by fermulator on 2009-06-01
I've an interesting follow-up to this solution.  Hopefully someone can shed some light for me.

Sometimes, I'll [WoL]("http://www.raneri.it/blog/eng/index.php/2008/12/14/enable-wake-on-lan-wol-on-an-ubuntu-pc/") my system, login through SSH, and want to re-suspend the system.  Of course, since I'm not in GNOME, I can't use the GUI command, but the "sudo pmi action suspend" command works well.

Unfortunately, I'm lazy.  I'd like to create a small script:
Location: **/usr/local/bin/suspend**
Contents:
> #! /bin/bash

# Suspend the system
/usr/sbin/pmi action suspend

 * Save the file.  Great.
 * Set permissions:
```
sudo chmod +x /usr/local/bin/suspend
```

When I load up a new shell, I can type
```
which suspend
``` and it returns > /usr/local/bin/suspend.  OK.

Now, if I try
```
suspend
```
the shell hangs.  I can't press CTRL-C, CTRL-Z, nothing.  Must close gnome-terminal and open a new one.

If I try
```
sudo suspend
```
the system suspends.

Some troubleshooting, if I try
```
/usr/sbin/pmi action suspend
```
the system suspends.

I don't understand why if I run the command as a regular user it works, but if I run a script (which only runs that same command), it hangs the terminal and the system doesn't suspend.

I've tried adding "sudo" to the front of the script, "&" after the command, and "exit" at the end of the script (in various combinations), but nothing seems to prevent the script from hanging if it's executed without sudo privileges.

Any idea why/how this could happen?

---

### Post by ibuclaw on 2009-06-01
Post moved to own thread.

This is a continuation of this thread here: [http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

@fermulator,

You can suspend/hibernate your system via dbus signals. No use of root/sudo is needed to do this.
See this post of reference for some more information: [http://ubuntuforums.org/showpost.php?p=6788504&postcount=2](http://ubuntuforums.org/showpost.php?p=6788504&postcount=2)

But the general gist of going about it is as follows.

To Suspend:
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal \
    /org/freedesktop/Hal/devices/computer \
    org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0
```

To Hibernate:
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal \
    /org/freedesktop/Hal/devices/computer \
    org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate
```

To Hybrid Suspend/Hibernate (if your machine supports it):
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal \
    /org/freedesktop/Hal/devices/computer \
    org.freedesktop.Hal.Device.SystemPowerManagement.SuspendHybrid int32:0
```
Regards
Iain

---

### Post by fermulator on 2009-06-01
Oh interesting!

Thanks so much.

Also, I just tried creating a simple alias in my .bash_aliases file:
```
alias suspend='pmi action suspend'
```

This works 100% without problems too.  I have no idea why the script method didn't work, but I'm find with an alias. :-)

---

### Post by fermulator on 2012-03-29
NOTE: At some point this pmi binary was removed (not included by default).  it should be part of the powermanagement-interface deb package.

---

### Post by CharlesA on 2012-03-29
> **fermulator said:**
> NOTE: At some point this pmi binary was removed (not included by default).  it should be part of the powermanagement-interface deb package.
You just have to instlal a different package.

[http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line](http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line)

---

