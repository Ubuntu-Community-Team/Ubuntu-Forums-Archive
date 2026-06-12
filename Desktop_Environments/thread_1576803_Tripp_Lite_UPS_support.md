---
title: "Tripp Lite UPS support"
date: 2010-09-17
forum: Desktop Environments
---

### Post by Reactor89 on 2010-09-17
My question is fairly simple: Are there Tripp Lite UPS (uninterruptible power supply) management software or daemons that are ubuntu compatible?

Added info:

I've found openSUSE and Fedora compiled versions of the Tripp Lite developed PowerAlert UPS management software, yet nothing for ubuntu.

If it helps, my model of UPS is a [Tripp Lite SMART1050SLT]("http://www.tripplite.com/shared/product-pages/en/SMART1050SLT.pdf").

Goal:

I want some kind of daemon that will trigger scripted events when the UPS batteries reach a certain charge level.

Example: 

At 25% battery charge, shutdown a computer on my local network if it's online. At 15% battery charge shutdown the ubuntu system that is running the daemon (last computer to shutdown).

Ideas?

Reactor89

---

### Post by tgalati4 on 2010-09-17
The only two protocols that I know of:  apcupsd and nut

Are the compiled versions under openSUSE and Fedora open source?  If so, you might be able to compile them for Ubuntu.  Try sending an email to Tripp Lite and post their reply.  I haven't seen anything really funny this week.

Another way to tackle this problem:  buy a used APC Smart UPS or Back UPS Pro--the older ones with metal cases.  The plastic ones catch fire.  Put in new batteries.  Make a special serial cable for it (search the web for instructions) or use USB if equipped.  Hang off of your server and set up broadcast capability.  Put apcupsd on all your client machines and set to listen for network shutdown calls.  Now all of your client machines can have any brand of UPS with no need to hook up.

The server with the APC UPS would naturally be the last one to shut down since the broadcast messages get sent out first, including emails of power events.  You can set timers and battery levels, etc.

Here's a config file for a networked APC UPS that has been running for years (since 6.06) on a Dapper Drake desktop/server: 


tgalati4@tubuntu2:/etc/apcupsd$ cat apcupsd.conf
## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.12.4 (19 August 2006) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
UPSNAME TerryLab


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
UPSCABLE simple

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
# usb       <BLANK>          Most new UPSes are USB.
#                            A blank DEVICE setting enables
#                            autodetection, which is th best choice
#                            for most installations.
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
#                            rfc1628 UPS-MIB. Port is usually 161. 
#                            Community is "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
UPSTYPE dumb
DEVICE /dev/ttyS0


# LOCKFILE <path to lockfile>
#   Path for device lock file.
LOCKFILE /var/lock

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
ONBATTERYDELAY 20

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
MINUTES 5

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
TIMEOUT 30

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 15

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
#  Default value is 0.0.0.0 that means any incoming request will be
#  serviced but if you want it to listen to a single subnet you can
#  set it up to that subnet address, for example 192.168.10.0
#  Additionally you can listen for a single IP like 192.168.10.1
NISIP 192.168.1.114

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
#            a UPS and controlling it via the network              

# The configuration statements below are used if you want to share one 
# UPS to power multiple machines and have them communicate by the network.
# Most of these items are for Master/Slave mode only, however NETTIME is
# also used for Client/Server NIS networking with the net driver.

# NETTIME <int>
#   Interval (in seconds) at which the slave or client polls the master
#   or server. This is applicable to BOTH master/slave and client/server
#   (NIS) networking.
NETTIME 100

#
# Remaining items are for Master/Slave networking ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster | netslave | netmaster ]
#   Normally standalone unless you share a UPS with multiple machines.
#   
UPSCLASS netmaster

# UPSMODE [ disable | share | net | sharenet ]
#   Unless you want to share the UPS (power multiple machines),
#   this should be disable.
UPSMODE net

# NETPORT <int>
#   Port on which master/slave networking communicates.
NETPORT 6544

