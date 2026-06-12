---
title: "reboots every 61 +/- minutes"
date: 2008-11-03
forum: Desktop Environments
---

### Post by dgermann on 2008-11-03
Hi--

I reported this problem at the first of the year in [this thread ]("http://ubuntuforums.org/showthread.php?t=659354").

What happens is that at almost exactly every 61 minutes, the computer reboots. I am now running 8.04.1. It usually goes away after a day--now it is into the second day, and it is disconcerting to be in the middle of something and have it shut down!

Here's what happens, in case it is a clue: I will be sitting typing away and then I hear the computer fan start up. I can save a document--I appear to have about 3 to 5 seconds, and then it goes into a reboot.

Here is the latest string of reboots:
```
doug@doug2:~$ last reboot
reboot   system boot  2.6.24-19-generi Mon Nov  3 20:41 - 20:48  (00:06)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 20:22 - 20:39  (00:16)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 19:22 - 20:39  (01:16)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 18:25 - 20:39  (02:13)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 17:21 - 17:47  (00:25)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 16:21 - 17:47  (01:25)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 15:21 - 17:47  (02:25)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 14:20 - 17:47  (03:26)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 13:20 - 17:47  (04:26)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 12:20 - 17:47  (05:26)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 11:20 - 17:47  (06:27)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 10:15 - 17:47  (07:31)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 09:15 - 17:47  (08:31)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 08:28 - 09:13  (00:44)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 07:28 - 09:13  (01:44)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 06:28 - 09:13  (02:45)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 05:27 - 09:13  (03:45)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 04:27 - 09:13  (04:45)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 03:27 - 09:13  (05:45)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 02:26 - 09:13  (06:46)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 01:26 - 09:13  (07:46)    
reboot   system boot  2.6.24-19-generi Mon Nov  3 00:26 - 09:13  (08:46)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 23:26 - 09:13  (09:47)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 22:25 - 09:13  (10:47)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 21:25 - 09:13  (11:47)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 20:25 - 09:13  (12:48)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 19:35 - 09:13  (13:37)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 18:24 - 09:13  (14:48)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 17:24 - 09:13  (15:48)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 16:23 - 09:13  (16:49)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 15:23 - 09:13  (17:49)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 14:23 - 09:13  (18:49)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 13:23 - 09:13  (19:50)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 12:25 - 09:13  (20:47)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 11:22 - 09:13  (21:50)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 10:22 - 09:13  (22:51)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 09:21 - 09:13  (23:51)    
reboot   system boot  2.6.24-19-generi Sun Nov  2 08:21 - 09:13 (1+00:51)   
reboot   system boot  2.6.24-19-generi Sun Nov  2 07:21 - 09:13 (1+01:51)   

wtmp begins Sun Nov  2 07:21:20 2008
doug@doug2:~$ 

```

See anything that is a clue?

Thanks!

---

### Post by bwhite82 on 2008-11-03
Thats odd, is there some rogue cron job doing it?

Check in the cron directories /etc/cron.hourly (for instance) and look at /etc/crontab just to make sure.

Edit: sorry, just saw your other thread...hmmm....very odd...

---

### Post by bwhite82 on 2008-11-03
I concur with others in the other thread, it is either hardware (power supply) or the power source itself, do you have an UPS to try on the machine?

---

### Post by dgermann on 2008-11-03
Soldierboy--

Thanks for jumping in!

Yup, tell me how odd it is.

Here are some things I checked out:
```
doug@doug2:~$ cat /var/spool/cron/*
cat: /var/spool/cron/atjobs: Permission denied
cat: /var/spool/cron/atspool: Permission denied
cat: /var/spool/cron/crontabs: Permission denied
doug@doug2:~$ sudo ls -alh /var/spool/cron/atjobs
[sudo] password for doug: 
total 12K
drwxrwx--T 2 daemon daemon 4.0K 2007-12-05 21:42 .
drwxr-xr-x 5 daemon daemon 4.0K 2007-12-05 21:40 ..
-rw------- 1 daemon daemon    2 2007-12-05 21:42 .SEQ
doug@doug2:~$ sudo less /var/spool/cron/atjobs/.SEQ
doug@doug2:~$ sudo cat /var/spool/cron/atjobs/.SEQ
0
doug@doug2:~$ sudo ls -alh /var/spool/cron/atspool/
total 8.0K
drwxrwx--T 2 daemon daemon 4.0K 2007-02-20 08:41 .
drwxr-xr-x 5 daemon daemon 4.0K 2007-12-05 21:40 ..
doug@doug2:~$ sudo ls -alh /var/spool/cron/crontabs/
total 16K
drwx-wx--T 2 root   crontab 4.0K 2008-10-22 18:27 .
drwxr-xr-x 5 daemon daemon  4.0K 2007-12-05 21:40 ..
-rw------- 1 doug   crontab  230 2008-10-22 18:20 doug
-rw------- 1 root   crontab 1.4K 2008-10-22 18:27 root
doug@doug2:~$ sudo cat /var/spool/cron/crontabs/doug
# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.PdhP42/crontab installed on Wed Oct 22 18:20:22 2008)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
# m h  dom mon dow   command
doug@doug2:~$ sudo cat /var/spool/cron/crontabs/root
# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.Brwdy5/crontab installed on Wed Oct 22 18:27:55 2008)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
# m h dom mon dow
7 0 * * * /etc/webmin/cron/tempdelete.pl
# * * * * * touch /sam/vol22/data/todo/bak/2crontest

####copied from sdb1 (old drive) and refers there 20071208: did not
 work so commented out for now; changed to new locations 20071210:

0 * * * * /usr/sbin/esets_update
# * * * * * root /usr/bin/touch /sam/vol22/data/todo/bak/1crontest

##############ddg 20061113 updated for new directories 20071210:

#0 3 * * * /usr/sbin/esets_scan -l --mail –unsafe / -- -/dev* 
-/proc* -/sam* -/media/sdb1/dev* -/media/sdb1/proc* 
-/media/sdb1/sam*


###20080715 ddg:
#0 3 * * * /usr/sbin/esets_scan -f /var/log/esets/scan.log / 
--exclude /dev /proc /sam
0 3 * * * /etc/cron.doug/eset
#0 21 * * * /etc/cron.doug/eset
###
#30 * * * *         cp -pru ~doug/.evolution /sam/vol22/comm/evo/
30 * * * *         rsync -a --delete ~doug/.evolution/ /sam/vol22/comm/evo

#######added by ddg 20080115:
21 15 * * *     root     cp -u /sam/vol22/data/ts/TSBACKUP.BKU ~doug

#######end of addition 20080115

###added by ddg 20080120:
31 01 18 1,3,5,7,9,11 * /etc/cron.doug/bkmonthone
31 01 18 2,4,6,8,10,12 * /etc/cron.doug/bkmonthtwo
# 31 01 18 3,6,9,12 * /etc/cron.doug/bkmonththree
###





doug@doug2:~$
```

Also this: 
```

doug@doug2:~$ ls -alh /etc/cron.monthly/
total 32K
drwxr-xr-x   2 root root 4.0K 2008-09-07 21:37 .
drwxr-xr-x 149 root root  12K 2008-11-02 18:24 ..
-rwxr-xr-x   1 root root  313 2007-03-05 01:38 0anacron
-rw-r--r--   1 root root  102 2006-12-20 09:46 .placeholder
-rwxr-xr-x   1 root root  106 2007-12-06 08:21 scrollkeeper
-rwxr-xr-x   1 root root  129 2006-12-20 09:46 standard
doug@doug2:~$ less /etc/cron.monthly/0anacron 
doug@doug2:~$ cat /etc/cron.monthly/0anacron 
#!/bin/sh
#
# anacron's cron script
#
# This script updates anacron time stamps. It is called through run-parts
# either by anacron itself or by cron.
#
# The script is called "0anacron" to assure that it will be executed
# _before_ all other scripts.

test -x /usr/sbin/anacron || exit 0
anacron -u cron.monthly
doug@doug2:~$ cat /etc/cron.monthly/.placeholder 
# DO NOT EDIT OR REMOVE
# This file is a simple placeholder to keep dpkg from removing this directory
doug@doug2:~$ cat /etc/cron.monthly/scrollkeeper
#!/bin/sh

set -e

[ -x /usr/bin/scrollkeeper-rebuilddb ] || exit 0

umask 022
scrollkeeper-rebuilddb -q

doug@doug2:~$ cat /etc/cron.monthly/standard 
#!/bin/sh
# /etc/cron.monthly/standard: standard monthly maintenance script

# rotation of wtmp and btmp taken over by logrotate
doug@doug2:~$
```

I have checked all sorts of things and nothing makes sense! I have for instance a UPS on this line, and there is nothing in the logs about power problems at these times. I have other machines in this same building, and they do not reboot every hour.

The fact that it is around the first of the month and that it lasts for a day or so, suggests software somewhere.

---

### Post by stinger30au on 2008-11-03
if you have a ups connected to the pc and im also assuming you have the pc connect to the ups for not only backup power but you have a usb or serial cable attached as well to the ups


have you checked the software settings in the ups. it may be getting low or high power surges and causing it to tell the pc to restart????

---

### Post by dgermann on 2008-11-03
stinger30au--

Thanks for jumping in.

There is a ups on the system, using apcupsd. The events log shows:

```
Wed Oct 29 14:44:11 EDT 2008  apcupsd shutdown succeeded
Mon Nov 03 09:13:21 EST 2008  apcupsd exiting, signal 15
Mon Nov 03 09:13:21 EST 2008  apcupsd shutdown succeeded
Mon Nov 03 17:47:23 EST 2008  apcupsd exiting, signal 15
Mon Nov 03 17:47:23 EST 2008  apcupsd shutdown succeeded
Mon Nov 03 20:39:21 EST 2008  apcupsd exiting, signal 15
Mon Nov 03 20:39:21 EST 2008  apcupsd shutdown succeeded
(END) 
```
This shows only the times I actually shut the machine down manually. No power failures are indicated.

The apcupsd.conf file is just the standard stuff:
```
doug@doug2:~$ cat /etc/apcupsd/apcupsd.conf
## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.14.1 (04 May 2007) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
# UPSCABLE smart
UPSCABLE usb

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
# UPSTYPE apcsmart
# DEVICE /dev/ttyS0
UPSTYPE usb
# DEVICE 

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc


#
# ======== Configuration parameters used during power failures ==========
#

# The ONBATTERYDELAY is the time in seconds from when a power failure
#   is detected until we react to it with an onbattery event.
#
#   This means that, apccontrol will be called with the powerout argument
#   immediately when a power failure is detected.  However, the
#   onbattery argument is passed to apccontrol only after the 
#   ONBATTERYDELAY time.  If you don't want to be annoyed by short
#   powerfailures, make sure that apccontrol powerout does nothing
#   i.e. comment out the wall.
ONBATTERYDELAY 6

# 
# Note: BATTERYLEVEL, MINUTES, and TIMEOUT work in conjunction, so
# the first that occurs will cause the initation of a shutdown.
#

# If during a power failure, the remaining battery percentage
# (as reported by the UPS) is below or equal to BATTERYLEVEL, 
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 5

# If during a power failure, the remaining runtime in minutes 
# (as calculated internally by the UPS) is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 3

# If during a power failure, the UPS has run on batteries for TIMEOUT
# many seconds or longer, apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
#
#  Note, if you have a Smart UPS, you will most likely want to disable
#    this timer by setting it to zero. That way, you UPS will continue
#    on batteries until either the % charge remaing drops to or below BATTERYLEVEL,
#    or the remaining battery runtime drops to or below MINUTES.  Of course,
#    if you are testing, setting this to 60 causes a quick system shutdown
#    if you pull the power plug.   
#  If you have an older dumb UPS, you will want to set this to less than
#    the time you know you can run on batteries.
TIMEOUT 0

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 60

# The condition which determines when users are prevented from
# logging in during a power failure.
# NOLOGON <string> [ disable | timeout | percent | minutes | always ]
NOLOGON disable

# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 0

#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  This is useful if your server is multi-homed (has more than one
#  network interface and IP address). Default value is 0.0.0.0 which
#  means any incoming request will be serviced. Alternatively, you can
#  configure this setting to any specific IP address of your server and 
#  NIS will listen for connections only on that interface. Use the
#  loopback address (127.0.0.1) to accept connections only from the
#  local machine.
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

#
# ========== Configuration statements used if sharing =============
#            a UPS with more than one machine

# NETTIME <int>
#   Interval (in seconds) at which the NIS client polls the server.
#   Used only when this apcupsd is a network client (UPSTYPE net).
#NETTIME 60

#
# Remaining items are for ShareUPS (APC expansion card) ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster ]
#   Normally standalone unless you share an UPS using an APC ShareUPS
#   card.
UPSCLASS standalone

# UPSMODE [ disable | share ]
#   Normally disable unless you share an UPS using an APC ShareUPS card.
UPSMODE disable

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if         
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog. 
#          If not specified, it defaults to "daemon". This is useful 
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters 
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery charge needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336
doug@doug2:~$ 

```

There is no indication I can see of problems with the ups nor with the power. If there were, why every 61 minutes, why only the first through the third of the month? This is a puzzler....

I'm also wondering--could it be some glitch in cron or anacron? Would it be something to try to kill cron and restart it when this happens?

BTW, it seems to have gone to sleep now for this month...no reboots the last hour or so.

---

### Post by gpsmikey on 2008-11-03
There may be something else on that circuit that causes it to reboot.  I am fairly sure it couldn't be a cron job of any kind since if it was, the time increment would stay the same, and it doesn't -- usually, 61 minutes, but there are a number of them that are off by 10-15 minutes.  Try moving it to a different circuit in the house (not just a different outlet) and see if that changes it.  You might also try opening the case up and setting a fan up to blow in there - see if that changes it (then there is my favorite - a can of compressed air to make sure the cooling fins etc are clear - including inside the power supply).  It may be internal, but I'm pretty sure it is not related to any kind of timer application (like cron) since it has those strange jumps that are different from the others.

mikey

---

### Post by detroit/zero on 2008-11-03
I'd say it's a thermal problem before anything, based on the fact that his fan kicks on before it does its' shutdown routine. My wifes' Acer occasionally hits the 100°C mark and her computer shuts down **right now** - no warning, no nothing.

Does it do this (60 min shutdown) every 60 minutes no matter what? Or is it 60 minutes from the time you turn it on? e.g., if you shut down after 45 minutes of use, and re-boot at a later time, do you now have 15 minutes of time left before random shutdown time, or the full 60?

When's the last time you had the case open? Is everything clean and dust-free? In other words, is there good air flow inside the thing? You haven't got the thing parked next to a heater vent or something, have you?

Is the CPU seated properly? If it's loose just one fraction of a smidgen (a highly technical term, I know..) when it gets hot and expands it could be just enough movement to break or degrade a connection.. If you've never had it out or otherwise messed with it, it's probably safe to assume it's seated in its' socket the way it should be.

How about the heat sink for the CPU? Is it tightened down properly and making good contact with the chip? Ever try putting a dab of [heat-sink compound]("http://http://www.radioshack.com/product/index.jsp?productId=2102858") on it?

What about jumpers and wires? Are all your pin jumpers set firmly? Are all your wires and connections in good shape, i.e., clean, corrosion-free, no bare wires or exposed strands, etc..?

Last but not least, and assuming it's software and not hardware related - have you tried re-installing the OS? My god, man! You've been dealing with this for almost a year now? As easy and quick as it is to install Ubuntu, I'd almost just do that to eliminate a possibility before I bothered to open my laptop and started poking around inside it.

You, sir, are definitely a glutton for punishment.

---

### Post by dgermann on 2008-11-03
mikey--

You may be on to something. The box is in a space with limited airflow (under my desk). 

It will take some investigating to see where I can find a different circuit, so that might make a difference.

On the other hand, why would that explain the first 2 or three days of the month?

The other issue is that it seems to have stopped for this month. So it may be that I will not have much to report till December! ;)

A couple of those reboots were done more or less manually--when it started to reboot, I killed the power and let it sit for a while, in the hopes that the break would jolt it. Then it started right in again 61 +/- minutes later. But it still varies, just a little bit.

Thanks for helping, mikey! I will try the fan and compressed air and look for a different circuit.

---

### Post by dgermann on 2008-11-03
detroit/zero--

A glutton for punishment, eh? :lolflag:

Good ideas.

I've not tried reinstalling the OS, unless upgrading from Gutsy to Hardy counts. Is that something easy to do, given that there is a lot of customization here--to say nothing of data files? For instance, I have nVidia for dual screens on this desktop system, and a handful of cron files (which are not related to this issue), etc. I presume it is more than just going to synaptic and reinstalling....

Yes, if I unplug and wait 15 minutes, I get a full 61 minutes or so, and then it goes down again. Which sounds like a heat problem. Isn't there a heat monitor somewhere on this system?

But if heat is the problem, why every first three days of the month? Granted, it is warm here in the midwest the last couple of days--around 70 degrees--but we had hotter in July and August.

Since I do not know what a heat sink is, I probably have not put any heat sink compound on it! ;)

I'll pop the lid and see what dust bunnies I can capture and what cables, etc., might be loose....

Thanks, detroit/zero!

---

