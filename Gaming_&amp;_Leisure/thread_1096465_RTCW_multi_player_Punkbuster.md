---
title: "RTCW multi player Punkbuster"
date: 2009-03-14
forum: Gaming &amp; Leisure
---

### Post by manij on 2009-03-14
Hi, I'm getting kicked out of the servers. the console is giving the following errors

[B][I]
UI menu load time = 5 milli seconds
CL_InitCGame:  3.44 seconds
58 msec to draw all images
Com_TouchMemory: 0 msec
execing wolfconfig_mp.cfg
usage: seta <variable> <value>
[skipnotify]^7This server is running ^4QMM^7 v^41.1.3^7
[skipnotify]^7URL: ^4http://www.q3mm.org/^7
^5PunkBuster Client: WARNING: ^7PB Kicks for Name Stealing and Locked Names and All PB Restrictions on this Server
[skipnotify]^4N^6D^9A^7 was killed by ^4P^0hantom ^4H^0omer^7's MP40
^5PunkBuster Client: 0 Current Cvar Violations
[skipnotify]^2{KT} ^3B A R^7 was killed by ^h:^aV^h:^aS^holdier ^aX^7's MP40
[skipnotify]^4K^0O^7R^1T^0EX^4*RF*^7 was blasted by ^!Mister^@Rogers^7's Panzerfaust
^5PunkBuster Client: Receiving from PB Server (v1.229 w)
Received signal 6, exiting...
Shutdown tty console[/I][/B]

sometimes I also get errors such as "unpure client"


About a couple of years ago, I managed to find intructions whihc solved all the above issue. I can't find them now.

could someone help this poor soul out please!

---

