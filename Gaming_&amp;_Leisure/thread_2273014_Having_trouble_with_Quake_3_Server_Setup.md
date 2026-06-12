---
title: "Having trouble with Quake 3 Server Setup"
date: 2015-04-10
forum: Gaming &amp; Leisure
---

### Post by manjon-la on 2015-04-10
Hello,

I am still fairly new to linux and i have been having some trouble with getting a Quake 3 server started. As soon as I execute the shellscript to start the server, the terminal returns with this:

```
quake3@bd7iquejie:~$ ./start-cpm-server.sh
./start-cpm-server.sh: line 1: //: Is a directory
./start-cpm-server.sh: line 2: //: Is a directory
./start-cpm-server.sh: line 3: $'\r': command not found
./start-cpm-server.sh: line 4: $'\r': command not found
./start-cpm-server.sh: line 9: $'\r': command not found
 : 279605.196.201a-cpm
./start-cpm-server.sh: line 11: $'\r': command not found
./start-cpm-server.sh: line 13: $'\r': command not found
./start-cpm-server.sh: line 14: $'\r': command not found
./start-cpm-server.sh: line 15: //: Is a directory



```

Below is the shellscript that I am using

```
// ********************** START OF SHELLSCRIPT TO START THE SERVER **********************
// FILENAME : start-cpm-server.sh




#!/bin/sh
ip="xx.xx.xx.xx"
port="27960"
name="q3a-cpm"


echo running server $name on $ip : $port


screen -A -m -d -S $name /usr/local/games/ioquake3/ioq3ded.i386 +set sv_punkbuster 1 +set fs_basepath /usr/local/games/ioquake3/ +set fs_game cpma +set dedicated 1 +set com_hunkMegs 32 +set net_ip $ip +set net_port $port +set g_log $name.log +exec q3ded-cpm.cfg




// ********************** END OF SHELLSCRIPT TO START THE SERVER **********************



```

---