### Post by kb2001 on 2008-11-03
Everything you've posted, in both threads, points to hardware issues.  When your fan kicks on (aka, another piece of hardware starts working), your computer shuts off.  Can you check BIOS for heat warnings?  Can you unplug the fan that kicks on and see what you get?  If you have smart hardware, the OS can interact with it for temperature readings.  Image your drive off (P.I.N.G. is a good imaging tool, do all partitions), install something else (like Fedora for example) and see if you get the same behavior.  I wouldn't expect the interval to be the same 61 minutes, but I would expect the interval to be precise (maybe 45 minutes every time, or 80 minutes every time).  Boot to a live CD and see what you get.  Take the side off, get a box fan and blow it in there and see what you get.  Hell, put windows on it and see what you get.  Your current installation is already imaged, so no worries about recovering your system.

Isolate the problem to identify it, and take steps to remove it.  It sounds like a hardware problem, so start by removing the OS as a factor and see if you get similar results.

---

### Post by detroit/zero on 2008-11-04
> **dgermann said:**
> detroit/zero--

A glutton for punishment, eh? :lolflag:

Good ideas.

I've not tried reinstalling the OS, unless upgrading from Gutsy to Hardy counts. No, that wouldn't really count. In an upgrade, you'd be taking any screwed up config files or cron jobs with you to your new OS. It's kind of tricky to recommend a fresh install and restoring your files from backups, because if you backup your cron jobs, for example, and the problem happens to be there (even though nobody sees it) you'll be right back in the same boat. I know it's a pain to go through all the setup procedures to get everything back the way you need/want it, but if you do a re-install, stick with backing up Pics, Docs and items of value, go for the gold and start the system fresh.> **dgermann said:**
> Yes, if I unplug and wait 15 minutes, I get a full 61 minutes or so, and then it goes down again. Which sounds like a heat problem. Isn't there a heat monitor somewhere on this system?Well, if your system can detect when it overheats and shut itself down, then yes, there's a monitor there. Whether or not it's a supported chipset is a different story. 

Try this. At a terminal ```
sudo apt-get install lm-sensors
```and once the program finishes installing, run ```
sensors-detect
``` It'll take you through a handful of questions while it tries to detect your hardware. Basically, type out "yes" to all the questions, and see what it gives you. I say type it out, because at the very end is a question about loading the sensors kernel module(s) automatically at startup, and the default answer is not yes.

After that's all done, and assuming you have supported hardware, it's as easy as typing ```
sensors
``` at a command prompt and reading the output. Here's all I get from mine when I run it: ```
zero@zero-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +57.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (crit = +100.0°C)
```but some people get way more detailed results, including voltage readings, fan states (on/off), fan RPMs, etc, etc..

Once you get lm-sensors in place, there are panel applets that give real-time readouts, there's an applet for AWN if you use that, and there's always Conky for you to use to keep an eye on it.
[RIGHT][LEFT][[IMG]http://img90.imageshack.us/img90/273/screenshotta0.th.png[/IMG]]("http://img90.imageshack.us/my.php?image=screenshotta0.png") 
While you're at it, you might as well also install hddtemp to keep an eye on your hard disk temps:```
sudo apt-get install hddtemp
```That one will work straight away without any detection process (again, if you have supported hardware) but you need to run it as sudo ```
sudo hddtemp
``` You can change this by using ```
chmod u+s /usr/sbin/hddtemp
```Then it's as easy as ```
zero@zero-laptop:~$ hddtemp /dev/sda
/dev/sda: Hitachi HTS541612J9SA00: 40°C

