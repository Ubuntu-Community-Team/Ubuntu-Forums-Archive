---
title: "init.d scrips no longer auto running at startup"
date: 2010-07-13
forum: Desktop Environments
---

### Post by theOgFlomaster on 2010-07-13
so I have 3 scripts I had set up to run at startup for these 3 programs 

Sabnzbd
Sickbeard
CouchPotato

here is what my sabnzbdplus init looks like 

```
#This file is sourced by /etc/init.d/sabnzbdplus
#
#When SABnzbd+ is started using the init script, the
#--daemon option is always used, and the program is 
#started under the account of $USER, as set below
#
#Each setting is marked either "required" or "optional"
#leaving any required setting unconfigured will cause
#the service to not start.

#[required] user or uid of account to run the program as:
USER=xbmc

#[optional] full path to the configuration file of your choice
#			otherwise, the default locatin (in $USER's home
#			directory) is used:
CONFIG=

#[optional] hostname/ip and port number to listen on:
HOST=0.0.0.0
PORT=9000

#[optional] extra command line options if any:
EXTRAOPTS=
```

my runlevel is N 2 

my user account has all admin privileges and read/write access so I have no idea why it wouldn't start on bootup.

all of these scrips can be ran manually from transmission



-=Jason=-

---

### Post by theOgFlomaster on 2010-07-27
*BUMP*
what service could be interfering with these starting up?

---

