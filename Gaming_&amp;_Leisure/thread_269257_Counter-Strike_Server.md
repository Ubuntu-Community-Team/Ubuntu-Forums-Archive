---
title: "Counter-Strike Server"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by compLexity on 2006-10-01
For some reason my server isn't connecting to the steam servers. I already forwarded port 27015. Does Ubuntu use some sort of firewall or program that could be blocking hlds from running?

Here is what the terminal looks like:

```
jlan@jlan-desktop:~$ cd hlds_l
jlan@jlan-desktop:~/hlds_l$ ./hlds_run -console -game czero +map de_dust2_cz +maxplayers 20 -autoupdate -pingboost 1
Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Condition Zero Base Content' version 16

Checking/Installing 'Counter-Strike Base Content' version 17

Checking/Installing 'Linux Server Engine' version 35

Checking/Installing 'Half-Life Base Content' version 8

HLDS installation up to date

Console initialized.
scandir failed:/home/jlan/hlds_l/./cstrike/SAVE
scandir failed:/home/jlan/hlds_l/./valve/SAVE
scandir failed:/home/jlan/hlds_l/./platform/SAVE
Protocol version 47
Exe version 1.0.0.2/Stdio (czero)
Exe build: 20:06:55 Mar  7 2006 (3421)
STEAM Auth Server
couldn't exec language.cfg
Server IP address 127.0.1.1:27015

   Metamod version 1.19  Copyright (c) 2001-2006 Will Day <willday@metamod.org>
   Metamod comes with ABSOLUTELY NO WARRANTY; for details type `meta gpl'.
   This is free software, and you are welcome to redistribute it
   under certain conditions; type `meta gpl' for details.


   AMX Mod X version 1.76a Copyright (c) 2004-2006 AMX Mod X Development Team
   AMX Mod X comes with ABSOLUTELY NO WARRANTY; for details type `amxx gpl'.
   This is free software and you are welcome to redistribute it under
   certain conditions; type 'amxx gpl' for details.

czero
scandir failed:/home/jlan/hlds_l/./cstrike/SAVE
scandir failed:/home/jlan/hlds_l/./valve/SAVE
scandir failed:/home/jlan/hlds_l/./platform/SAVE
scandir failed:/home/jlan/hlds_l/cstrike/SAVE
L 10/02/2006 - 13:19:14: -------- Mapchange to de_dust2_cz --------
Navigation map loaded.
[AMXX] Loaded 1 admin from file

Executing AMX Mod X Configuration File
Scrolling message displaying frequency: 10:00 minutes
couldn't exec listip.cfg
couldn't exec banned.cfg
Adding master server 68.142.72.250:27010
Adding master server 69.28.151.162:27010
Could not establish connection to Steam servers.
```

---

### Post by deanhopkins on 2006-10-01
Hey mate. If its only started recently, I would try again later.

The steam servers are VERY up and down today, see: [http://enemydown.co.uk/forumreplies.php?id=79024](http://enemydown.co.uk/forumreplies.php?id=79024)

The VAC servers have also been playing up over the past few days, it may be a steam problem.

---

### Post by compLexity on 2006-10-01
But i also have another computer with Windows XP and i have a Condition Zero server running fine on that computer.

How come it can connect fine with windows XP but not with Ubuntu?

---

### Post by buffy^ on 2007-01-22
you havent set the IP address +IP 192.168.0.14 etc. then you need to enable the port forwarding.

---

### Post by Branti on 2007-03-04
+IP 192.168.0.XXX   +hostport 27015   
XXX= i don't know you last ip.. but you must give this and portforward ip and port TCP UDP on you router!

---