```There's also a panel applet for that, and it does read out in Conky. I don't think AWN has an applet, though.> **dgermann said:**
> But if heat is the problem, why every first three days of the month? Granted, it is warm here in the midwest the last couple of days--around 70 degrees--but we had hotter in July and August.I couldn't even venture a guess. Maybe the moon's gravitational pull those particular days? Gremlins? Elves? Aliens? Beats me...> **dgermann said:**
> Since I do not know what a heat sink is, I probably have not put any heat sink compound on it! ;)A heat sink is a big chunk of aluminum or copper or something attched to the top of your cpu that draws heat away from the CPU and aids in cooling. In desktops (at least in the ones I've seen, anyways) it's usually a chunk of aluminum with a bunch of fins to increase surface area to aid the dissipation of heat. In most laptops, it's a network of small copper tubes that run from whereever the CPU is over to that little air vent and the fan is. It may or may not have a fan built into it - there's [a million different kinds]("http://images.google.pl/images?q=heat%20sink&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wi"). Heat sink compound is just a thermally-conductive grease to increase the transfer of heat from the surface of the chip to the heat sink so it can be cooled by airflow.[/LEFT]
 [/RIGHT]
> **dgermann said:**
> 
 
I'll pop the lid and see what dust bunnies I can capture and what cables, etc., might be loose....

Thanks, detroit/zero!Cleaning - That's the best place to start. Don't just use compressed air, though - you're just blowing the dust around and you'll end up breathing it in and all that. I always use a vacuum cleaner with a brush attachment when I clean mine. Be as gentle as possible is the best advice I can give if you're going to do it that way.

Good luck, and let us know what happens..

---

### Post by bwhite82 on 2008-11-04
Is this machine at your work or home?

---

### Post by gpsmikey on 2008-11-04
I should have mentioned -- take it outside to blow the dust out of it !!  I prefer not to use a vacuum around the systems because you can get significant static buildup on the attachments for the vacuums and static discharges and semiconductors do not go well together !!  Especially if you have pets in the house, you will likely find the fins on the heatsinks for the processor etc plugged with dust/hair.

mikey

---

### Post by ZootNerper on 2008-11-05
The cheapest way to keep your PC cool is to take at least one side off (I permanently have both off). Try that and see if it changes the time to shutdown.

-- Zoot

---

### Post by dgermann on 2008-11-05
Hi all--

Well, as the pattern has been, the machine has now not rebooted in 50 hours. So it might be the first of December before the pattern repeats.

Just so you get a picture of the setting: This is a production machine in an office setting.

It is under the desk on its side. The desk has two "pedestals" which are the drawers hanging from the desktop. The computer is under one of these pedestals, laying on its side. The side it is laying on is solid with no air vents in it.

There is a 1.5 inch gap between the top of the computer (the side with all the air vents and fan) and the bottom of the pedestal. The computer is about 6 inches from the side wall, 10 inches from the back wall. The other two sides are open to where my feet are and to the rest of the room, respectively. The nearest heat vents are 6 feet and 10 feet away.

The airflow around this area of the desk is not obstructed, and I think it flows freely.

kb2001 --

Thanks for your ideas.

"Can you check BIOS for heat warnings?" How do I do that?

"If you have smart hardware, the OS can interact with it for temperature readings." How do I know? Perhaps the copied material below answers this?

Thanks for the info about P.I.N.G.--I found their website.

detroit/zero--

I installed lm-sensors and got this error message. What do you suggest?

```
doug@doug2:~$ sudo sensors-detect
[sudo] password for doug: 
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): 
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: SMBus I801 adapter at 2000 (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC8374L Super IO Sensors'                 
    (but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): 
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
doug@doug2:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
doug@doug2:~$ 

```

Soldierboy--

Office.

gpsmikey--

Good idea! Thanks!

It may be raining/snowing this weekend, which might limit my ability to do this. No pets in here, though!

ZootNerper--

Excellent idea!

Everybody--

Any suggestions what to do now that it has settled down?

Would it make sense to reset the OS time to November 1 and see what happens? Or should I reset the bios time to November 1 instead? Or both? Or just wait till December?

Thank you all for all your help. You have so many good ideas it is hard to keep up with you!

---

### Post by detroit/zero on 2008-11-06
> **dgermann said:**
> detroit/zero--

I installed lm-sensors and got this error message. What do you suggest?
[...]

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
doug@doug2:~$ sensors
No sensors found!
** Make sure you loaded all the kernel drivers you need.**
Try sensors-detect to find out which these are.
doug@doug2:~$ 
[/code]
I'm assuming you didn't reboot or anything before that last command. As per the last question, the coretemp module has been added to etc/modules for the kernel to load the next time you do reboot, but that doesn't do anything for you right now.

Run```
sudo modprobe coretemp
```to load the module.These two might not be needed, but just to make sure run```
sudo depmod -a
```to update any dependencies, and then```
sudo update modules
```

Then run sensors. Should work now.

---

### Post by bwhite82 on 2008-11-06
So this is an office **networked** machine? The reason I ask is perhaps the sysadmin has some kind of shutdown script, or someone remoting into the box as a prank and shutting it down?

Sorry if this sounds far-fetched, I'm throwing everything out on the table. :)

---

### Post by dgermann on 2008-11-06
detroit/zero--

Thanks for being my tutor!

Here's what I get:
```
doug@doug2:~$ sudo update modules
sudo: update: command not found
doug@doug2:~$ sudo update-modules

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

doug@doug2:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (crit = +85.0°C)                  

doug@doug2:~$ 

```

So that looks pretty good for temperatures, bad for telling us where the problem is. Except of course it has been days since the last reboot.

Thanks, detroit/zero!

Soldierboy--

Yup, networked. I am the sysadmin, such as there might be in these parts. No one else here knows enough to play such a joke. (I hope.) The machine is firewalled, and is behind a router, so it seems unlikely an attack from outside.

Good ideas. Thanks, Soldierboy!

---

### Post by HyperHacker on 2008-11-07
Next time it happens, could you try running without the network cable plugged in and see what happens? A hardware issue alone sure seems odd for something that happens with such precise timing, although it could be a timed event triggering a hardware problem.

---

### Post by y@w on 2008-11-07
If it starts doing it again, why not just run it off a live CD for a couple of hours? If it stops rebooting without changing anything else then you can rule out hardware.. Except for maybe a hard drive, I suppose.

---

### Post by gimmejimmy on 2008-11-07
Do you have something like AMD Cool n Quiet or Intel Speedstep?

---

### Post by funchords on 2008-11-08
Is this machine any kind of a server that might be rebooting if it can't contact (or be contacted by) another machine?  (aka a "watchdog" feature).

---

### Post by dgermann on 2008-11-08
HyperHacker--

Thank you for this idea. It is worth a try....

y@w--

Thanks. I was considering that--but would that not rule out software problems more than hardware?

gimmejimmy--

Gee, I don't know what those are. How would I tell?

Thanks!

funchords--

No, I don't think so. I do not know what a watchdog feature is, so I am unsure. There were a couple of things where it is a server--such as for openvpn, but I only added that a couple of months ago--this problem predates that. It may be a samba server.

Would those be any clues?

Thanks, funchords.

---

### Post by seldon77 on 2008-11-14
I wonder if your CMOS is set up to shutdown/reboot if temperature gets above a certain level. So, then your computer slowly builds up temperature until the reboot, which would explain the fan also going faster.

You should be able to change the CMOS setting at boot-up.

---

### Post by dgermann on 2008-11-15
seldon77--

That is entirely possible.

I have added a computer temperature monitor to my panel (usually runs at or below 30 degrees celsius) and will switch it to log the temps to a text file when we get to the first of the month when this problem repeats.

I looked into bios a few days ago when I last rebooted and saw nothing that would reboot the machine, but was not specifically looking for temperature so I will look for that next reboot.

Thanks, seldon77!

---

### Post by zaadjis on 2008-11-25
seems i have the same problem with my work computer.

started last month when i left my comp on over the weekend (still on hardy):
<snip>
reboot   system boot  2.6.24-21-generi Sat Oct 18 17:52 - 14:14 (1+20:22)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 16:51 - 14:14 (1+21:22)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 15:51 - 14:14 (1+22:23)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 14:51 - 14:14 (1+23:23)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 13:51 - 14:14 (2+00:23)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 12:50 - 14:14 (2+01:24)   
reboot   system boot  2.6.24-21-generi Sat Oct 18 11:50 - 14:14 (2+02:24)   
reboot   system boot  2.6.24-21-generi Fri Oct 17 09:50 - 14:14 (3+04:24)   
reboot   system boot  2.6.24-21-generi Thu Oct 16 09:54 - 18:12  (08:17) 

proplem stopped on the following tuesday (weird, i know)

now it's back (on intrepid), have 2 minutes to finish this post, before my next reboot, so detailed info later.

===
so it started this morning after dehibernation (first time i used it on intrepid). turned the comp on at 10:26, and now i have to save all my work no later than 25 past the hour (funny, i know).

not caused by:
* cronjobs (only system defauts, no custom scripts)
* network (pulled the cable 2 mins before reeboot, just to rule out)
* heat (sensors reported +42.0°C..+43.0°C)

i do have a UPS however, so now i turned it off and plugged the comp into grid directly. will report if that changes anything.

===
ok, disconnecting the UPS didn't help. starting to supsect software updates (or the de-hibernation).

software updates made today:

manual:
-------
Upgraded the following packages:
libpq-dev (8.3.4-2.2) to 8.3.5-0ubuntu8.10
libpq5 (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-8.3 (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-client-8.3 (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-contrib (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-contrib-8.3 (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-doc (8.3.4-2.2) to 8.3.5-0ubuntu8.10
postgresql-doc-8.3 (8.3.4-2.2) to 8.3.5-0ubuntu8.10

unattended:
-----------
2008-11-25 11:00:26,348 INFO Packages that are upgraded: openoffice.org-base libwebkit-1.0-1 libwebkit-dev openoffice.org-writer openoffice.org-report-builder-bin openoffice.org-officebean openoffice.org-filter-binfilter openoffice.org-emailmerge openoffice.org-draw openoffice.org-java-common openoffice.org-filter-mobiledev openoffice.org-calc openoffice.org-style-human openoffice.org-math openoffice.org-impress openoffice.org-gnome openoffice.org python-uno openoffice.org-common openoffice.org-gtk ttf-opensymbol openoffice.org-core openoffice.org-base-core

===
Left the computer off (no hibernation) yesterday when leaving the office and no reboots this morning, so looks like turning it off for a while helps. Best guess right now is that the problem's related to the power supply (hardware issue).

---

### Post by detroit/zero on 2008-11-25
Duh!

I just realized that was someone else.

Nevermind.

---

### Post by y@w on 2008-11-26
> **dgermann said:**
> 
y@w--

Thanks. I was considering that--but would that not rule out software problems more than hardware?


I had to read that like 10 times to make sure I said that right :) .. Yeah, if it stops rebooting when running from a live CD (effectively a fresh Ubuntu installation) should rule out a hardware issue.

Perhaps this might help you too.. It sounds like a similar issue only on Fedora. This person did a fsck on his/her filesystem on boot and it seemed to take care of it: [http://www.zimbra.com/forums/administrators/23837-fedora8-zimbra-reboots-every-hour-why.html](http://www.zimbra.com/forums/administrators/23837-fedora8-zimbra-reboots-every-hour-why.html)

---

### Post by bford16 on 2008-11-26
What a fascinating thread!  Did running fsck on boot do the trick?  And if so, why?  What kind of filesystem corruption would cause the computer to reboot regularly for three days, then stop?  I'll be checking back to see how this works out.

---

### Post by dgermann on 2008-11-27
Should start its antics again, if it will, in about 3 or 4 days. Will let you know.

You have all been so helpful with ideas to test. Thanks!

---

### Post by dgermann on 2008-12-25
Merry Christmas!

Here we go again. It skipped the rebooting at the first of the month, (preferring holidays?). For the record, here are the reboots:

```
doug@doug2:~$ last |grep boot
reboot   system boot  2.6.24-22-generi Thu Dec 25 12:39 - 12:54  (00:15)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 11:36 - 12:54  (01:18)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 10:35 - 12:54  (02:18)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 09:35 - 12:54  (03:19)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 08:35 - 12:54  (04:19)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 07:35 - 12:54  (05:19)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 06:34 - 12:54  (06:20)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 05:34 - 12:54  (07:20)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 04:34 - 12:54  (08:20)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 03:33 - 12:54  (09:20)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 02:33 - 12:54  (10:21)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 01:33 - 12:54  (11:21)    
reboot   system boot  2.6.24-22-generi Thu Dec 25 00:32 - 12:54  (12:21)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 23:32 - 12:54  (13:22)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 22:32 - 12:54  (14:22)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 21:32 - 12:54  (15:22)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 20:31 - 12:54  (16:23)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 19:31 - 12:54  (17:23)    
reboot   system boot  2.6.24-22-generi Wed Dec 24 18:31 - 12:54  (18:23)    
reboot   system boot  2.6.24-22-generi Tue Dec 23 10:31 - 12:54 (2+02:23)   
reboot   system boot  2.6.24-22-generi Sat Dec  6 11:21 - 23:18 (5+11:57)   
doug@doug2:~$ 

```

What I am seeing is the same pattern starting December 24 at 18:31. I do not recall the reboot at 10:31 am.

I did set up a script to capture the ps aux output every two seconds. Here is what it shows for the last entry before rebooting:

```
root      7214  0.0  0.0   3332   880 ?        S    12:29   0:00 hddtemp --syslog=5 /dev/sda1 /dev/sdb1
doug      7232  0.0  0.0   1772   492 ?        S    12:34   0:00 /bin/sh /home/doug/every60
doug      7237  0.0  0.0   1772   496 ?        S    12:34   0:00 /bin/sh /home/doug/every60
doug      7275  0.0  0.0   1772   496 ?        S    12:34   0:00 /bin/sh /home/doug/every60
doug      7451  0.0  0.0   3068   720 ?        S    12:35   0:00 sleep 2
doug      7454  0.0  0.0   3068   724 ?        S    12:35   0:00 sleep 2
doug      7456  0.0  0.0   2644  1004 ?        R    12:35   0:00 ps aux


^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@:

```

(I started the every60 script three times, not realizing it was running.) 

I do not know what those "sleep 2" entries are at the end--is that a clue?

There is quite a bit of that binary stuff following, and then a bunch of stuff that looks like this:

```
<bookmark:application name="File Manager" 
exec="&apos;openoffice.org2.3 -calc %U&apos;" timestamp="1203283282" count="2"/>
        </bookmark:applications>
      </metadata>
    </info>
  </bookmark>
 
```

Following that is a normal ps aux output with the boot up at 12:39.

syslog shows:

```
Dec 25 12:34:51 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:34:51 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:34:55 doug2 kernel: [ 3578.466418]  CIFS VFS: server not responding
Dec 25 12:34:55 doug2 kernel: [ 3578.466427]  CIFS VFS: No response for cmd 50 mid 5913
Dec 25 12:34:56 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:34:56 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:35:02 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:35:02 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:35:07 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:35:07 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:35:12 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:35:12 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:35:15 doug2 kernel: [ 3598.428064]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_
info in lookup of \data\m-esp
Dec 25 12:35:17 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:35:17 doug2 hddtemp[7214]: /dev/sdb1: WDC WD2000JS-00MHB0: 39 C
Dec 25 12:35:22 doug2 hddtemp[7214]: /dev/sda1: WDC WD800JD-60LSA5: 31 C
Dec 25 12:39:43 doug2 syslogd 1.5.0#1ubuntu1: restart.

```

I think that "CIFS VFS: server not responding" was when I unplugged the network cable to try to eliminate network activity as a factor. I plugged it back in to save a document and then unplugged again, which accounts I think for the second CIFS VFS entry.

Here we have the temperatures staying steady the whole time, and well under the critical level of 85 or so.

I am wondering how the different programs read temperatures, since the 39 degrees is higher than I have seen watching hwmon over the last month--currently hwmon shows 29 and 31 degrees while hddtemp shows 33 and 41. sensors show 29 and 31. But in any event, would you say we can rule out temperatures?

Next, I'm going to try to figure out how to do an fsck or e2fsck on these drives.

...time passes...

OK, here is what I did and what happened:

I went to safe mode and ran as root e2fsck -fpv /dev/sdb1 and left the computer for dinner; when I came back it had rebooted. So it looks like gnome is not the issue.

I remembered there were some updates I installed yesterday, I think—is there a log somewhere? Libavahi, firefox, xulrunner, vinagre, perl, passwd, openoffice.org, login, flashplugin, ubuntu docs, among others if I recall correctly....

Booting in to the live CD 8.04.1 gave me no usable gnome login—the display was not good, perhaps because it does not have nVidia. But I could do ctrl-alt-f1 and get a command prompt. From here I ran e2fsck -pfv on both HDDs and found no issues. It also did not auto-reboot from the live CD.

I have tried everything that has been suggested short of formatting the disk and reinstalling everything

I wonder if the last.log has grown too big and if that might be an issue? It is only 286K, and has less than three screens of info in it.

We have now passed the 36 and 37 minutes past the hour mark without a reboot. So what did it? fsck? starting in live CD and running there for awhile? Or will it reboot again one hour after I restarted from the HDD? Stay tuned....

---

### Post by dgermann on 2008-12-26
Hi all--

Well, it has gone 20 hours now without a reboot, so I am hoping that the fsck was what did the trick. 

What I think I will do next is use tune2fs to change the interval of checks to something like 20 or even 15, so that it gets checked more often. Or maybe every week. I think this system does not get rebooted very often and that might be contributing to this problem.

However, if the number of times fsck is run is the issue, or the time between them, then does this mean there is a bug in the OS, or in my system, and what is the fix for that?

---

### Post by RJARRRPCGP on 2008-12-26
It looks like a virus or malware.

If it was heat, it would be more random and the time it stays on would get shorter and shorter and shorter and shorter.

---

### Post by dgermann on 2008-12-28
RJARRRPCGP--

(What an interesting user name!)

Yes, I agree it does not look like heat. I also lean away from the virus idea because I daily run esets nod32 on this machine, and have since before the problem.

The first time the problem showed up, I think, was several months after I installed 7.10 after having added a new HDD, and not being able to get the old one to boot (6.06). So I converted the old HDD to data use only, and the new one became the boot disk. But as I say, this started probably at least 3 months after the install, so it seems likely it is unrelated to that.

Thanks for helping me, RJARRRPCGP!

---

### Post by shookmon on 2008-12-31
Not that this probably has ANYTHING to do with your problem, but this reminds me of an old story where the servers would reboot every morning at 1am.
 
This went for months and months with the entire dept. pulling their hair out trying to figure it out. No errors in the log, no error on the drives. Rebuilding the servers didn't work, new hardware, nothing.
 
Until one morning one of the techs decides he's going to camp out in the server room to prove there's no ghosts turning off the servers.
 
When 1:00 am rolls around he goes outside for a smoke and notices a cop car pulled up right outside the data center wall with the cop eating his lunch.
 
Just as he goes over to the car, he sees the cop pull out his radio and he hears the cop call in to dispatch. Sure enough, the tech's pager starts going berserk with new alerts of rebooting servers.
 
It seems that the cop had just started this beat a few months prior, and he thought that this would be a good place to take his lunch break. Of course, he had to call into dispatch to tell them he's on break. His radio was so powerful it was causing the servers to lock up and then reboot.
 
:D

---

### Post by dgermann on 2009-01-02
shookmon--

Thanks! That is a good story--and a reminder to look in places we hadn't thought to look.

All--

Got into the office today, and found that the machine was rebooting again--first of the month like it had been doing. Here is last:```

reboot   system boot  2.6.24-22-generi Fri Jan  2 09:49 - 09:54  (00:04)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 08:46 - 09:54  (01:08)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 07:45 - 09:54  (02:08)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 06:45 - 09:54  (03:09)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 05:45 - 09:54  (04:09)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 04:45 - 09:54  (05:09)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 03:44 - 09:54  (06:09)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 02:44 - 09:54  (07:10)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 01:44 - 09:54  (08:10)    
reboot   system boot  2.6.24-22-generi Fri Jan  2 00:43 - 09:54  (09:10)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 23:43 - 09:54  (10:11)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 22:43 - 09:54  (11:11)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 21:43 - 09:54  (12:11)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 20:42 - 09:54  (13:12)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 19:42 - 09:54  (14:12)    
reboot   system boot  2.6.24-22-generi Thu Jan  1 18:42 - 09:54  (15:12)    
doug     pts/0        :0.0             Thu Jan  1 14:44 - 14:45  (00:00)
```

So I immediately ran this and rebooted:
```
doug@doug2:~$ sudo tune2fs -c 1 /dev/sda1
```

After it rebooted (running fsck), I immediately ran this to put it back where it was:
```
doug@doug2:~$ sudo tune2fs -c 17 /dev/sda1
```

It has now gone past the time it had been rebooting, without auto rebooting.

What I can say is that I think I know what medicine to give to stop these hiccups, but I do not know how to cure them, nor do I know what causes them!

---

### Post by Navarre on 2009-01-02
TBH I haven't dissected this entire thread, but daily, monthly and yearly reboots sounds human initiated.  Like someone set up scheduled backup jobs or processing.  My thought is that what ever they scheduled is failing and causing the reboot, after the reboot it recognizes it failed and re-schedules itself an hour later.  I would look into your 'crontab' and 'at' schedules see if you see something there.  Just a thought.

---

### Post by dgermann on 2009-01-02
Navarre--

Thanks for jumping in!

Sorry the thread is so long that this is buried, but cron and at were some of the first things raised and checked--those do not seem to be the culprits! That's what makes these gremlins fun to chase! ;)

---

### Post by y@w on 2009-01-02
> **dgermann said:**
> Navarre--

Thanks for jumping in!

Sorry the thread is so long that this is buried, but cron and at were some of the first things raised and checked--those do not seem to be the culprits! That's what makes these gremlins fun to chase! ;)

Haha that almost sounds like the part in the latest Batman movie where the Joker tells Batman that he won't kill him because he completes him. :)


Is it possible to move the machine to another place in the office? I once worked with a router (a small PC) that kept rebooting somewhat like this only more random. It turned out in the end that it was a bad network patch cable. Not that that's what it is, but it's something to try (shrug).

---

### Post by Navarre on 2009-01-02
> **dgermann said:**
> Navarre--

Thanks for jumping in!



NP, This one is intriguing, what a way to learn ubuntu's behavior.  If you'll tolerate a ubuntu newbie discussing this with you, I'd like to spend some time looking into this.  

<Stating the obvious just so I can see it in type> The tune2fs commands you're using tells the OS to check the filesystems the 1st time its mounted then resetting it to check them the 17th time its mounted.  </goodbye cap'n obvious (for now Heh)>

Have you seen any correlation to the file systems getting mounted and the reboots?

I have seen continuous reboots when bad disks are involved on SunSparc running Solaris.  It actually turned out to be a bad disk controller so I'm not sure if thats relevant.

I'm grabbing smarttools to see what those will tell me about SMART on my disks.

======= software installed ======  sensors, gsmartcontrol (on top of smarttools)

that sensors util is pretty cool, whole bunch of information that is absolutely irrelevant atm though, since you eliminated heat.  
I installed GSmartControl and ran through that gui.  It has another bunch of information, I found I had a couple errors on one of my disks, interesting.

---

### Post by dgermann on 2009-01-04
y@w--

Thanks! I will check that out the next time it starts misbehaving--for now it has quieted down.

Navarre--

> Have you seen any correlation to the file systems getting mounted and the reboots?

Other than the fact that the auto-rebooting stops when I run the fsck, no. I do not even have a theory as to why fsck would stop the reboots. 

Someone saw another thread where someone running redhat had the same problem and solved it with fsck.

Further in answer to your question: usually this box just sits for weeks on end without mounting or umounting anything new--it is a production machine which runs 24/7.

I found smartmontools in synaptic, but not gsmartcontrol--did you download it separately?

I just installed smartmontools and ran smartctl -a on both HDDs and I do not see anything there that looks like an error.

Thanks for helping me noodle on this one, Navarre!

---

### Post by dgermann on 2009-02-15
Hi friends--

Turned on my screens this morning and found that the computer had rebooted about 13 times since 9:49 pm last night.

So I ran the tune2fs commands again, and all is well after about 6 hours.

This might be a clue: last evening I upgraded to the newly offered linux image for Ubuntu 8.04.1. (Not a whole new kernel, just the image package.) There was also a bunch of Firefox related stuff, about 12 upgrades in all, but Firefox was not left on overnight (unless I did so by mistake).

---

### Post by chewbie on 2009-03-03
Hey,

I think I have the same problem as you : 

```

~$ last | grep boot
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 14:56 - 15:37  (00:40)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 13:56 - 15:37  (01:41)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 12:55 - 15:37  (02:41)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 11:55 - 15:37  (03:41)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 11:01 - 15:37  (04:36)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 09:54 - 15:37  (05:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 08:54 - 15:37  (06:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 07:54 - 15:37  (07:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 06:54 - 15:37  (08:43)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 05:53 - 15:37  (09:43)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 04:53 - 15:37  (10:43)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 03:53 - 15:37  (11:44)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 02:52 - 15:37  (12:44)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 01:52 - 15:37  (13:44)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 00:52 - 15:37  (14:45)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 23:51 - 15:37  (15:45)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 22:51 - 15:37  (16:45)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 21:51 - 15:37  (17:46)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 20:50 - 15:37  (18:46)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 19:50 - 15:37  (19:46)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 18:50 - 15:37  (20:47)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 17:49 - 15:37  (21:47)    
reboot   system boot  2.6.24.5-xxxx-st Mon Mar  2 16:49 - 15:37  (22:47)    
...

```

Notice any pattern? ^^

Could you tell me if you have resolved the problem?

By the way I'm wondering... what mean the 15:37 ? There are the only consistency on the logs and I'm really wondering what it cool be...
* ops * stupid me, it's the local time ^^

---

### Post by dgermann on 2009-03-03
chewbie--

Yes I can tell you if it has been resolved: No, it has not been resolved.

The best I have found is a band-aid: see post #37 in this thread.

I surmise that 15:37 is the latest time you rebooted. So in parentheses it shows how long from that time to the reboot listed on that line.

Everybody--

We are collecting a number of people who are having this problem. Is it time we reported it as a bug somewhere?

But where? Is this a kernel issue? An Ubuntu issue (people outside Ubuntu are having it too, so I suspect not).

By the way, I had another episode on 20090222, just seven days after the prior one. Same fix worked.

---

### Post by chewbie on 2009-03-03
It indeed looks like we are not alone : 

[http://ubuntuforums.org/showthread.php?t=1067061](http://ubuntuforums.org/showthread.php?t=1067061)


I am trying your method, (tune2fs rebooting and then setting it up again...) I hope it will works (at least for some time). 

I am seriously thinking about re installing it but that would be bothersome (it s a production machine -_-)

---

### Post by chewbie on 2009-03-03
Looks like the tune2fs trick does not work for me : 

```

~$ last | grep reboot
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 17:33 - 17:39  (00:05)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 16:33 - 17:39  (01:05)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 15:56 - 17:39  (01:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 14:56 - 17:39  (02:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 13:56 - 17:39  (03:42)    
reboot   system boot  2.6.24.5-xxxx-st Tue Mar  3 12:55 - 17:39  (04:43) 

```

16h33 being the reboot I did when I tried the tune2fs trick...

---

### Post by dgermann on 2009-03-04
chewbie--

Could you post the commands you issued and the steps you took?

When I have done it, I rebooted twice, which might be part of it. (Beginning to sound like a Windows thing, huh? Reboot fixes all? ;)  )

I suspect you did it right and it did not work for you, but I am hoping that another try might help.

What version Ubuntu and what kernel have you? he asks, grasping at straws....

---

### Post by Magellan on 2009-03-13
I had this after installing 8.04.  Exact problem: reboot about every hour.
Adding acpi=off to the boot command (in /etc/gurb/menu.lst) fixed the problem for about a year.  Now it's back.

However, I recently did an update to Ubuntu Studio and I think my boot options changes.  I have more entries now.  I added acpi=off to all of them and will see how it goes.

---

### Post by dgermann on 2009-03-14
Magellan--

Please let us know how it goes for you.

How would apci affect this?

Thanks, Magellan!

---

### Post by Magellan on 2009-03-14
> **Magellan said:**
> I had this after installing 8.04.  Exact problem: reboot about every hour.
Adding acpi=off to the boot command (in /etc/gurb/menu.lst) fixed the problem for about a year.  Now it's back.

However, I recently did an update to Ubuntu Studio and I think my boot options changes.  I have more entries now.  I added acpi=off to all of them and will see how it goes.

adding acpi=off to the new entries in me boot list (from a recent upgrade) has again fixed this problem.

Here's what my/boot/grub/menu.lst file looks like:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


---

### Post by dgermann on 2009-03-14
Magellan--

Interesting....

By chance, when you rebooted, was there a fsck that might have affected fixing the problem?

Could you explain your entry for acpi? The man files for acpi and grub do not give ro or quiet as options....

Thanks, Magellan!

---

### Post by Magellan on 2009-03-14
> **dgermann said:**
> Magellan--

Interesting....

By chance, when you rebooted, was there a fsck that might have affected fixing the problem?

Could you explain your entry for acpi? The man files for acpi and grub do not give ro or quiet as options....

Thanks, Magellan!

Those are actually kernel commands and not grub options.  You can find a list if you search for kernel commands.  In any case, they were all ready there.  I just added the acpi option.

ro tells the kernal to mount the root device as read only on boot.  I don't know much about this, but I suspect it is to protect the files from a bad boot.  I think it gets over-ridden when a user logs in.

quiet suppresses most messages, I think.

---

### Post by dgermann on 2009-03-15
Magellan--

Thanks!

I suspected that's what they meant, too.

What put you on to acpi as a possible solution?

---

### Post by dgermann on 2009-03-30
Hi friends--

Just to report, with symptoms:

20090330: rebooted 14 times since 21:29 yesterday; I had rebooted the system at 09:29 yesterday morning—interesting that it used the same minute to start rebooting. 

Had updated firefox yesterday I think, or the day before, and some others a day or two earlier, primarily OOo from the debian repositories, not from ubuntu repositories.

Anybody see an similar symptoms in your case?

I did the tune2fs trick; will report if that does not work.

:- Doug.

---

### Post by NetDesignate on 2009-04-08
I have a similar issue - I think - and need some help to debug/resolve the situation.  Doug, well done on your persistence - I cannot believe that this hasn't resolved itself sooner.  Anyway, here is a "last reboot" listing - NONE of these reboots were requested.

```
donmc@MSJ:~$ last reboot
reboot   system boot  2.6.24-23-generi Wed Apr  8 08:08 - 09:11  (01:02)
reboot   system boot  2.6.24-23-generi Wed Apr  8 08:06 - 09:11  (01:05)
reboot   system boot  2.6.24-23-generi Wed Apr  8 08:04 - 09:11  (01:06)
reboot   system boot  2.6.24-23-generi Wed Apr  8 08:02 - 09:11  (01:08)
reboot   system boot  2.6.24-23-generi Wed Apr  8 07:57 - 09:11  (01:13)
reboot   system boot  2.6.24-23-generi Wed Apr  8 07:56 - 09:11  (01:15)
reboot   system boot  2.6.24-23-generi Wed Apr  8 07:54 - 09:11  (01:16)
reboot   system boot  2.6.24-23-generi Tue Apr  7 20:47 - 09:11  (12:23)
reboot   system boot  2.6.24-23-generi Tue Apr  7 20:43 - 09:11  (12:27)
reboot   system boot  2.6.24-23-generi Tue Apr  7 20:41 - 09:11  (12:29)
reboot   system boot  2.6.24-23-generi Tue Apr  7 20:40 - 09:11  (12:31)
reboot   system boot  2.6.24-23-generi Tue Apr  7 16:16 - 09:11  (16:54)
reboot   system boot  2.6.24-23-generi Tue Apr  7 15:22 - 09:11  (17:48)
reboot   system boot  2.6.24-23-generi Tue Apr  7 15:18 - 09:11  (17:52)
reboot   system boot  2.6.24-23-generi Mon Apr  6 20:51 - 09:11 (1+12:19)
reboot   system boot  2.6.24-23-generi Mon Apr  6 20:49 - 09:11 (1+12:21)
reboot   system boot  2.6.24-23-generi Mon Apr  6 20:48 - 09:11 (1+12:23)
reboot   system boot  2.6.24-23-generi Mon Apr  6 20:45 - 09:11 (1+12:26)
reboot   system boot  2.6.24-23-generi Mon Apr  6 20:43 - 09:11 (1+12:27)
reboot   system boot  2.6.24-23-generi Mon Apr  6 08:08 - 09:11 (2+01:02)
reboot   system boot  2.6.24-23-generi Mon Apr  6 08:07 - 09:11 (2+01:04)
reboot   system boot  2.6.24-23-generi Sat Apr  4 20:26 - 09:11 (3+12:45)
reboot   system boot  2.6.24-23-generi Sat Apr  4 20:24 - 09:11 (3+12:47)
reboot   system boot  2.6.24-23-generi Fri Apr  3 20:15 - 09:11 (4+12:55)
reboot   system boot  2.6.24-23-generi Thu Apr  2 20:05 - 09:11 (5+13:05)
wtmp begins Thu Apr  2 14:26:15 2009
donmc@MSJ:~$
```

I have scanned the logs for clues, but this is the only serious error I can find - see below:

```
donmc@MSJ:~$ sudo grep segfault /var/log/* -r
/var/log/auth.log.0:Apr  7 15:41:50 MSJ sudo:    donmc : TTY=pts/0 ; PWD=/home/donmc ; USER=root ; COMMAND=/bin/grep segfault /var/log/syslog
/var/log/kern.log.0:Apr  7 13:32:18 MSJ kernel: [59970.920137] console-kit-dae[4923]: segfault at 00000000 eip b7ecf597 esp bfe3a604 error 4
/var/log/messages.0:Apr  7 13:32:18 MSJ kernel: [59970.920137] console-kit-dae[4923]: segfault at 00000000 eip b7ecf597 esp bfe3a604 error 4
/var/log/syslog:Apr  7 13:32:18 MSJ kernel: [59970.920137] console-kit-dae[4923]: segfault at 00000000 eip b7ecf597 esp bfe3a604 error 4
```

I am at a loss as to how to debug this further.
This issue has been going on for weeks (maybe longer) with random timings - sometimes it can go for 3-4 days without a reboot, then as you see above, there can be frequent restarts.  It is NOT hourly like yours Doug, just every now and then.

The machine is an HP DL380 V3 with 1 GB RAM - Intel(R) Xeon(TM) CPU 2.80GHz
OS is Ubuntu 8.04 (hardy) but I run updates regularly, so it is probably whatever is the current version from ubuntu.

Kernel: 2.6.24-23-generic (#1 SMP Mon Jan 26 00:13:11 UTC 2009)

Can someone suggest some sleuthing activities to get this sorted out ?
I'll try anything you have to suggest...

Thanks in advance for ANY assistance.
Don

---

### Post by dgermann on 2009-04-08
NetDesignate--

It was rebooting every 2 minutes? Wow! Certainly can't get any work done that way.

Did you try the tune2fs trick with any success?

Your segfaults do not track the times of the reboots so those don't look like promising clues, although I have no idea what a segfault is....

How does the rebooting track with the times you run updates on your machine? I think that has some correlation for me....

PS: Does anybody think this rises to the level of a bug that should be reported somewhere? Where?

---

### Post by NetDesignate on 2009-04-11
Well I had an interesting error when I ran update this morning: ```
"[COLOR="DarkRed"]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/COLOR]"
```
So I did what it said to do, and it did it's thing, and I am HOPING that the system may return to some stability. (I did the updates after the reboot at 8:04am) so let's see how it goes.  I will update you in a few days.  I do recommend that you run this command at a shell prompt though: 
```
'dpkg --configure -a'
```
Without the single quotes though...

Here is the current list of reboots (Scarey!):
```
donmc@MSJ:~$ last reboot
reboot   system boot  2.6.24-23-generi Sat Apr 11 08:04 - 14:15  (06:10)
reboot   system boot  2.6.24-23-generi Sat Apr 11 07:58 - 08:02  (00:04)
reboot   system boot  2.6.24-23-generi Fri Apr 10 16:43 - 07:56  (15:13)
reboot   system boot  2.6.24-23-generi Fri Apr 10 16:40 - 07:56  (15:16)
reboot   system boot  2.6.24-23-generi Fri Apr 10 08:52 - 07:56  (23:04)
reboot   system boot  2.6.24-23-generi Fri Apr 10 08:12 - 07:56  (23:44)
reboot   system boot  2.6.24-23-generi Fri Apr 10 08:10 - 07:56  (23:45)
reboot   system boot  2.6.24-23-generi Fri Apr 10 03:51 - 07:56 (1+04:05)
reboot   system boot  2.6.24-23-generi Fri Apr 10 01:48 - 07:56 (1+06:08)
reboot   system boot  2.6.24-23-generi Fri Apr 10 01:30 - 07:56 (1+06:26)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:51 - 07:56 (1+07:05)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:34 - 07:56 (1+07:22)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:20 - 07:56 (1+07:36)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:14 - 07:56 (1+07:42)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:13 - 07:56 (1+07:43)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:10 - 07:56 (1+07:46)
reboot   system boot  2.6.24-23-generi Fri Apr 10 00:08 - 07:56 (1+07:48)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:56 - 07:56 (1+08:00)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:41 - 07:56 (1+08:15)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:39 - 07:56 (1+08:17)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:31 - 07:56 (1+08:25)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:17 - 07:56 (1+08:39)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:08 - 07:56 (1+08:47)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:05 - 07:56 (1+08:51)
reboot   system boot  2.6.24-23-generi Thu Apr  9 23:02 - 07:56 (1+08:54)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:58 - 07:56 (1+08:58)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:56 - 07:56 (1+09:00)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:52 - 07:56 (1+09:04)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:48 - 07:56 (1+09:08)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:45 - 07:56 (1+09:11)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:43 - 07:56 (1+09:13)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:36 - 07:56 (1+09:20)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:34 - 07:56 (1+09:22)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:32 - 07:56 (1+09:24)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:28 - 07:56 (1+09:28)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:15 - 07:56 (1+09:41)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:12 - 07:56 (1+09:44)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:09 - 07:56 (1+09:47)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:08 - 07:56 (1+09:48)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:06 - 07:56 (1+09:50)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:04 - 07:56 (1+09:52)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:02 - 07:56 (1+09:54)
reboot   system boot  2.6.24-23-generi Thu Apr  9 22:01 - 07:56 (1+09:55)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:58 - 07:56 (1+09:58)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:56 - 07:56 (1+10:00)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:54 - 07:56 (1+10:02)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:52 - 07:56 (1+10:04)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:48 - 07:56 (1+10:08)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:46 - 07:56 (1+10:10)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:42 - 07:56 (1+10:14)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:36 - 07:56 (1+10:19)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:32 - 07:56 (1+10:24)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:30 - 07:56 (1+10:26)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:28 - 07:56 (1+10:28)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:25 - 07:56 (1+10:31)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:23 - 07:56 (1+10:32)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:22 - 07:56 (1+10:34)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:20 - 07:56 (1+10:36)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:18 - 07:56 (1+10:38)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:15 - 07:56 (1+10:41)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:13 - 07:56 (1+10:43)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:11 - 07:56 (1+10:44)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:08 - 07:56 (1+10:48)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:07 - 07:56 (1+10:49)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:04 - 07:56 (1+10:52)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:02 - 07:56 (1+10:54)
reboot   system boot  2.6.24-23-generi Thu Apr  9 21:00 - 07:56 (1+10:56)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:58 - 07:56 (1+10:57)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:57 - 07:56 (1+10:59)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:55 - 07:56 (1+11:01)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:53 - 07:56 (1+11:02)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:52 - 07:56 (1+11:04)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:50 - 07:56 (1+11:06)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:48 - 07:56 (1+11:08)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:43 - 07:56 (1+11:12)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:39 - 07:56 (1+11:17)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:38 - 07:56 (1+11:18)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:36 - 07:56 (1+11:20)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:34 - 07:56 (1+11:22)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:33 - 07:56 (1+11:23)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:31 - 07:56 (1+11:25)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:29 - 07:56 (1+11:27)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:27 - 07:56 (1+11:28)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:26 - 07:56 (1+11:30)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:24 - 07:56 (1+11:32)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:22 - 07:56 (1+11:34)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:19 - 07:56 (1+11:37)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:18 - 07:56 (1+11:38)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:16 - 07:56 (1+11:40)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:14 - 07:56 (1+11:42)
reboot   system boot  2.6.24-23-generi Thu Apr  9 20:13 - 07:56 (1+11:43)
reboot   system boot  2.6.24-23-generi Thu Apr  9 07:58 - 07:56 (1+23:58)

```

---

### Post by NetDesignate on 2009-04-12
Update Sunday 12th:
All seems well for now - will keep you posted.
**Don**
```
donmc@MSJ:~$ date
Sun Apr 12 10:51:39 EDT 2009
donmc@MSJ:~$ last reboot
reboot   system boot  2.6.24-23-generi Sat Apr 11 08:04 - 10:51 (1+02:47)
```

---

### Post by dgermann on 2009-04-12
Don--

Interesting! Thanks.

So do you see a clue here? I wonder if doing the dpkg --configure -a would solve the issue as well as sudo tune2fs -c 1 /dev/sda1?

But I wonder if it would cause problems if dpkg had not stopped midway as it did for you?

---

### Post by tom66 on 2009-04-12
As far as I know, "dpkg --configure -a" simply tells dpkg (the package manager) to finish any installation tasks. For example, you install something and cut power before installation is complete - the command will rerun the installation procedure (without the downloading part.) It needs to be done because otherwise dpkg is left in an inconsistent state (packages are missing/installed where they shouldn't be, and incompatibilities arise.)

---

### Post by dgermann on 2009-04-13
tom66--

Thanks for jumping in!

If that won't work, and what does works only for some people, got any ideas for clues here?

Thanks!

---

### Post by NetDesignate on 2009-04-14
OK - well I think you are right - it started failing again yesterday.  remember that the last failure was at 8:04am Saturday...

I am thinking it is bad RAM - as the system just drop dead and boots - I cannot find any syslog msgs etc. to give me a clue on it.  I have ordered a whole new machine for spares (yes believe it !) so can replace all of the RAM and see if that is what is going on.

Seems like we need some docs on how to debug such sneaky issues as this - (hardware related issues methinks) 

See the reboots list below.  It continues...

Any suggestions or questions ?  I will do anything within reason.


```
donmc@MSJ:~$ last reboot
reboot   system boot  2.6.24-23-generi Tue Apr 14 09:53 - 09:54  (00:01)
reboot   system boot  2.6.24-23-generi Tue Apr 14 09:51 - 09:54  (00:03)
reboot   system boot  2.6.24-23-generi Tue Apr 14 09:46 - 09:54  (00:07)
reboot   system boot  2.6.24-23-generi Tue Apr 14 09:43 - 09:54  (00:11)
reboot   system boot  2.6.24-23-generi Tue Apr 14 08:38 - 09:54  (01:16)
reboot   system boot  2.6.24-23-generi Tue Apr 14 08:05 - 09:54  (01:49)
reboot   system boot  2.6.24-23-generi Mon Apr 13 22:59 - 09:54  (10:55)
reboot   system boot  2.6.24-23-generi Mon Apr 13 22:56 - 09:54  (10:58)
reboot   system boot  2.6.24-23-generi Sat Apr 11 08:04 - 09:54 (3+01:50)

```

---

### Post by dgermann on 2009-04-14
NetDesignate--

Hmmm.... I think my problems might have started about the time I got new ram.

1. Is there a way to test ram for such problems as this? Perhaps a test you run and capture results for when the problem is recurring?

2. What if you replace just half the ram and see what happens, then the other half? Would that tell us anything?

---

### Post by NetDesignate on 2009-04-14
To test the RAM I think it needs to be offline - you could use the hardware diagnostics (from the manufacturer of your hardware) or boot to a CDROM like:
   [COLOR="Red"][http://www.**ultimatebootcd**.com/]("http://www.ultimatebootcd.com/")[/COLOR]

- that has memtest amongst other test tools (filesystem tests etc.) on it.

That is what I am going to do when I get in there next...

Don

---

### Post by dgermann on 2009-04-15
NetDesignate--

Don, you have triggered it for me--there is a memtest at bootup in Ubuntu: when you boot up hit esc (I think) and you get the various kernels and safe modes you can enter. At the end of the list is something like memtest+.

I ran it a month ago on one machine--let it run over about 36 hours--and it found no problems. But that is not the machine that is rebooting.

---

### Post by The_Doc_tor on 2009-04-15
I have a similar issue with my PC but only on shutdown.
My issue seems to be with the Bios specifically with the keyboard boot function.
If my Bios is set to allow the keyboard to Boot the system when any key is touched, Ubuntu wont shut down but only Reboot.
I had a heck of a time figuring out thats what it was but it seems fine now.
Could it be something in your bios telling your PC to Reboot when a certain key sequence is activated?

---

### Post by dgermann on 2009-04-15
The_Doc_tor--

Thank you. That is I think the first time that clue has been suggested over the last too many months. Thanks!

Most of my reboots have been in the wee small hours, when there is no one here, except maybe the beasties.... Then again, I have found no droppings around, so they may be fairies.... ;)

Anybody else see this as a clue for your system?

As I think about it, you mean any key press caused a reboot? Or only after you had asked for a shutdown?

Thanks, The_Doc_tor!

---

### Post by NetDesignate on 2009-04-20
Hi Doug,

So I have a faint glimmer of hope here for my situation.
You'll remember that I had random reboots going on - not HOURLY like yours...

I was chatting with a friend yesterday (an IT guy) and he told me a story about recent troubles with UPS's that have oldish batteries causing reboots off and on...

So yesterday I removed the battery backup from the equation just as an experiment, and touch wood, it is now stable. (Last reboot was the one I did manually on Sunday afternoon).

Fingers crossed.

Not sure if this is likely to fix your issue, but I would definitely take a good look at your UPS software & hardware diagnostics and make sure that you don't have a rogue UPS doing its thing to your server like mine is/was !

Regards, Don

```
http://help.ubuntu.com/
You have new mail.
Last login: Mon Apr 20 08:27:46 2009 from 192.168.0.200
donmc@MSJ:~$ last reboot|less
**[COLOR="Red"]reboot   system boot  2.6.24-23-generi Sun Apr 19 14:29 - 23:37 (1+09:07)[/COLOR]**
reboot   system boot  2.6.24-23-generi Sun Apr 19 13:58 - 14:22  (00:23)
reboot   system boot  2.6.24-23-generi Sun Apr 19 13:44 - 14:22  (00:38)
reboot   system boot  2.6.24-23-generi Sat Apr 18 08:09 - 14:22 (1+06:13)
reboot   system boot  2.6.24-23-generi Sat Apr 18 08:07 - 14:22 (1+06:14)
reboot   system boot  2.6.24-23-generi Sat Apr 18 08:05 - 14:22 (1+06:16)
reboot   system boot  2.6.24-23-generi Fri Apr 17 20:58 - 14:22 (1+17:23)
reboot   system boot  2.6.24-23-generi Fri Apr 17 08:31 - 14:22 (2+05:50)

```

---

### Post by dgermann on 2009-04-21
Don--

That is good news for you! I am glad. Keep us informed if the problem resurfaces.

I don't think it is my problem, since the UPS does not report problems at the same time, and if I recall correctly, my rebooting problem predates having any UPS connected to the machine. <sigh>

---

### Post by NetDesignate on 2009-05-12
Doug,

[B]I have some more news for you:
[/B]
1.  What I thought had fixed it (removal of the UPS) did NOT fix it.  It ran clean for about a week, which got me all excited, but then started to reboot randomly again.  In the end, I bought another WHOLE DL380 G3 for spares, and replaced the entire server.  Overkill, I know, but I was feeling guilty about the number of interruptions my customers had been putting up with :(

2.  I have since had access to the machine that was playing up, and I think you might want to check on the ASR (Automatic System Reboot) setting in your ROM Based System Config - you'll get there by hitting F9 during reboot (at the right time) - the BIOS setup.  Scroll down to the ASR settings, and DISABLE ASR.

Fire it up and see how it goes now.

Good luck.
Don

[B]My users are stable since I replaced the hardware:
[/B]
> Last login: Tue May  5 18:30:24 2009 from 192.168.0.88
donmc@MSJ:~$ last reboot
reboot   system boot  2.6.24-24-generi Tue May  5 18:19 - 10:11 (6+15:52)
reboot   system boot  2.6.24-23-generi Tue May  5 17:45 - 10:11 (6+16:25)
reboot   system boot  2.6.24-23-generi Tue May  5 14:24 - 10:11 (6+19:47)
reboot   system boot  2.6.24-23-generi Tue May  5 12:18 - 10:11 (6+21:53)
reboot   system boot  2.6.24-23-generi Mon May  4 09:19 - 10:11 (8+00:52)
reboot   system boot  2.6.24-23-generi Mon May  4 09:16 - 10:11 (8+00:54)
reboot   system boot  2.6.24-23-generi Mon May  4 07:54 - 10:11 (8+02:17)

wtmp begins Mon May  4 07:54:33 2009
donmc@MSJ:~$


---

### Post by dgermann on 2009-05-13
Don--

Thanks for your suggestion. Sounded like a good suspect, but for me no go.

F2 gets me to bios, F9 does nothing. Unless I am looking/hitting F9 in the wrhong place.

Anyway, BIOS' power page gives these entries, and these are my settings:

After power failure --->           Stay off
Wake on LAN from S5 --->           Stay off
ACPI suspend state  --->           S3 State
EIST                --->           Enable
Wake system from S5 --->           Disable

There is nothing else on this page. There is no ASR anywhere in the BIOS.

Did this fix it for you, Don?

Just this evening it started rebooting at 6:13 pm. I am running the tune2fs fix now....

Thanks, Don!

---

### Post by dgermann on 2009-05-16
Reporting to all our friends--

The tune2fs trick worked the other day.

And I am pretty sure that when I heard the fan start up, I managed to save what I was working on at that moment (ctrl-S in OOo).

---

### Post by dgermann on 2009-06-25
Hi--

Having the rebooting this morning again.

Two thoughts:

1. I saw something flash on the screen just before the login screen after one auto reboot, something about ntp I think. I do not know what ntp is. Could it affect this?

2. This is the only computer among about 8 that has this problem. This is the only computer running nVidia. Could there be a connection there?

Off to run tune2fs....

---

### Post by philcamlin on 2009-06-25
are you hacked? :confused:

---

### Post by dgermann on 2009-06-25
philcamlin--

Thanks for coming up with something new!

I don't think so. The computer is desktop kept in a locked environment. Firestarter shows no events outside my network, and the only connections are for Firefox and Evolution Pop3.

Where else would I look?

And the fact that others are having similar difficulties suggests it is not a hack, or at least not a common hack.

Thanks philcamlin!

---

### Post by dgermann on 2009-08-21
Hi--

Again this morning. Started later in the day, around 7:58 am.

I tried something different this time: after running through the first iteration of tune2fs, I reset the maximal mount count to 3 (had had it at 9). My theory is that 2 of 3 times I will be able to reboot without waiting for a fsck, and when this rebooting happens (which is more common than me rebooting on purpose), I will in most cases not have to do anything because the computer will take care of it itself overnight on the third reboot.

---

### Post by NetDesignate on 2009-08-21
Hi Doug,
I just saw your post and remembered that I never did let you know that my issue turned out to be _faulty RAM_.

My system is now completely stable after removing two RAM sticks from my 4MB of RAM.  [at some stage I will determine WHICH stick it is that is faulty, but for now, I am just happy that it is fixed...]

So I am not sure if you have any spare RAM that you could use to test, but it is worth a shot.  Before that, my system would reboot with NO warning, NO messages to logs, just SNAP - and it is in a reboot loop.

Anyway,
Since you have been so long-suffering with this issue, I thought I would throw this data out there for you to consider.

Best of luck.
Don

---

### Post by dgermann on 2009-08-22
Don--

Good thought. Could explain why some are having the problem and others not.

Any thought as to why tune2fs would fix it for awhile each time?

(I'm a little leery of changing memory sticks--last time I did, I fried the mobo!)

---

### Post by NetDesignate on 2009-08-22
Well give it a shot - just move slowly and carefully.  

You'll be fine with swapping the RAM out.  Given how long this has been an issue for you, it is definitely worth a try...

As for your question, I have seen MANY things LOOK like a fix for a while, only to have the issue return each time.  So no - I don't have any easy answer to your question...

Good luck.
Don

---

### Post by dgermann on 2009-08-24
Don--

Thanks for giving me courage.

I may try it soon, once I run my courage up a notch or two more! :)

---

### Post by yusenda1 on 2009-10-30
Hi dgerrman !

How's the result of replacing the RAM stick?

I'm eager to heard the result as I'm having exactly the same problem with you (although mine is a Samba file server, running Ubuntu Hardy).

I'm currently running MemTest from the install CD, let's see what the verdict.

---

### Post by dgermann on 2009-10-30
yusenda1--

Thanks for jumping in here.

I have not (yet) replaced the memory sticks. I have had the rebooting about twice since August, so it continues about every month or so.

But the fact that you are running a server and having the problem is a clue that it is perhaps related to the memory sticks: this machine is kept on pretty much 24/7/365, as I suspect your server would be. Is it possible that that kind of use puts more stress on the memory sticks?

:- Doug.

---

### Post by Bjalf on 2009-10-30
> **dgermann said:**
> 1. I saw something flash on the screen just before the login screen after one auto reboot, something about ntp I think. I do not know what ntp is. Could it affect this?
ntp = Network Time Protocol. [http://en.wikipedia.org/wiki/Network_Time_Protocol](http://en.wikipedia.org/wiki/Network_Time_Protocol)
What if the ntp daemon runs every 60 minutes after boot, and crashes the computer for whatever reason? RAM, messed-up binary program file, or something?

Try disabling the ntp daemon and see what happens.

---

### Post by luigi_mb on 2009-10-30
> **Bjalf said:**
> ntp = Network Time Protocol. [http://en.wikipedia.org/wiki/Network_Time_Protocol](http://en.wikipedia.org/wiki/Network_Time_Protocol)
What if the ntp daemon runs every 60 minutes after boot, and crashes the computer for whatever reason? RAM, messed-up binary program file, or something?

Try disabling the ntp daemon and see what happens.

A few years ago a friend of mine had a somewhat similar experience. To make it short, it turned out that there was a spurious, stray signal in the power line leaking from a system that was synchronizing some electric clocks. Placing a suitable filter between the wall outlet and the computer solved the problem. I am sorry I can't provide more useful details.

---

### Post by Marrkk on 2009-10-31
i'd say Thermal problem too...  if u suspect a software prob, suggest u run another live CD (not neccessarily *buntu) for a hour or two,
different distros use / abuse power management / cpu scaling etc in different ways
wonder what cpu u usin ?

---

### Post by yusenda1 on 2009-11-02
Stress on the sticks usually come from unfiltered electical spike (caused by low quality Power Supply Unit inside the casing).
Problem is, that does not apply in my case, as I've replaced the PSU with a high quality one, and there's also a UPS supplying the server, and there's a stabilizer for the whole building.

So far, I've memtest the server for 8 hours , do an fsck for all drive, do SMART test.

And suddenly, the reboots stops.

Uptime output:

campuhan@campuhanserver:~$ uptime
 14:12:22 up 2 days, 21:16,  2 users,  load average: 0.00, 0.00, 0.00

So far so good, let's see what will happen...

*of course, I need to take out the server to do the memtest during the weekend*

---

### Post by dgermann on 2009-11-02
Bjalf--

Thanks. 

Do you think that once it is in the loop of shutting down, disabling the ntp daemon will give the results? Because otherwise, it might be difficult to tell if that worked, since it only happens once in a month or two.

luigi_mb--

Thank you for helping.

I have a ups on the line--does that provide some filtering? It's an APC about a year old.

Marrkk--

Thank you.

What CPU? How can I tell to report it to you?

yusenda1--

I wonder if the fsck "fixed" it for you? I think that's essentially what the tune2fs does....

How is it going for you now? Any more involuntary reboots?

:- Doug.

---

### Post by yusenda1 on 2009-11-02
It's been 3 days, 18 hours, 25 minutes and no reboot!

I forget to mention, beside all those steps, I also separated the power line.
The output from the UPS now connected to the server ONLY, before it was connected to the server and a monitor that was connected to the server.
The reason I did this was because I suspected the UPS can't handle the amount of electricity needed by the monitor, so it colapsed from time to time (don't know why it does not happened in the first 3 months, but it's a cheap UPS...)

So far so good, let's hope it goes on to be good :D

---

### Post by dgermann on 2009-11-02
yusenda1--

Great! Let's hope you've got it solved!

---

### Post by Bjalf on 2009-11-03
> **dgermann said:**
> Bjalf--

Thanks. 

Do you think that once it is in the loop of shutting down, disabling the ntp daemon will give the results? Because otherwise, it might be difficult to tell if that worked, since it only happens once in a month or two.
I have no idea, sorry. But the extreme regularity of the problem sounds to me like it's software related. That's why I would suspect cron or some daemon. Or maybe even the BIOS. Could you flash to a newer version? Or at least check if any newer versions fixed any bugs that might be related to this. Do you know what motherboard and BIOS version you have?

On the other hand, inexplicable problems are often caused by bad RAM. And as inexplicable problems go, this one is going to be a classic!  ;)    I fully expect Hollywood to make "Computer Gremlins" after hearing about this. Wait, you fed it after midnight, didn't you?

Hmmm, when that sucker rebooted, did you notice if the BIOS time and date were correct? You would have to wait for a reboot and immediately enter the BIOS to check that. A dead backup battery could give some really weird symptoms.

---

### Post by dgermann on 2009-11-04
Bjalf--

Thanks.

I think your idea about flashing to a newer bios might be useful--if I could figure out how to do that. Have never done such a thing. The mobo is an Intel DG33FB, installed new December 2, 2007.

Well, I only fed the ram after midnight twice, no thrice, so that should be no witches brew, yes?

No, I have not checked the bios clock--that's a good idea.

I am curious about the ram--these problems came up shortly after the new mobo was installed--with more ram, of course. I am reluctant to change the ram myself, since that's why I got a new mobo--putting the new ram into the old mobo and powering up, I got a fire on the mobo!

---

### Post by Bjalf on 2009-11-05
Intel® Desktop Board DG33FB
[http://www.intel.com/Products/Desktop/Motherboards/DG33FB/DG33FB-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG33FB/DG33FB-overview.htm)

The latest BIOS for DG33FB (that I could find in a hurry) is 0572 from July 15, 2009.
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=2781&DwnldID=17930&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=2781&DwnldID=17930&lang=eng)

From the release notes:
"Fixed potential failures on S3 resume due to bad algorithm for clock chip programming."
"Fixed the 2 minutes boot delay during warm reboot problem plus the invalid DFROM TCM segment and TEM address issues."
"Fixed S3 Resume time increase when 4GB installed."
"iQST: Fan detection improvement."
From the sound of it, any and all of these might be related to your problems. Not that I really understand what it all means  :lol:

**Lots** of other fixes:
[http://downloadmirror.intel.com/17930/eng/DP_0572_ReleaseNotes.pdf](http://downloadmirror.intel.com/17930/eng/DP_0572_ReleaseNotes.pdf)



Flashing a BIOS is not for the faint of heart, a power-out or glitch during the flash could be fatal for the MoBo. That being said, I flash BIOS'es all the time, whether I need to or not. Never gone wrong yet! (I just jinxed myself, didn't I? :-#  )

The best way of doing it is to make a bootable CD / USB stick / floppy and cold boot from it:

> **Recovery BIOS Update [DP0572P.BIO]** - A .BIO file to be used for BIOS  recovery process, regardless of operating system. In the unlikely event that a  BIOS update is interrupted, it is possible the BIOS may be left in an unusable  state. Use the Recovery BIOS update to recovering from this condition. It  requires a blank floppy diskette or CD.

**ISO Image BIOS Update  [DP0572P.ISO]** - Bootable ISO image BIOS update; this is the recommended  method to update the BIOS on systems running Linux*. It requires a blank CD and  a read/writeable CD drive.

**Iflash BIOS Update / Integrator Toolkit  BIOS Files [DPP3510J.86A.0572.BI.ZIP]** - A DOS-based utility to update the  BIOS regardless of operating system. It requires a CD or a USB flash device.  This download also provides the necessary files for Intel® Integrator Toolkit.  Support and FAQs for Intel® Integrator Toolkit are available [here.]("http://support.intel.com/support/motherboards/desktop/sb/CS-015474.htm")
:popcorn:

---

### Post by dgermann on 2009-11-10
Bjalf--

Yes, I found that same page, and I too wonder what that means, whether it applies to the problems I have been having. I might just give that a try.

Thanks for giving me the tip about using a memory stick.

Thanks!

---

### Post by dgermann on 2009-11-10
Bjalf--

I just rebooted and checked my bios clock--it was 19 hours behind. So I reset it.

But now my desktop clock is 19 hours ahead. Guess I need to see how to kick it to check with the server for the correct time! [edit--after a couple minutes it took care of this itself; time is now correct.]

I'll keep an eye on this--it suggests that my backup battery might be shot.

Thanks for this idea.

---

### Post by Bjalf on 2009-11-11
> **dgermann said:**
> Bjalf--

I just rebooted and checked my bios clock--it was 19 hours behind. So I reset it.

But now my desktop clock is 19 hours ahead. Guess I need to see how to kick it to check with the server for the correct time! [edit--after a couple minutes it took care of this itself; time is now correct.]

I'll keep an eye on this--it suggests that my backup battery might be shot.

Thanks for this idea.

Ummm, that sounds more like a time zone thing. What's your offset from GMT? 5 hours?  ;)   Linux wants the hardware clock to be GMT, and the software clock to be local time. Or something like that, IANALG (I Am Not A Linux Guru)  :P

A dead battery typically shows up as the date being 01.01.someyear at every reboot.

---

### Post by dgermann on 2009-11-11
Bjalf--

Yes, we are UTC -5, not 19! ;)

OIC why the battery might give the 01-01-01 kind of result. Thanks.

Gnome Clock is set to retrieve the time from the Internet, so that is usually pretty accurate.

However, if the battery is dying and not dead, it seems it would lose time, yes?

---

### Post by Bjalf on 2009-11-11
> **dgermann said:**
> However, if the battery is dying and not dead, it seems it would lose time, yes?
Nope, the hardware clock is (mostly) correct as long as the power is good, and when the power is bad, it resets completely to 000000, which the BIOS then interprets as 01.01.01 or whenever. Or you're suddenly 1024 days off, or something weird like that. And, as long as the main power is good, the battery could be dead as a Dodo, and nobody would notice. Power is power!

Like most digital devices, it's either completely good or completely bad, there's rarely anything in-between like analog devices. Unless you have a wind-up computer?  :p

I actually had that very problem with the father of a friend. He couldn't do online banking. Every time he logged on to the bank, he got the message that the certificate was invalid. So, when I booted the PC, I went straight for the BIOS (OK, on the 3rd try), and noticed that the date was **way** off. 01.01.something, and the time 00:01:something. WTF?

Of course the certificate was invalid! The certificate was only valid for 1 year, and that timespan was nowhere near the date on the computer!

Totally stupid problem. He couldn't do online banking, because the backup battery was dead. Tiny watch battery buried inside a PC case = online banking. **Nobody** connected the dots. Me neither, at first.

And sometimes +19 = -5. Which (again) reminds me: A contestant for the Olympics were trying to pre-adjust for the future 8 hours jetlag, so he offset his clock by 8 hours. Except he went the wrong way! And the newspapers went nuts (i.e. stupid), and claimed that now he was 16 hours off! Of course he wasn't, he was still 8 hours off, just the other way.

---

### Post by dgermann on 2009-11-11
Bjalf--

Oh! Did I forget to mention that I have one of those new green computers--it is partially wind-up! It is a hybrid--once it gets up to highway speed, it drops into wind-up mode.

Yes, I can see how +19 = -5! Oh, but I was -19, so is that the same as +5? Where's that? Turkey? ;)

---

### Post by Dullstar on 2009-11-11
Try a different release - probably Jaunty would be a good bet (trust me, it should be findable; recently I found an iso for dapper drake).  AND DO NOT UPGRADE!  BACK UP ANY IMPORTANT DATA AND DO A FRESH INSTALL!

---

### Post by dgermann on 2009-11-12
Dullstar--

Interesting thought.

This is a production environment, so I have to go slow about changing releases, and prefer to stay with the LTS versions--and keep all my desktop machines for everybody on the same version.

Actually, the next release I install will probably be a fresh install--there are some other things that are just not acting correctly. For instance, Evo can't seem to figure out to use OOo to open .doc files and keeps trying to use evince! Minor irritations which have not pushed me to the brink yet. I do have a lot of things I did to customize this over the years, many of which I probably can no longer recall.... <grin>

Why Jaunty?

Thanks, Dullstar!

---

### Post by Dullstar on 2009-11-12
The reason for Jaunty is that it is more recent but has had more time to mature.  Karmic isn't yet as stable.

---

### Post by dgermann on 2009-11-18
Dullstar--

Thanks, Dullstar, I will check it out. Hadn't thought about versions maturing, but I guess they do.

Sorry you had to wait so long for a reply--I was away from a computer for an extended period.

Thanks for giving me such good advice.

---

### Post by Dullstar on 2009-11-18
Good luck.

---

### Post by yusenda1 on 2009-12-28
I'm back to report that my server gone berserk again about a week a go.

Tried the fsck way again, no gain. Still 60 minutes loop restart.

Resorted to replaced the whole OS with Centos 5.4, testing it for a whole week, looks good.
But today (actually last night) it started the exact same 60 minutes restart loop.

I guess it really come down to hardware.

I'll try to break up the machine tomorrow to see whether it is the problem of:
1. overheating
2. bad hardware
3. bad bios

wish me luck!

---

### Post by dgermann on 2009-12-28
yusenda1--

Good luck!

Please let us know what you find. It looks like you are on to something that might help us all! :popcorn:

---

### Post by yusenda1 on 2009-12-29
Bad news...

Dec 28 08:54:21 campuhan syslogd 1.4.1: restart.
Dec 28 09:54:40 campuhan syslogd 1.4.1: restart.
Dec 28 10:55:00 campuhan syslogd 1.4.1: restart.
Dec 28 11:55:20 campuhan syslogd 1.4.1: restart.
Dec 28 12:55:38 campuhan syslogd 1.4.1: restart.
Dec 28 13:55:57 campuhan syslogd 1.4.1: restart.
Dec 28 14:56:13 campuhan syslogd 1.4.1: restart.
Dec 28 15:56:36 campuhan syslogd 1.4.1: restart.
Dec 28 16:56:58 campuhan syslogd 1.4.1: restart.
Dec 28 17:13:25 campuhan syslogd 1.4.1: restart.

at 17:13 I restarted the machine in order to set the SELinux condition from disabled to permissive , in order to start the livecd creation script. And strangely, the machine does not reboot automatically anymore!

I'm really starting to believe in server's gremlin....

Now, should I break out the machine or not????

---

### Post by dgermann on 2009-12-29
yusenda1--

Do you think selinux has anything to do with it? Or with solving it?

Are you going to try swapping out ram?

---

### Post by yusenda1 on 2010-01-03
Doug,

No idea on SE Linux. AFAIK, in permissive mode, SELinux only spew warnings whenever something is considered a security risk. No action taken. That's why I'm really confused that it stops boot-looping.

My best bet still on hardware. As I mentioned before, I've run memtest on this server for a full day. So I guess RAM is OK, so next is heat problem and motherboard. I've bought some extra fan, and will install it this weekend.

Philip

---

### Post by dgermann on 2010-01-03
yusenda1--

My hunch is for the ram; on my system at least I have never (in a year of watching) seen the temp go above 40 degrees C, and this all follows some new ram for me.

Anyway, please let us know what you are trying and finding out. I think it will help a lot of people.

Thanks, yusenda1!

---

### Post by Sismon on 2010-01-22
Hi everybody,

I was digging into another older thread so I come here to let everybody know that for me on Ubuntu 8.04 LTS my server just rebooted once this morning whereas it was running for more than a year...

Strange behaviour as nothing has been changed recently but it just seems to be a hardware failure, either a HDD or the SCSI Controller.

syslog :

> Jan 22 08:25:33 srv01 snmpd[9412]: Connection from UDP: [127.0.0.1]:54118
Jan 22 08:59:41 srv01 syslogd 1.5.0#1ubuntu1: restart.
Jan 22 08:59:41 srv01 kernel: Inspecting /boot/System.map-2.6.24-19-srv01kern.log :

> Jan 22 00:20:08 srv01 kernel: [5701920.407878] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5701920.407949] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 00:20:08 srv01 kernel: [5701981.143857] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5701981.143922] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 00:20:08 srv01 kernel: [5702052.567931] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568246] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568269] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568292] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568360] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 08:59:41 srv01 kernel: Inspecting /boot/System.map-2.6.24-19-server


Will check hardware but pretty sure it has to do with it.

Will keep you inform,
Thanks
Sismon

---

### Post by dgermann on 2010-01-23
Sismon--

Please do keep us informed.

I may be misreading the logs you posted, but I do not see how they point to a hardware problem. Could you explain a bit so I might know how to interpret my logs?

Thanks!

---

### Post by tyk on 2010-01-24
Hi all,
this problem has just started off for me. In fact a lengthier post I was writing was stymied by a restart. This is the same system I have been running on Xubuntu 8.04 for a year+ without this issue. I think it was the 19th of Jan when I did a clean install of Ubuntu 8.04.2. I didn't notice the problem till today when it went off right in front of me, and then again. I had woken up in the morning to find a login screen in the previous days but had attributed it to my poor power supply/UPS (skips sometimes). But this has all the markings of the problem described here.

```
reboot   system boot  2.6.24-23-generi Sun Jan 24 17:44 - 18:02  (00:18)    
reboot   system boot  2.6.24-23-generi Sun Jan 24 16:32 - 18:02  (01:30)    
reboot   system boot  2.6.24-23-generi Sun Jan 24 15:32 - 18:02  (02:30)    
reboot   system boot  2.6.24-23-generi Sun Jan 24 14:32 - 18:02  (03:30)    
reboot   system boot  2.6.24-23-generi Sat Jan 23 13:32 - 18:02 (1+04:30)   
reboot   system boot  2.6.24-23-generi Fri Jan 22 17:12 - 18:02 (2+00:50)   
reboot   system boot  2.6.24-23-generi Fri Jan 22 12:10 - 18:02 (2+05:52)   
reboot   system boot  2.6.24-23-generi Thu Jan 21 13:09 - 18:02 (3+04:53)   
reboot   system boot  2.6.24-23-generi Wed Jan 20 12:09 - 18:02 (4+05:53)   
reboot   system boot  2.6.24-23-generi Wed Jan 20 02:08 - 18:02 (4+15:54)   
reboot   system boot  2.6.24-23-generi Tue Jan 19 21:49 - 02:07  (04:17)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 21:26 - 21:48  (00:22)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 20:03 - 21:25  (01:21)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 20:02 - 21:25  (01:23)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 19:54 - 20:00  (00:06)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 14:46 - 19:53  (05:07)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 14:20 - 14:44  (00:24)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 08:31 - 14:44  (06:13)    

wtmp begins Tue Jan 19 08:31:19 2010
```

System Specs:
Intel Q6600
Intel DG33FB
4G RAM
ATI X300

At last reboot, I see in my BIOS:
Version DPP3510J.86A.0216.2007.0502.1916 (Seems old. Should I try flashing it?)
There was also a log entry for 
CMOS Battery Failure: 13-01-2010 (But that would be when the Xubuntu system was installed, and the system date/time are correct UTC)

Cheers and kudos to the work done here, and especially to dgermann :)

---

### Post by dgermann on 2010-01-24
tyk--

Thanks, tyk, for being so kind to give us kudos!

Someone else suggested flashing the bios, too, so if you are OK doing that (not something I have ever done) it might be worth a try. Please let us know if that helps. (Note that my episodes only happen every few months.)

Did you try the fsck trick?

:- Doug.

---

### Post by tyk on 2010-01-24
Since I wrote the post, the computer has not rebooted. Uptime is at 16 hours right now.

Doug, I didn't try the fsck trick. Tell me, do you run fsck on the root partition only? 

Cheers,
Swastik.

---

### Post by Sismon on 2010-01-25
Hi Doug, everybody

Thanks for the follow up on this thread,

Well I don't know I might be misreading as well, or misunderstanding, but as it was RAID related, and I never had such a problem in my logs, I just suggested it was because of either my RAID controller or on of my HDD.

But it now runs from 2 days more hope it will stay, will check today with another sysadmin...

---

### Post by dgermann on 2010-01-25
tyk--

Not sure you can run it only on one partition, but only on a whole HDD. In any case, I just run it on the one that has the boot partition on it.

Sismon--

We'll hope for you! But the proof for me only comes after a few months, so we'll hope a long time, too! ;)

---

### Post by tyk on 2010-01-25
```
swastik@teg:~$ sudo fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
swastik@teg:~$ sudo fsck /dev/sdb7
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb7 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
swastik@teg:~$ 
```

I think one can run it on a disk or a partition. Anyway I'm no expert!

Haven't experienced automatic reboot in some time. Hope it stays that way..

```
swastik@teg:~$ last reboot
reboot   system boot  2.6.24-23-generi Tue Jan 26 00:23 - 01:13  (00:49)    
reboot   system boot  2.6.24-23-generi Mon Jan 25 12:26 - 01:13  (12:47)    
reboot   system boot  2.6.24-23-generi Sun Jan 24 17:44 - 01:13 (1+07:28)   
reboot   system boot  2.6.24-23-generi Sun Jan 24 16:32 - 01:13 (1+08:40)   
reboot   system boot  2.6.24-23-generi Sun Jan 24 15:32 - 01:13 (1+09:40)   
reboot   system boot  2.6.24-23-generi Sun Jan 24 14:32 - 01:13 (1+10:40)   
reboot   system boot  2.6.24-23-generi Sat Jan 23 13:32 - 01:13 (2+11:40)   
reboot   system boot  2.6.24-23-generi Fri Jan 22 17:12 - 01:13 (3+08:00)   
reboot   system boot  2.6.24-23-generi Fri Jan 22 12:10 - 01:13 (3+13:03)   
reboot   system boot  2.6.24-23-generi Thu Jan 21 13:09 - 01:13 (4+12:04)   
reboot   system boot  2.6.24-23-generi Wed Jan 20 12:09 - 01:13 (5+13:04)   
reboot   system boot  2.6.24-23-generi Wed Jan 20 02:08 - 01:13 (5+23:04)   
reboot   system boot  2.6.24-23-generi Tue Jan 19 21:49 - 02:07  (04:17)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 21:26 - 21:48  (00:22)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 20:03 - 21:25  (01:21)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 20:02 - 21:25  (01:23)    
reboot   system boot  2.6.24-26-generi Tue Jan 19 19:54 - 20:00  (00:06)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 14:46 - 19:53  (05:07)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 14:20 - 14:44  (00:24)    
reboot   system boot  2.6.24-23-generi Tue Jan 19 08:31 - 14:44  (06:13)    

wtmp begins Tue Jan 19 08:31:19 2010

```

Except for the times I have switched it off for any reason. Still, I'm not quite convinced this problem is gone. A BIOS upgrade is waiting on a CD but I haven't yet done it. Will do as soon as problem reappears.

Best,
Swastik.

---

### Post by dgermann on 2010-01-25
tyk--

Yup, I got those error messages too, until I did this:

```
sudo tune2fs -c 1 /dev/sda1
sudo reboot
```

Then when you are done, you want to reset it:
```
sudo tune2fs -c 3 /dev/sda1 
```

Of course, change sda1 to what is correct for your machine, and the number of reboots you want before it is checked instead of "3."

---

### Post by tyk on 2010-01-30
Hi Doug,
Thanks for the tips. I've been out a few days and just got back to the machine now. And uptime is 1h1m and so far so good. I will wait for something to go wrong before I try to fix it (as th old adage goes).
If something goes wrong then I will try BIOS update too. Btw, there is 8.04.4 out recently. Anybody given it a shot?
Cheers,
Swastik.

---

### Post by dgermann on 2010-01-30
tyk--

Let us know how it goes....

No, did not know about 8.04.4. Shouldn't it show up in update manager?

Well, maybe I do have it:
```
doug@doug2:~$ cat /etc/issue
Ubuntu 8.04.4 LTS \n \l

doug@doug2:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"
doug@doug2:~$ 

```

So, I gather I have it. What's your question? ;)

---

### Post by tyk on 2010-01-31
Not a question really, Doug. Just that feeling that maybe 'my problem' might be solved in this update. I always get this feeling whenever they announce new updates or releases. This does not even need me to have a real problem but the update/upgrade looks tempting, always :)

On the other hand, my brother, a computer pro says install a new system and never update it. This is what I did with my previous Xubuntu install on this system and well, it was alright.

Anyway, I digress and the question remains, is my computer automagically rebooting every 60 minutes? And the answer is yes it did for some time, and now its not. I read earlier in the thread that this is true for most people. I might expect this to come back sometime. So here's my question. Should I do a BIOS flash and maybe even a fresh install or should I let the problem recur..? After all, a reboot is not critical for me as this is not a web server and saving my work often while working is a habit.

Cheers,
Swastik.

---

### Post by dgermann on 2010-02-01
Swastik--

Well, you could go back to your old xubuntu system and see if that fixes the problem! Actually, the idea of never upgrading sounds dangerous to me--it leaves one open to all sorts of exploits, I imagine.

If you are willing to do a BIOS flash and see what happens, that would help us all. Someone suggested it, but I have never done that, and am a little gun-shy about it. But it sounds like you see it as no big deal.

I am using my machine in a production environment, so even though I save all documents automatically every 2 minutes, the loss of 15 or 20 minutes while I go through rebooting and tune2fs is a big deal.

BTW, I had the problem recur yesterday morning. Tune2fs fixed it, until the next time.

I'd suggest just doing the BIOS flash and see how that goes, then if necessary the fresh install. Doing two things at once would make it hard to figure which one fixed things....

---

### Post by tyk on 2010-02-13
Ah, fortune favors the brave, they said.

To cut a long story short, I have my BIOS **back** and updated to the latest version. Of course the 3 HDs were mapped differently in the new bios and so no grub etc. happened. At this point, I was in multiple minds and near panic. I must admit changing the boot order of the HDs in the bios didn't occur to me till later.

Here's the only (possibly) useful piece of information for this thread I have to share. One of the LiveCDs I tried during the panic phase was an Ubuntu 9.04 with the 'Palimpsest' automatic-disc-checking utility. It promptly told me that my 80G SATA (5 years old) had problems. I'm sorry I didn't exactly note down what problem it had but it sounded serious enough (and I didn't really need it hooked in to the computer) so I backed it up and removed it from my box.

Thereafter, I did some juggling with the HDs and the partitions and bailed from 8.04 completely. I am running Xubuntu 9.10 now and am quite satisfied with it.

To all the thread posters here, thanks and all the very best, especially Doug. May I recommend a full (physical) HD check for those facing the problem?

---

### Post by dgermann on 2010-02-14
tyk--

Well, that's a good idea. I do not see palimpsest in synaptic, so I might have to go looking for it or something similar.

I would prefer to stay with the LTS with 8.04.3, given that I am in a production environment.

Thanks for give us a heads up!

---

### Post by tyk on 2010-02-15
Doug, it shows up as gnome-disk-utility in 9.10.

Cheers, S.

---

### Post by dgermann on 2010-02-16
tyk--

OK, I found that. Thanks.

It is not in the repos for 8.04. I did find [this]("http://packages.debian.org/sid/i386/gnome-disk-utility"), but it is not clear to me that it would run under 8.04, but it does give some similar projects out there.

One is smartmontools (command line: smartctl and smartd), which seems to give a lot of info--and take a lot to learn how to use it. I ran a short test on the drive that I keep having to run the tune2fs command on, and it shows no errors.

Does anybody know if these two apps are similar?

---

### Post by Magellan on 2010-02-16
> **dgermann said:**
> Magellan--

Thanks!

I suspected that's what they meant, too.

What put you on to acpi as a possible solution?

Sorry for not replying sooner...I must have found the answer I was looking for and haven't been back in a while.
 
In any case, it was these forums that put me onto my solution.  If I recall correctly, Someone had me check a log somewhere and that lead to suspecting the power controls.

---

### Post by dgermann on 2010-02-16
Thanks Magellan!

---

### Post by calif99x on 2010-03-19
I would be most interested in hearing about possible solutions to this problem as well.  I have an Intel DG33BU based system with a E6750 CPU that periodically goes into a reboot cycle as well for several days.

The annoying thing is that it will usually do this after an extended period of running without a problem.  

I originally started with Ubuntu 7.10, then upgraded to 8.10, decided that the upgrade may have messed something up.  I next did a clean install of 8.10 on a new drive and have since done a clean install of 9.04 (same HD though).

The system is plugged into a UPS, with a USB connection that Ubuntu seems to recognize as a UPS.  

The only item that I came up with is that if I left Firefox running the problem seemed to manifest itself.  If some other browser (Chrome ) is what is left running the problem did not seem to occur even if the general SW (pidgin, Thunderbird, etc.) were all also running concurrently.  

This is only a guess as I am not sure which file might maintain some type of a log.

Regards

---

### Post by dgermann on 2010-03-20
calif99x--

Well, that is an interesting twist, the idea that Firefox is a culprit. I generally leave Evolution up and running, but cannot think of a time that I have left Firefox up overnight. I will watch and see if that is an issue for me. If so, it might be a good clue.

Otherwise, your symptoms sound like what the rest of us are experiencing. The bandaid for it is the tune2fs trick in post 37 above.

As to logs, I did a locate firefox |grep log and found nothing of any use.

As you sleuth this out, please keep us all informed what clues you find!

Thanks for jumping in!

---

### Post by my_wan on 2010-03-23
This might be a clue. While browsing I noticed my screen darken, which it does when root is accessed. So I started checking log files, and this is what I found:

```
Mar 22 21:17:01 ####### CRON[4694]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 22 22:17:02 ####### CRON[12250]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 22 23:17:01 ####### CRON[12380]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Here's the kicker: I have not created *any* cron jobs to be done. What's there is system defaults. The daemon also checks the folder for cron jobs in case they exist whether they do or not. There is also a default daily, weekly, and _monthly_ file to be checked for cron jobs. If your monthly check is setting off the reboot issue (which has default system job scripts), followed by the hourly reboots from an hourly check that got whacked by the monthly job, it could explain your issue. It wouldn't explain everybodies issue that posted here though.

In my case the daemon darkens my entire display upon the root access by the daemon. Not sure what might be corrupted but would explain both the hourly and monthly routine. My freshly installed system has default monthly scripts which could be corrupted on your machine. Any scripts in:
/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly,
will get executed, and they will get checked for scripts at that time whether they exist or not. If your bios is losing power intermittently and/or losing time it could also cause conflicts in log rotations and such. If a .placeholder file is not in these otherwise empty folders dpkg will remove the directories, which might also cause trouble.

Something worth looking at anyway....

---

### Post by dgermann on 2010-03-23
my_wan--

Interesting.

My screens do not grey out when root is accessed. What OS are you running?

If it is those cron folders that are the culprit, wouldn't we expect the problem to occur every month or every week, instead of very sporadically?

I have a .placeholder in all the cron directories.

I like the idea of checking logrotations to see if they correspond to the times of reboots. Will try to remember to check that out next time I have this happen again.

Thanks! Some good things to check out, my_wan!

---

### Post by my_wan on 2010-03-24
It's a freshly downloaded and installed Ubuntu Karmic Koala 9.10, October 09 release. I've only been playing with it about a week, but it's now my OS.

Is there any scripts in any of those directories at all? Perhaps if there should be a logrotate or other script that doesn't exist the system might be expecting something that doesn't happen. Does your logs get rotated at all? You've mentioned a 'possible' correlation between software updates and reboots. What daemon is triggering your software updates, anacron, manual?

I'm a really raw newby to this system but I'm learning. The hourly and monthly routine you have is no accident and sets the trigger of your problem apart from others. The monthly seems to point away from hardware alone, though could be involved with initiating the trigger. Though I suspect the triggering mechanism can vary, I also suspect that the problem being triggered is consistent with others here. Cron, anacron, dpkg, along with a host of system maintenance jobs are tied to and initiated by daemons, which don't have to have a job configured to check on the configuration of jobs at these times. Thus my guess is that a daemon that runs into certain misconfiguration issues responds badly. Not all such processes require you to be logged into a desktop, though I need to learn more about the boot process.

My list of possibilities is very presumptuous poorly defined, but I can't actually investigate to do better from here. My highly limited knowledge is also a major factor. I do suspect that whatever the trigger, over written files (corrupted) due perhaps to bad time stamps, hardware issues, some combination of the two, etc., I still think there is a software issue that is reacting very badly to an otherwise minor issue. And the Monthly/hourly correlation is the biggest clue available. I'll be doing some research.

---

### Post by dgermann on 2010-03-24
my_wan--

I am anxious to learn what your research shows.

If you have the energy to plow through all the things we tried above in this thread, and perhaps the other threads linked, it might give you some clues.

I do recall having checked all cron files and at files. There is no anacrontab entry other than what comes out of the box.

The only logrotate in any cron directory is in cron.daily.

Not sure what you mean by "What daemon is triggering your software updates, anacron, manual?" Usually what happens here is through update manager, and then I manually choose what to install.

I may be misunderstanding your post as saying that you think my problems occur regularly. They do not. I might go several months and have no problem. (Check the dates of my posts to this thread to see the lack of pattern.) When it does occur, then about every 61 minutes it will reboot. Is that what you mean? Other people here are having very similar problems.

I thought from reading your post that the problem might be that I have upgraded when a new LTS version comes out, and have not done clean installs. But that is not true. The first instance of this problem was after a fresh install: I had a fire on my mobo and replaced the mobo. At that point I could not get the OS to recognize the old drive as having the OS, so I installed another as primary drive and did a fresh install of the OS, with the LTS just before 8.04.1. My first experience of this problem was shortly after that clean install. So I think that eliminates the clean install as a solution here.

Thanks, my_wan!

---

### Post by my_wan on 2010-03-24
What I mean by the trigger issue is that I suspect the problem is separate from the events that trigger the reboot. The underlying problem can be fairly uniform across different users but triggered differently. Thus you not all cases have the 60/61 minute pattern. 

The daemon part is where I suspect that perhaps the problem is with bonobo for instance, which is the parent process for anacron. The process get runs whether they have a job to do or not, and this fact may be important to understanding the problem. Also bonobo doesn't exit as I think it should when you log out of the desktop. Certain prior bugs have been dealt with by patching widgets rather that exiting bonobo as I think it should on desktop logout.

I'm working out this threading process as it relates to cron and anacron as my knowledge is more than a little deficient. So for me this is a curiosity/learning thing. There's a mathematical issue with assumptions that even if your really sure about any given assumption by the time you stack several assumptions dependently you are almost certainly wrong. So the way I fork possibilities isn't explained very easily. It's only easy when you assume the answer already exist in your domain of presumptions.

Give me some more time to learn and formulate test, though I'm aware of your limitations in a production environment. I may ask you to consider temporarily moving some scripts or kill the process of certain services, but I need to know exactly what presumptions such test would falsify. For that I need to study. Even if something is found that fixes it for the moment it's almost certainly has little relevance in defining the actual problem. It's sort of like Christmas tree lights in reverse. I'll also make a data sheet based on what information has already been given. I'll ask more questions when I a better idea of which ones may be the most relevant. Can't promise you any good, but I'll learn.

---

### Post by my_wan on 2010-03-25
I have no doubt that hardware (bad or not) is at the root of the problem. However, I still think software is responding badly. Thus tracing it down the point in software could still give a way to patch around the reboot issue.

Let's throw a wider net...
Clues (w/speculation):
(1) Fan goes to high speed (heat apparently not at fault)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617)
Here in the comments:
[https://bugzilla.kernel.org/show_bug.cgi?id=5670](https://bugzilla.kernel.org/show_bug.cgi?id=5670)
setting ec_burst=1 fixed a different fan problem (notebooks) for some. This would tie into WLAN Wakeup, burst mode (hard drive), and acpi.

From tomgriffing:
(2) Mar 11 01:55:09 phoenix dhcdbd: Started up. [...] Mar 11 02:55:21 phoenix syslogd 1.4.1#21ubuntu3: restart.
Mar 11 02:55:24 phoenix dhcdbd: Started up. [...] Mar 11 03:55:40 phoenix syslogd 1.4.1#21ubuntu3: restart. etc.
Here the timing was an hour but correlated with dhcdbd, which is a dbus interface for the network manager. 
[http://packages.ubuntu.com/sl/dapper/dhcdbd](http://packages.ubuntu.com/sl/dapper/dhcdbd)
Wonder if ACPI had a wake on LAN set in that case? It shouldn't matter if nothing was asleep, but the event might still occur regardless. Referring back to your case it would explain the reboot time offsets from an hour, timed from reboot. On my own installation when I left it on overnight it would be off when I woke up. After setting power management to "never" it hasn't happened since. Loads of people reporting inability to get their Ubuntu to wake up from sleep.

(3) Apparently you changed hard drives if I understand correctly. Do you have "Burst Mode" enabled,  ACPI port 66 command (0x82 Burst Enable)? Perhaps it is different on your old hard drive, refer back to ec_burst in (1).

In going through bug reports etc., it appears to me that there's a whole range of bugs associated with ACPI issues varying on different platforms. Including on my installation. This could even be at the root of a host of other ill defined bugs. Your right that the variation in reboot offsets should be even more consistent per clock with cron. ACPI management is timed from events, not a set clock time. But you reported some strange occurances with clock settings to.

Suggestion:
Set all power management events to never, turn off any power management running. Your "green" monitor may not be so green anymore. I would even include your apcupsd in this if power management doesn't fix it, but I 'think' it works as a separate daemon through usb. Check your bios for burst mode settings on the hard drive. Not sure how you would determine how it was set for the old hard drive. I would make notes and test setting related to burst mode and ACPI when a new round of reboots started. Also try and grep the log files for any time stamps within a few minutes prior to the reboots, say anything logged within 5 minutes prior to each reboot. It could find a pattern that's being missed. Hopefully you can configure around the issue, but until then everything must be considered.

1. What do you run in terms of DHCP client/server on that machine?
2. Can you cross reference DHCP updates, if any, with the reboot times?
3. Did the reboots started 'after' changing the hard drive that was lost in a power outage?

On tomgriffing machine the relation between dhcdbd and ACPI is a little specious, but not entirely unreasonable. Removing jobs associated with an event often doesn't remove the event from being triggered. For now I would try the bios burst mode and ACPI settings as soon as the reboots start their cycle again. If this works it seems likely it's tied to a whole host of unresolved bugs that manifest quiet differently on different machines and OS's.

Good luck

---

### Post by dgermann on 2010-03-25
my_wan--

To respond to your post in # 136, I do not log out of the desktop at night--merely activate the lock screen button.

---

### Post by dgermann on 2010-03-25
my_wan--

This responds to your post #137:

My box is tower model that is put together by my computer supplier, using an Intel DG33FB mobo. I have four other boxes (3 Ubuntu 8.04.4) and one WinXP Pro--those each have an Intel 915GAVL mobo. No Fujitsu, which is what was mentioned in the one thread you linked.

If it matters, my box lies on it side under the pedestal of my desk with at least 6 inches of clearance on two edges (back and bottom), 1.5 inches on the side with the grille in it, and the other two edges are open to the room. I have had Computer Temperature Monitor 0.9.6.1 running on it for a year or so, and in the summer it runs in the mid 30 degrees, and in the winter the upper 20s (Centigrade). No spikes I have seen.

(2) I do not put my computer in sleep mode.

(3) I don't know what burst mode is. How would I tell if I had it, please?

You suggest I grep the log files for about 5 minutes either side of a reboot. If you know, what is the command line for that? If you don't know, I'll see if I can do a web search on it.

Power management is set to never on Actions for both AC and UPS power. The Display is set to a time interval--40 and 23 respectively. See any reason to change the screen settings?

1. dhcp is auto config. This is a client machine. The server is an older emachines running rh 9.0. There is also a router if that makes a difference.

2. cross referencing dhcp updates--would not know how to do that.

3. yes, the reboots started after the mobo was replaced.

Thanks for bringing your knowledge to bear here, my_wan!

---

### Post by my_wan on 2010-03-28
Sorry about being away, the Gnome GUI is really starting to irk me pretty bad. I'm forced to write a wrapper for every CL with switches I want access to in Nautilus file browser, because it's too brain dead to know what a command line is. 'Open With' strips any args from the command! Even many switches have equal signs with no spaces breaking default GUI style wrappers. Who would have ever thunk it, a GUI on a Unix system that doesn't understand what a CL is... That should be nearly all a GUI needs to be able to understand!!! Anyway...

I'm well aware that most of those systems was different from yours. In my research what I noticed though was an ACPI problems across about every hardware setup, including my own. Also the fundamentals of the architecture doesn't change that much, but the variations can lead to different symptoms. I even made a spurious connection between ACPI and DHCP through NIC card events. Probably off base in your case but probably also a mistake to ignore. Still exploring the neat 'upstart' system Ubuntu uses. Can't say how close the reasoning is to the actual problem in your case, but the guesses are worth testing.

I see you've already figured out how to get into the wtmp* file. I need to write a good script for parsing log files. You can grep the log piecemeal style. The log files look something like this for DHCP updates:
Mar 24 12:31:24 XXXX NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot

I assume the 'reboot' is just the device here, not the machine. As my computer didn't actually reboot at these times, though it shows similar entries about every 3 hours in my log files.

You can simply: $ grep $search_string /var/log/*log* >> $text_file, replacing $search_string with a partial date or other string you want. Then repeating the grep on the output $text_file to narrow the content. There's also a filter built into Ubuntu's log file viewer, but it's messed up because every time you select another log category it deselects your filters.

That's the hard way. By using regex with some awk and sed you can make the search as specific as you want. Perhaps someone better than me can post a better date filter. I need to write a library of script functions for this kind of thing, but getting a usable GUI has to come first. I'm lucky to remember a random 3 digit number a full 5 seconds, which is why I need a useful GUI that's hasn't been developed yet for Unix boxes. I can figure anything out, but the dictionary labels for everything eats my lunch. I'll be a lot more productive when I get my GUI app developed a bit more.

---

### Post by dgermann on 2010-03-28
my_wan--

Thanks!

I only understood about a third of what you wrote, but that is probably OK. ;)

Let me know when you get some clues and I will try out some things to see if they get us closer.


Thanks, my_wan!

---

### Post by dgermann on 2010-06-20
Hi all--

Just a report: rebooted again today. Last time was January 2, so just over half a year.

I ran the tune2fs thing and we will see what happens....

---

### Post by Gatewest on 2010-06-24
I have been experiencing the exact same issue on two of my servers.

One is running 9.10 and the other is running 10.04.  Both are running identical hardware right down to the last bolt.

One machine (message):
Jun 24 10:55:06 internal kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 24 10:55:06 internal rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="985" x-info="http://www.rsyslog.com"] (re)start
Jun 24 10:55:06 internal rsyslogd: rsyslogd's groupid changed to 103
Jun 24 10:55:06 internal rsyslogd: rsyslogd's userid changed to 101
Jun 24 10:55:06 internal kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 10:55:06 internal kernel: [    0.000000] Initializing cgroup subsys cpu

(kern)
Jun 24 10:55:06 internal kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 24 10:55:06 internal kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 10:55:06 internal kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 24 10:55:06 internal kernel: [    0.000000] Linux version 2.6.32-21-server (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 (Ubuntu 2.6.32-21.32-serv
er 2.6.32.11+drm33.2)
Jun 24 10:55:06 internal kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-server root=/dev/mapper/internal-root ro quiet
Jun 24 10:55:06 internal kernel: [    0.000000] KERNEL supported cpus:
Jun 24 10:55:06 internal kernel: [    0.000000]   Intel GenuineIntel
Jun 24 10:55:06 internal kernel: [    0.000000]   AMD AuthenticAMD


The other (message):
Jun 24 11:01:54 130 syslogd 1.5.0#5ubuntu3: restart.
Jun 24 11:01:54 130 kernel: Inspecting /boot/System.map-2.6.28-19-server
Jun 24 11:01:54 130 kernel: Cannot find map file.
Jun 24 11:01:54 130 kernel: Loaded 49159 symbols from 22 modules.
Jun 24 11:01:54 130 kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun 24 11:01:54 130 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 11:01:54 130 kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 24 11:01:54 130 kernel: [    0.000000] Linux version 2.6.28-19-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #61-Ubuntu SMP Thu May 27 00:22:27 UTC 2010 (Ubuntu 2.6.28-19.61-server)
Jun 24 11:01:54 130 kernel: [    0.000000] Command line: root=/dev/mapper/130-root ro quiet splash 
Jun 24 11:01:54 130 kernel: [    0.000000] KERNEL supported cpus:

(kern):
Jun 24 11:01:54 130 kernel: Inspecting /boot/System.map-2.6.28-19-server
Jun 24 11:01:54 130 kernel: Cannot find map file.
Jun 24 11:01:54 130 kernel: Loaded 49159 symbols from 22 modules.
Jun 24 11:01:54 130 kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun 24 11:01:54 130 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 11:01:54 130 kernel: [    0.000000] Initializing cgroup subsys cpu

The strange thing is I had experienced the "130" machine rebooting previously but thought it was hardware.  Now I have that machine AND "internal" rebooting at nearly the same instant.  Both are hooked up to different UPS and circuit.  The hardware is identical on both:

 - OCZ Titanium XTC PC2-6400 4GB 2X2GB DDR2-800 CL4-4-4-15 DDR2 240PIN Dual Channel Memory Kit
 - ASUS P5QPL-VM Epu Uatx LGA775 G41 DDR2 1PCI-E16 1PCI-E1 2PCI HDMI Video Sound GBLAN Motherboard
 - Intel Core 2 Duo E6300 Dual Core Processor LGA775 2.8GHZ 1066FSB 2MB Retail Box
 - Intel PRO/1000 GT Gigabit Ethernet PCI Network Adapter Card NIC
 - APC BACK-UPS RS 1500VA 865W UPS 8 Outlet 340J LCD Display RJ-45 Protection (Part#: BR1500LCD)

There are definitely no heat-associated problems.  The computers are in a climate-controlled vault, at 20'C (68'F).  One has been in use offset by 6 months from the other, both bought at the same time, from the same batch of manufactured components.  Both have identical BIOS (not sure of the version).  One is accessible from the internet, one is behind redundant firewall (no chance of the second being compromised).

Any advice?  This seems like a Ubuntu bug to me.

---

### Post by dgermann on 2010-06-24
Gatewest--

How odd! Both rebooting at the same instant?

What is that lowmem entry all about?

Have you tried the tune2fs trick? With what results?

The heat can be what is generated internally, not just from the environment. Are you monitoring cpu temps?

What are you finding out?

---

### Post by Gatewest on 2010-06-24
> **dgermann said:**
> Gatewest--

How odd! Both rebooting at the same instant?

What is that lowmem entry all about?

Have you tried the tune2fs trick? With what results?

The heat can be what is generated internally, not just from the environment. Are you monitoring cpu temps?

What are you finding out?

Hi dgermann,

They both rebooted at the same instant (the clock was off by a few minutes on one machine, which is why the log entries don't match time-wise, but they both rebooted at the same instant).  I'm not sure what the lowmem entry is about, either.

I haven't tried tune2fs.  What does it do?

There is literally no heat generated by the machines.  They have very little load, and run at only 1.6 out of the clocked 2.8 GHz.  The machines each draw a total of 17 - 20 watts of electricity each according to power measurements which indicates very little load.  I'm using Antec power supplies, so nothing el cheapo there.  CPU usage usually is around 7-10 %.  Generally speaking these are low-load systems, so there's no problems with heat, load, etc.

Like I said earlier, they are both identical hardware, one with 9.10 and one with 10.04.  The 10.04 machine is Server with the GUI installed on top. The 9.10 is Server cli only.  I'm going to see tomorrow about disabling ACPI on them to see if it makes a difference.  I'm thinking about setting up a third machine to see if all 3 reboot at the same time next time.

If I disable ACPI in the BIOS, do I need to do anything in Ubuntu, or will it detect that ACPI is disabled?  Do you think this will solve the issue (I have seen something like "ACPI Bad address" in the log)?

Any help you can provide would be greatly appreciated.  I'm not a computer nooB, but I'm a bit new to Ubuntu and it's fickle nature, so it seems.  I've used OS X as a server OS since 2000 (yes, public beta).  I'm trying to migrate my company's dependence off of OS X towards Linux so that we can use generic cheap hardware.

Thanks.

Cameron
Gatewest

---

### Post by dgermann on 2010-06-27
Gatewest--

The tune2fs trick is in post # 37 above. Try that and see if it at least stops the rebooting for a while for you.

I googled lowmem and found quite a bit of stuff--you might take a look and see if there are any clues to be had there. When I got started up the linux learning curve somebody told me "Google is your friend." It has proven true.

Sorry, I don't know anything about ACPI.

It sounds to me like either the software gremlins that have hit a few of us in this thread, or hardware. Have you tried swapping out memory and see if that makes a difference? My problems started soon after I got a new mobo and new memory on it. I don't have any spare memory or I'd try that myself.

Let us know if either idea gives you any clues....

---

### Post by Gatewest on 2010-06-29
Hi Doug,

I've started having some other glitches with Ubuntu.  It started after I first installed, I could not at all set a static IP address on the machine.  I searched many forums, and discovered it was a bug since about 8.10 and people's only solution was to "use DHCP, it's better anyways".  For a server, that's not usually an option.  Fine, I figured.  So I installed a router on the network, set it for DMZ and put the server on DHCP with the router then having a static IP address.  That worked fine, until the machine decided that it didn't want to renew the DHCP lease (3 times!).  Only way to solve it was to reboot.  Not fun.  I brought down an entire company for 2 hours while I tried to troubleshoot the network on this crazy box.  It seems Ubuntu (at least 10.04 and 9.10) is FULL of bugs!

I'm going to try CentOS 5.5 and see how that works for me.  At least when I installed it on a test machine it let me enter a static IP address, which never took on Ubuntu.

Thanks for your help.  If CentOS doesn't work well for me, I'll be back, and I'll try more troubleshooting.

---

### Post by dgermann on 2010-06-29
Gatewest--

Wow! That's a problem.

Right now, my network relies partially on static ip addresses, partially dhcp. So I am interested in what you find.

Couldn't a server work on a dhcp assigned address? (That is, if it would renew its lease.) Another option might be to drop back to 8.04lts until the problem is resolved.

I'll have to take a look and see what kinds of bugs people are finding--I was about ready to move my machines from 8.04 to 10.04. Thanks for the heads up!

---

### Post by Gatewest on 2010-06-30
Hi Doug,

Dropping down to 8.x is not an option for me.  In regards to DHCP and Static, I *MUST* use static IPs for my servers.  DHCP won't work, and isn't ideal, either.  You should not use DHCP for a server which you access via DNS lookups or IP address.  My internet provider drops a 100Mb fiber connection here, and all they provide is 13 static ip addresses.  Our servers are provided static addresses and our internal network is behind a router using DHCP.  In order for DNS to function properly, it has to refer to servers that don't have their IP addresses change.

I tried CentOS but found out why most people use Ubuntu.  I don't know how to install software by downloading source code and dependancies and compiling it.  That just doesn't work for me.  I like apt-get blah and it works.

I removed the Intel PCI gigabit ethernet card to see if that is the trouble and reverted back to the Atheros on-board ethernet.  I also updated the BIOS to the most recent version.  I also checked the spec for the RAM I have regarding the proper voltage, and it wasn't setup properly in the BIOS (was 1.5v should have been 2.1).  We'll see if that solves to rebooting problem.  Now if only I could solve my network problem.

In the end, I wish I had never strayed from Mac OS X as my server platform.  That works FLAWLESSLY every time, and that's worth the price of admission alone.

Cameron
Gatewest

---

### Post by dgermann on 2010-06-30
Cameron--

Wish I had a solution for you.

I have found good help at these two forums, and if you have not tried them, you might want to try there and see.

[http://www.linuxquestions.org]("http://www.linuxquestions.org")
[URL="http://www.justlinux.com/forum/index.php"]
http://www.justlinux.com/forum/index.php[/URL]

There has to be a solution.

As an aside, what little I have seen of mac is that they seem to have some core that looks like linux.

So I hope you solve your problems and that the rebooting is solved in a way that might give us a clue to the question of this thread. ):P

---

### Post by bigwigbaz on 2010-07-02
> **Gatewest said:**
> Hi Doug,

Dropping down to 8.x is not an option for me.  In regards to DHCP and Static, I *MUST* use static IPs for my servers.  DHCP won't work, and isn't ideal, either.  You should not use DHCP for a server which you access via DNS lookups or IP address.  My internet provider drops a 100Mb fiber connection here, and all they provide is 13 static ip addresses.  Our servers are provided static addresses and our internal network is behind a router using DHCP.  In order for DNS to function properly, it has to refer to servers that don't have their IP addresses change.

I tried CentOS but found out why most people use Ubuntu.  I don't know how to install software by downloading source code and dependancies and compiling it.  That just doesn't work for me.  I like apt-get blah and it works.

I removed the Intel PCI gigabit ethernet card to see if that is the trouble and reverted back to the Atheros on-board ethernet.  I also updated the BIOS to the most recent version.  I also checked the spec for the RAM I have regarding the proper voltage, and it wasn't setup properly in the BIOS (was 1.5v should have been 2.1).  We'll see if that solves to rebooting problem.  Now if only I could solve my network problem.

In the end, I wish I had never strayed from Mac OS X as my server platform.  That works FLAWLESSLY every time, and that's worth the price of admission alone.

Cameron
Gatewest

Cameron, Have you tried Debian on the servers? I know the forums and support are not quite as popular but it is, after all what debian was created for. Ubuntu is built on the 'unstable' testing branch of deb, may be worth a go? I am certainly no expert but I understand the debian server installer is pretty much identical to the ubuntu server installer. Sorry if someone has already suggested this, I have not read the thread in detail. Debian also uses apt, I think it should fit the bill. 

Apologies to Doug, this does not answer your problem.

---

### Post by Gatewest on 2010-07-12
> **bigwigbaz said:**
> Cameron, Have you tried Debian on the servers? I know the forums and support are not quite as popular but it is, after all what debian was created for. Ubuntu is built on the 'unstable' testing branch of deb, may be worth a go? I am certainly no expert but I understand the debian server installer is pretty much identical to the ubuntu server installer. Sorry if someone has already suggested this, I have not read the thread in detail. Debian also uses apt, I think it should fit the bill. 

Apologies to Doug, this does not answer your problem.

Hi Doug,

I did not know that Ubuntu was based on the unstable Debian release.  I have not tried Debian directly, only Ubuntu.  I will have to setup a test machine and configure it for my network and go from there, which will take me considerable time given all of the other things I do at work.  I will report back if I continue having reboot issues and whether Debian solved the problem.  Thanks for the suggestion!

Cameron

---

### Post by dgermann on 2010-07-12
Cameron--

I did not know that either.

It would seem to me that for it to be a valid test, one of the two machines you had the rebooting problems with would have to be the new Debian test box, right?

I'm still thinking the problem is memory chips.

Are you still having the reboots, Cameron?

---

### Post by Gatewest on 2010-07-13
I last booted it on June 30, and we closed up for vacation until today.  I checked the logs and it rebooted on July 3 twice in one hour, and has been running since (8+ days) straight.  That was one machine, the other has not rebooted since I posted a message here.  I'm downloading Debian (all 5 DVDs!) to try and see if it reboots as well.

---

### Post by mister_p_1998 on 2010-07-13
Might be worth booting a live CD and leaving it for 61 minutes, to see if its hardware...

Steve

---

### Post by dgermann on 2010-07-13
Cameron--

Good luck!

Steve--

Great idea!

---

### Post by mooseydoom on 2010-07-14
Hey, I have a similar problem on a CentOS 5 server.  The server restarts every 61-ish minutes.  This started a month ago.  Changing some bios settings temporarily fixed this, but the problem is back again now.  I stopped the cron service, and the server still reboots, so I don't think it's cron-related.  I reset the bios again, and the server's been up for over an hour now, but I feel like it is likely to relapse.  Just adding my experiences here.

---

### Post by dgermann on 2010-07-14
mooseydoom--

Sorry to see you're having the problems too.

Have you tried the tune2fs trick to see if that helps you? See post #37 above.

Please keep us informed about what you try and what hopefully works for you.

One thing that I think is worth checking out is to swap out your memory chips and see if that works. (I'm gun shy--I fried a board adding memory a while ago!)

---

### Post by Gatewest on 2010-08-04
After a while away, I've come back to report:

3 separate machines, one with Debian 5 Lenny, one with Ubuntu Server 9.04 and one with Ubuntu Desktop 9.10.  All identical hardware.  One has original motherboard BIOS, others are updated to latest version.  One has ram overvolted 2.3v purposely, other undervolted to minimum 1.5v.  Two directly connected to the internet, one behind a router and firewall.  All 3 are on separate power circuits, all 3 have battery backup.  All 3 were booted at different times.

On Saturday, all 3 rebooted simultaneously.  It is now the most bizarre thing I have ever seen.  Not only that, but a Mac G5 ran without incident (and it is far more sensitive to power and heat issues than these machines).

The only thing the same in the entire scenario is that all 3 machines point to the same internal DNS server, running Ubuntu 6.10 or 7.04 (can't remember).  They all rebooted simultaneously before at the same instant before the hour (x:57) as previously when it happened simultaneously.  Could there be some sort of kernel event or daemon being triggered at a certain moment that is causing this to happen on three separate machines simultaneously?  With different "versions" of Linux?  And, how can it be hardware-related 3 times over, but yet they reboot at the exact same second?  If it were hardware, it would be random.  It seems that by them rebooting simultaneously it would be a kernel or daemon event triggering it somehow (like a bug in the kernel or a driver).

I am almost ready to give up and just let the reboots happen.

Cameron

---

### Post by dgermann on 2010-08-04
Cameron--

Really weird!

What if the three machines did not all have the same clock times? Would they all reboot at what they "thought" was the same time?

And would disconnecting them from the common DNS server make any difference?

Are there any logs for the DNS server showing events at that same instant?

Anybody else have any ideas?

---

### Post by mister_p_1998 on 2010-08-05
That definitely sounds like a power spike to me.....
Steve

---

### Post by Gatewest on 2010-08-05
> **dgermann said:**
> Cameron--

Really weird!

What if the three machines did not all have the same clock times? Would they all reboot at what they "thought" was the same time?

And would disconnecting them from the common DNS server make any difference?

Are there any logs for the DNS server showing events at that same instant?

Anybody else have any ideas?

Hi dgermann,

Previously I did have 2 machines reboot at the exact instant, and one had its clock off by about 5 minutes.  I haven't tried disconnecting them from the DNS server.

There are no log entries for any of the events.  The previous log entry prior to reboot was minutes before, and wasn't unusual.  This is all that's reported once it reboots:


Jul 31 13:54:05 133 kernel: imklog 3.18.6, log source = /proc/kmsg started.
Jul 31 13:54:05 133 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 31 13:54:05 133 kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 31 13:54:05 133 kernel: [    0.000000] Linux version 2.6.26-2-amd64 (Debian 2.6.26-24) (dannf@debian.org) (gcc version 4.1.3 20080704 (prerelease) (Debian 4.1.2-25)) #1 SMP Sun Jun 20 20:16:30 UTC 2010
Jul 31 13:54:05 133 kernel: [    0.000000] Command line: root=/dev/md0 ro quiet
Jul 31 13:54:05 133 kernel: [    0.000000] BIOS-provided physical RAM map:

One thing that bothers me is that partway through the log:
Jul 31 13:54:05 133 ntpdate[2145]: step time server 216.234.161.11 offset -2.758031 sec

This is on the Debian machine.  On the Ubuntu machine:

Jul 31 13:53:39 internal kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 31 13:53:39 internal rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1021" x-info="http://www.rsyslog.com"] (re)start
Jul 31 13:53:39 internal rsyslogd: rsyslogd's groupid changed to 103
Jul 31 13:53:39 internal rsyslogd: rsyslogd's userid changed to 101
Jul 31 13:53:39 internal rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jul 31 13:53:39 internal kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 31 13:53:39 internal kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 31 13:53:39 internal kernel: [    0.000000] Linux version 2.6.32-23-server (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 09:11:11 UTC 2010 (Ubuntu 2.6.32-23.37-server 2.6.32.15+drm33.5)
Jul 31 13:53:39 internal kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-23-server root=/dev/mapper/internal-root ro quiet
Jul 31 13:53:39 internal kernel: [    0.000000] KERNEL supported cpus:

For NTP on the Ubuntu machine:
Jul 31 13:51:56 internal ntpd[2774]: kernel time sync status change 2001
Jul 31 13:57:40 internal ntpd[971]: synchronized to 91.189.94.4, stratum 2
Jul 31 13:57:40 internal ntpd[971]: kernel time sync status change 2001

I'm still concerned that somehow ntp is crashing the system somehow, or maybe a DNS request is poisoning the system somehow.

Any thoughts?

---

### Post by dgermann on 2010-08-05
Cameron--

Anything in the logs for the DNS server at that time?

I thought you had eliminated the idea of a power spike, true?

And I don't remember if you said whether the tune2fs trick works for you or not.

---

### Post by dgermann on 2011-10-05
Friends--

Twice this year so far: January 10th and then again this morning.

apcupsd shows now power events during the latest period.

---

### Post by CharlesA on 2011-10-05
Are you still running 8.04? I didn't see any mention of which version of Ubuntu you were running.

---

### Post by dgermann on 2011-10-05
CharlesA--

Thanks for your reply.

Nope: I try to keep it upgraded to the latest LTS (10.04.3 LTS):

```
uname -a
Linux doug2 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

```

Thanks, Charles!

---

### Post by CharlesA on 2011-10-05
So the problem was happening on 8.04 and 10.04. Is this a server install or desktop install?

It really sounds like some sort of hardware problem to me, since it's so intermittent.

---

### Post by dgermann on 2011-10-05
Charles--

Thanks for helping me!

This is a desktop install.

Yes, we have (on this thread mostly) looked into that. The thing that is curious to me is that other people are experiencing the same thing, too.

Power issues also have been mentioned--but today is a beautiful day here, blue skies, light airs, and has been that way for 4 or 5 days, so although this is in the country where the electricity can be a problem, it seems unlikely that is the culprit.

I am hoping that by keeping a running log of the issues on this thread, someone might see a clue.

Thanks, Charles!

---

### Post by CharlesA on 2011-10-05
I'm not sure where to even start outside of trying a clean install - but that wouldn't tell you if the problem is fixed or not since the reboot is sporadic.

Are you using the same hardware as before?

---

### Post by dgermann on 2011-10-05
Charles--

Yes, same hardware.

The last upgrade I did (to 10.04) was an upgrade and not a clean install.

You are right: if the problem persists after a clean install, we have learned nothing. If it goes away, put it down to a gremlin trapped in an Ubuntu versions time warp!

I may just do a clean install some weekend when I have a couple days to spare. Or do that when 12.04 LTS comes around.

---

### Post by CharlesA on 2011-10-05
I'd go for a clean install and see what happens. 

If it still happens after a clean install, then I'd say it's more then likely a hardware problem.

---

### Post by dgermann on 2011-10-05
CharlesA--

Yes, worth a shot. Thanks!

But there are a lot of settings I have here, such as shortcuts in OOo, so I need to be able to dedicate a large block of time!

Thanks, Charles!

---

### Post by CharlesA on 2011-10-05
I'd probably throw in another hard drive and do a clean install on it and see if the problem persists. That way you still have everything from the other drive is working order.

---

### Post by dgermann on 2011-10-05
CharlesA--

That's a really good idea! Thanks!

---

### Post by CharlesA on 2011-10-05
No problem. Just trying to narrow down the cause a bit. I figure that if it is still acting up after a clean install, that it's probably a hardware thing that is causing it to act funky, even though there isn't anything in the logs.

---

### Post by brianmrowe on 2011-11-30
This is an old thread. Wondering if it was every fixed.  My machine is doing this now.  And while people are convinced its hardware, I think nothing about this points to hardware.  No way does hardware just turn off every 61 mins, no matter what the usage pattern.

---

### Post by CharlesA on 2011-11-30
I don't think there was any resolution.

---