# MASTER <machine-name>
#   IP address of the master. Only applicable on slaves.
#MASTER

# SLAVE <machine-name>
#   IP address(es) of the slave(s). Only applicable on master.
SLAVE hpubuntu
#SLAVE slave2

# USERMAGIC <string>
#   Magic string use by slaves to identify themselves. Only applicable
#   on slaves.
#USERMAGIC

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 300

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
DATATIME 300

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
UPSNAME TerryLab

# Battery date - 8 characters
BATTDATE 06/03/04

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
SENSITIVITY M

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
SLEEP 30

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

# Battery change needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
BEEPSTATE T

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
SELFTEST Off

---

### Post by Reactor89 on 2010-09-18
> **tgalati4 said:**
> The only two protocols that I know of:  apcupsd and nut


I maybe misinformed but I think I'm fairly certain that apcupsd and nut are both Daemons/Tool packages not protocols. They use a variety of protocols to do their job and be compatible with many brands of UPS (see: [http://networkupstools.org/protocols/](http://networkupstools.org/protocols/)). And yes, those are the options I know of too.

> **tgalati4 said:**
> 
Are the compiled versions under openSUSE and Fedora open source?  If so, you might be able to compile them for Ubuntu.  Try sending an email to Tripp Lite and post their reply.  I haven't seen anything really funny this week.


My guess is neither the openSUSE or fedora packages are open source.

Yet I fired off the question:

> Question: Can I get either PAL (PowerAlert Local) or PANSA (PowerAlert Network Shutdown Agent) software be compiled for Debian (another breed of GNU/Linux, different from fedora and openSUSE)? More specifically, I'm using the Ubuntu 10.04 (Debian derived) operating system. We (the Debian community) can also compile and debug are own version of the software if we get source code. If the official answer to Debian support is "no", I challenge Tripp Lite to give me specific reasons why.I will post the response.

In regards to using used APC power supplies that are compatible, been there done that, and haven't had a whole lot of luck with them. True the ones with metal cases don't burn quite as completely but I've had ones where their insides burn up all the same. For now, I'm done with that.

The config file you posted looks fairly straight forward, so once I get some software that is compatible, the rest should be gravy.

Otherwise, I may need to talk to the developers for nut and see what processes they have for decoding the Tripp Lite protocol myself. That would be kind of cool yet time consuming.

Thanks for the input tgalati4, I will post any new info I get,

Reactor89

---

### Post by tgalati4 on 2010-09-18
APC UPS's tend to burn up under the following:

1.  Overload them.  A 500VA unit can only realistically support 250 watts for 20 to 40 minutes.  APC typically designs the heatsinks to support 5 minutes of power.  Try to run for 20 minutes and you may see smoke.

2.  Lightning.

I have found the older, metal case ones can take bigger batteries and you can run them at lower loads (say 1/3 to 1/2 of rating) for longer/useful periods of time.

And you are correct, apcupsd and nut are daemons.  Your link is a nice collection of UPS protocols.

Good luck.

---

### Post by Reactor89 on 2010-09-18
> **tgalati4 said:**
> APC UPS's tend to burn up under the following:
1.  Overload them.  A 500VA unit can only realistically support 250 watts for 20 to 40 minutes.  APC typically designs the heatsinks to support 5 minutes of power.  Try to run for 20 minutes and you may see smoke.


Exactly and as MOSFETs in the power supply are repetitively used these run time specs can go even lower. Hence the exploding of a UPS, then some :frown:, which is normally followed up by some roasting of some :popcorn: on burning UPS... :biggrin:

> **tgalati4 said:**
> 
I have found the older, metal case ones can take bigger batteries and you can run them at lower loads (say 1/3 to 1/2 of rating) for longer/useful periods of time.


I run external battery packs on my UPSs for exactly this reason. I don't really care if the UPS was "designed" to run a external battery pack or not.

Reactor89

---

