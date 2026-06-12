---
title: "Doom3"
date: 2005-03-27
forum: Gaming &amp; Leisure
---

### Post by Bicet on 2005-03-27
Finally i got it working under Linux, with this  little script ;)

 ```
#bin/bash
echo ----Killing ESD----
killall esd
echo ----Starting DOOM3-----
doom3 +set s_driver oss +set s_numberOfSpeakers 2 +set sys_VideoRam 128
``` 

Now I got a small problem, do you know why I cannot have the game on full screen??? 
Everytime I must edit my xorg.conf and restart X, before playing... do you have any suggestion?

p.s. I'm using fglrx...

---

### Post by sdyson on 2006-07-01
This same script works for Quake 4 as well. Thanks a lot.

---

### Post by ghoran on 2007-12-19
Perhaps you can help me.
I tried to run doom3 from the command line of a terminal.
Then I saw this and created the script and tried to run.
In both cases I get the same error.
It seems that the vid_restart command is missing.

> 
gary@gary-desktop:~$ ./run_doom3
----Killing ESD----
esd: no process killed
----Starting DOOM3-----
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.165/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/gary/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
gary@gary-desktop:~$ 
gary@gary-desktop:~$ 
gary@gary-desktop:~$ 
gary@gary-desktop:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.165/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/gary/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
gary@gary-desktop:~$

---

### Post by ghoran on 2007-12-19
Guys,
There is no real problem.
I copied the files from the cd(s) into my home directory and forgot to put them in the /usr/loca... directory.
All is well

---

### Post by ahaslam on 2007-12-19
More likely:
> Sys_Error: Couldn't load default.cfg
Did you install to the default locations? I recommend installing as user within your home dir to avoid permission problems (and keep your root partition tidy) ;)

---

### Post by ghoran on 2007-12-19
It is working fine but, there is some static through the sound card even if I run it off the script.

gary@gary-desktop:~$ cat run_doom3
#bin/bash
echo ----Killing ESD----
killall esd
echo ----Starting DOOM3-----
doom3 +set s_driver oss +set s_numberOfSpeakers 2 +set sys_VideoRam 128

gary@gary-desktop:~$

---

