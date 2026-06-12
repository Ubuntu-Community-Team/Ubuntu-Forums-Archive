---
title: "help with powernow"
date: 2006-03-15
forum: Desktop Environments
---

### Post by deathbyswiftwind on 2006-03-15
Is there anyway to configure powernow to be more sensative? sometimes when i need the extra power boost of my 64bit it wont kick up the speed for a while. im looking for performance now not in 5 minutes when the system finally sees my need for it.

---

### Post by engla on 2006-03-15
Yes, it should be possible

First, if you want some information you can read the man page.. "man powernowd" (or you can open the Help viewer in ubuntu and find the man page there)

Then, looking at the service script for this service, it's /etc/init.d/powernowd

The top of this file looks like this. Notice the part in bold.
> #! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/powernowd
NAME=powernowd
DESC=powernowd

test -x $DAEMON || exit 0

[B]# create the file /etc/default/powernowd if you want to override the value of
# variable OPTIONS and change the default behavior of the daemon as launched[/B]

OPTIONS="-q"


So you need to create the file /etc/default/powernowd like this:
```

# in /etc/default/powernowd
# Some options to make it more agressive
OPTIONS="-q -p 500 -m 1"

```

This should make it poll every half sec (-p 500 milliseconds) and be agressive (-m 1 is agressive). The agressive part is already the default, so I don't know if this is really going to make a difference!


So, in the light of the above rant/tip this might not be the trouble. On my machine, a PPC G4, powernowd does all the work, however on many others centrino/etc, there is another kernel module that does this, and that might be the cause
you can also try this, to make it use a different "scaling governor"
```
$ cd /sys/devices/system/cpu/cpu0/cpufreq
$ cat scaling_available_governors
//comment This should list available "governors". Probably you have performance, conservative etc
$ cat scaling_governor
//comment This prints what is active right now.. when powernowd does the work, this might be "userspace"
//comment Now, if you want to try to change this, try this: 
$ sudo -s
//comment input your pass, you get a root shell
#echo "performance" > scaling_governor
#exit
//comment verify that it works
$ cat scaling_governor

```

edit: If changing the scaling_governor does the trick, you will have to make a startup script that changes it after every reboot.
I'm not really sure how to do that :)

---

### Post by IGNIZ on 2006-03-15
for the scaling governor there is the gnome applet

---

### Post by engla on 2006-03-15
[QUOTE=IGNIZ]for the scaling governor there is the gnome applet[/QUOTE]
Aha, but it only shows the scaling governor, it can't change it right? I can't on my setup at least.

Hovering over the cpu scaling applet displays the governor, in my case "Userspace"

---

### Post by IGNIZ on 2006-03-17
u have to chmod it so u can change it, if u search something like chmod scaling applet you should find it in the forum

---