### Post by batharoy on 2009-03-15
Try doing a manual PB update.
The current version is 1.727, yours is 1.229.
Thats almost 3 years old.
[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

---

### Post by manij on 2009-03-15
How do I run the file?

I downloaded the pbsetup.run file

my wolfenstein is installed in /usr/local/games/wolfenstein

There also hidden file in the home folder 

home/.wolf with some config files in it?

Where do I runt his pbsetup.run file from? do I run it as root? Thanks for your help!

---

### Post by manij on 2009-03-16
I figured out how to install the update and i'm still getting kicked out. Help please!

[B][I]Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: File Not Found: pbcl.cfg
^5PunkBuster Client: Not Connected to a Server
^5PunkBuster Client: PunkBuster Client (v0.993 | A0) Enabled
^3PunkBuster Server: PunkBuster Server (v0.993 | A0 C0.0) **DISABLED**
Resolving wolfmotd.idsoftware.com
wolfmotd.idsoftware.com resolved to 192.246.40.70:27951
8 servers listed in browser with 120 players.
72 servers not listed (filtered out by game browser settings)
Resolving wolfmotd.idsoftware.com
wolfmotd.idsoftware.com resolved to 192.246.40.70:27951
174.34.173.100:27960 resolved to 174.34.173.100:27960
Resolving wolfauthorize.idsoftware.com
wolfauthorize.idsoftware.com resolved to 192.246.40.70:27952
^5PunkBuster Client: Connected to Server 174.34.173.100:27960
^5PunkBuster Client: Master Query Sent to (RTCW1.EVENBALANCE.COM) 192.246.40.80
^5PunkBuster Client: Received New Security Information

usage: seta <variable> <value>
^5PunkBuster Client: WARNING: ^7PB Kicks for Name Spamming and Non-standard Characters and Level 1 PB Restrictions on this Server
^5PunkBuster Client: Receiving from PB Server (v1.730 w)
^5PunkBuster Client: Received New Security Information
Received signal 6, exiting...
Shutdown tty console[/I][/B]


IS there some kinda configuration that I need to do?

---

### Post by Azure.Rise on 2009-03-16
I was having problems on that game with punkbuster too. What I did is in the terminal go to the install directory and run pbweb.x86 using sudo. Then go into the hidden directory for the game in your home folder and find the pb folder if pbweb.x86 isn't there copy it over and run it in the terminal. Look at the terminal results and make sure there were no errors like timeouts or anything else. If there was run it again until it gets it right.

---

### Post by manij on 2009-03-16
> **Azure.Rise said:**
> I was having problems on that game with punkbuster too. What I did is in the terminal go to the install directory and run pbweb.x86 using sudo. Then go into the hidden directory for the game in your home folder and find the pb folder if pbweb.x86 isn't there copy it over and run it in the terminal. Look at the terminal results and make sure there were no errors like timeouts or anything else. If there was run it again until it gets it right.

Here is the error in the terminal when I do this

***Gdk-CRITICAL **: file gdkgc.c: line 689 (gdk_gc_set_clip_rectangle): assertion `gc != NULL' failed.***

Here are the latest errors from starting the game

[B][I]^5[SIZE="5"]_PunkBuster Client: File Not Found: pbcl.cfg_
_^5PunkBuster Client: Not Connected to a Server_[/SIZE]
^5PunkBuster Client: PunkBuster Client (v0.993 | A0) Enabled
Resolving wolfmotd.idsoftware.com
wolfmotd.idsoftware.com resolved to 192.246.40.70:27951
7 servers listed in browser with 142 players.
73 servers not listed (filtered out by game browser settings)
Resolving wolfmotd.idsoftware.com
wolfmotd.idsoftware.com resolved to 192.246.40.70:27951
66.29.75.101:27960 resolved to 66.29.75.101:27960
Resolving wolfauthorize.idsoftware.com
wolfauthorize.idsoftware.com resolved to 192.246.40.70:27952
^5PunkBuster Client: Connected to Server 66.29.75.101:27960
^5PunkBuster Client: Master Query Sent to (MASTER3.EVENBALANCE.COM) 216.240.146.139
^5PunkBuster Client: Received New Security Information
^5PunkBuster Client: WARNING: ^7PB Kicks for Name Stealing and All PB Restrictions on this Server
^5PunkBuster Client: 0 Current Cvar Violations
^5PunkBuster Client: Receiving from PB Server (v1.229 w)
^5PunkBuster Client: Received New Security Information
Received signal 6, exiting...
Shutdown tty console
[/I][/B]


It says it can't find pbcl.cfg?

Is this some thing I need to fix?

---

### Post by batharoy on 2009-03-16
I used a script to get get every thing working and have had no problems.
Here's a link to the page I used.
[http://ubuntusoftware.info/games/rtcw/](http://ubuntusoftware.info/games/rtcw/)

---

### Post by manij on 2009-03-16
> **batharoy said:**
> I used a script to get get every thing working and have had no problems.
Here's a link to the page I used.
[http://ubuntusoftware.info/games/rtcw/](http://ubuntusoftware.info/games/rtcw/)

Can I use this for rtcw mp also?

this seems specific for ET?

---

### Post by batharoy on 2009-03-16
> **manij said:**
> Can I use this for rtcw mp also?

this seems specific for ET?

Your right, it is ET specific.
Sorry bout that.

You could try a Manual update method.
[http://www.evenbalance.com/index.php?page=dl-rtcw.php]("http://www.evenbalance.com/index.php?page=dl-rtcw.php")

---

### Post by manij on 2009-03-17
> **batharoy said:**
> Your right, it is ET specific.
Sorry bout that.

You could try a Manual update method.
[http://www.evenbalance.com/index.php?page=dl-rtcw.php]("http://www.evenbalance.com/index.php?page=dl-rtcw.php")

Yup,

downloaded the pbsetup.run

I run it, the GUI comes up. I add the game and point to the path in 

/usr/local/games/wolfenstein

ask it to look for updates and then I keep having the same problem!

HELP! please!

---

### Post by manij on 2009-03-17
I'm thinking about a complete uninstall and reinstallation at this point.

does it go away of I simply delete the wolfenstein folder? and delete the .wolf folder in my home page?

thanks

---

