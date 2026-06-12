---
title: "Conky and hddtemp as non-root user"
date: 2006-10-22
forum: Desktop Environments
---

### Post by tturrisi on 2006-10-22
**How To get conky to display hard drive temperature as a non-root user**

**Caveat:**
hddtemp requires root privledges to use.

**Workaround:**
use netcat as a non-root user to obtain the hard drive temperature.

**Prerequisites:**
1. conky installed & working
$apt-get install conky
2. hddtemp installed
$apt-get install hddtemp

*note: this guide is if have one hard drive though can be modified to use more than one hard drive.*

**config hddtemp to run as a daemon:**
# sudo gedit /etc/default/hddtemp
```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# Master system-wide hddtemp switch. The initscript will not run if it is not
# set to true. STOP THE SERVICE BEFORE DISABLING IT!

# [automatically edited by postinst, do not change line format or set it to
# anything but false or true ]
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/hda"  [COLOR="Red"]# your hard drive here hda or hdb etc.[/COLOR]

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures.
SYSLOG="300"  [COLOR="Red"]# 300 = every 5 minutes; default is 0, thus no logging occurs.[/COLOR]

# Other options to pass to hddtemp
OPTIONS=""
```

**edit your .conkyrc**
$ gedit .conkyrc

add this line in the TEXT section:
```
TEXT
Hard Drive Temp: ${execi 300 nc localhost 7634 | cut -b29-30 ;}C
```

What it does:
The conky command $execi executes netcat at an interval of 5 minutes at localhost on the port used by conky 7634 and the result is cut to only the number value, the 29th & the 30th characters of the netcat result above, the hd temp.

example netcat result:
|/dev/hda|FUJITSU MHT2060AT|44|C|

**determine YOUR cut values to use**
Why? Because the result will be the model name of your hard drive and not all drives are the same!
$nc localhost 7634
count the characters in YOUR result and use those values in your .conkyrc

---

### Post by MeduZa on 2008-04-12
hi, I'm working on the same problem, this version works for all the disk's model:

nc localhost 7634 | cut -d"|" -f4

the problem is that I have 3 harddrives I need 3 diferent cuts. first at 4 and every five spaces (next one at 9)


Salutes

---

### Post by Velociraptor on 2008-04-19
You can also configure hddtemp so that you don't need the sudo. Run:

**sudo dpkg-reconfigure hddtemp**

---

