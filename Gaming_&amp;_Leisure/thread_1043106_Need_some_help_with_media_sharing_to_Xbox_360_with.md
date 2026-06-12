---
title: "Need some help with media sharing to Xbox 360 with uShare"
date: 2009-01-18
forum: Gaming &amp; Leisure
---

### Post by rotor_of_the_internet on 2009-01-18
Hi,

I'm new to Linux, I'm running ubuntu/Intrepid. I've set up an uShare to share media to my Xbox 360. I've been trying to get this to work for days, but I haven't been able to get any media shared on my 360 so far.

My ushare.conf looks like this: 

> # /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/disk/Vid

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=



I disable the ubuntu ufw firewall by sudo /etc/init.d/ufw stop

In my /etc/hosts.allow I've added the following line to allow my network access to my machine:
ALL: 192.168.123.*

I start ushare like this:

> rotor@rotor:~$ ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.123.127:49153
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/disk/Vid
Found 4 files and subdirectories.


Which looks normal. I can now access the Web interface at [http://192.168.123.127:49153/web/ushare.html](http://192.168.123.127:49153/web/ushare.html). Interestingly, I can also access this address on my Windows XP machine.

/media/disk/Vid is mounted, it has a .mp3 file, an .avi file and a .jpg file in it solely for testing purposes.

My uShare shows up on my Xbox 360 when I go to My Xbox -> System Settings -> Network settings -> Test PC Connection. So it can actually see it's there. Now when I connect to it, it just times out.

When I run Windows Media Player 11 on my Windows XP machine and go to the Media Sharing options, it displays my Xbox 360 there. Since I'm running a UPnP service on my Ubuntu laptop, I'm thinking it should show up here as well?

I've check my router specifications and it supports UPnP.

Does anyone have an idea what I'm missing here? :confused:

---

### Post by rotor_of_the_internet on 2009-01-18
For some reason the 360 only finds my machine when I start uShare to the uShare daemon while it's already searching for PCs. I also opened up all the tcp/udp ports that the 360 required, that doesn't seem to help me either.

This is really driving me nuts :(

---

