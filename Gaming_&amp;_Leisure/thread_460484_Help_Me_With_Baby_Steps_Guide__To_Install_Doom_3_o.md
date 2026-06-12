---
title: "Help Me With Baby Steps Guide:  To Install Doom 3 on Unbuntu?"
date: 2007-05-31
forum: Gaming &amp; Leisure
---

### Post by jfrancis on 2007-05-31
Good evening all,

I am a relatively inexperienced Linux user.  I kicked my Windows habit a couple months ago and learn as I go.

I really want to get my copy of Doom 3 up and running on my system and I have read a couple threads and a wiki guide on doing this, but they confused me :(

I would love guidance from anyone with a little spare time.  I'm talking baby steps here!  

So - I have the Doom 3 CD's in front of me.  I have Feisty Ubuntu running - the i386 version with a nvidia 7600 GS graphics card.  So, what do I do first?

:D

---

### Post by noerrorsfound on 2007-06-01
There are two installers for Doom 3 but you don't need them both. One is the official installer from id Software (the creators of Doom 3) and the other is an unofficial one from a site called [Loki Installers For Linux Gamers]("http://liflg.org/"). I recommend the unofficial one because it will copy necessary files from the CDROMs instead of making you do it manually.
1. Unofficial installer (try this first): [http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run](http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run)
2. Official installer (not as simple): [ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run](ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run)

You should be able to just double-click on the unofficial installer and choose Run. The installation process should be easy but post if you need help.

---

### Post by lordhebe on 2007-06-01
Lol if you want it in even more simple terms for the liflg installer:

1: Download the newest installer off [http://www.liflg.org/]("http://www.liflg.org/")
2: Right click it and click on properties, click on the permissions tab, and tick allow executing file as a program.
3: Double click on it or if you want to installer it to a place that is read-only access (Like /ect/local/games) then run it in a terminal by typing in (if the file was on the desktop ```
sudo sh /home/name/Desktop/doom3_1.3.1.1304-multilanguage.run
```
4: The installer will then run, will ask you to put in the first cd! Do as it says, and the installer will commence, it will ask you for a second cd later.
5: If you ran it as root (aka by runing it in a terminal with sudo) do NOT click start when the installer finishes, as it will mess up permissions. 

Hope this is useful.

---

### Post by jfrancis on 2007-06-02
Hey I want to thank you both very much!! :D  I appreciate your guidance.  

Now for some gaming,,,

---

### Post by treblesix on 2007-06-28
I will give these a try :)

---

### Post by weblordpepe on 2007-06-28
Yeah basically you use one of those installers to install the Linux binaries & all the Linuxy files etc.

Doom3's stuff gets installed to /usr/local/games/doom3 or something like that. Anyway, you gotta put the contents of your Doom3 folder into there. I threw it all in there.

For a while I could run both the doom3.exe under Wine, or the native Doom3 binary. Much better native.

---

### Post by treblesix on 2007-06-28
Just installed Doom + the expansion pack with that installer. Great stuff. Only thing I can comment negatively on, is that it doesn't create an Icon.

---

### Post by weblordpepe on 2007-06-29
Oh yeah. It'd be nice if there was a .deb file instead of this text based installer thing. 
Doom3/Quake4 are definately the killer games for the Linux desktop. Hopefully now that EA are making games for the mac, they'll better run under WINE. 
Quake Wars will be good too once the Linux binary comes out.

---

### Post by dfreer on 2007-06-29
> **treblesix said:**
> Just installed Doom + the expansion pack with that installer. Great stuff. Only thing I can comment negatively on, is that it doesn't create an Icon.

This is a known bug, the included icon file is corrupted somehow.
[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)
Icon itself (PNG):
[http://zerowing.idsoftware.com/linux/doom3.png](http://zerowing.idsoftware.com/linux/doom3.png)

I believe it goes into the /usr/local/games/doom3/ directory.

> **weblordpepe said:**
> Oh yeah. It'd be nice if there was a .deb file instead of this text based installer thing. 
Doom3/Quake4 are definately the killer games for the Linux desktop. Hopefully now that EA are making games for the mac, they'll better run under WINE. 
Quake Wars will be good too once the Linux binary comes out.

Hmmm. Shouldn't be too hard to make a bash shell script to handle the install, and once that is done it could be packaged in a .deb... I'll look into it but no promises, I've got a zillion project's I'm already working on lol

---

### Post by weblordpepe on 2007-06-29
Holy cow I wasnt asking you to make it :) But thats amazing. Thanks for offering. The way I see it, I just want to see the linux community being more unified.
Instead of making a new OS every day, just working on a few good ones & pushing them hard. You see when you get the 'linux version' of software on the web there's sometimes a zillion different package formats.

It'd be nice if it was just a .deb, .rpm, and a .tar.gz.

---

### Post by kineticenrage on 2011-01-28
I know this is an old thread but i have a doom3 related question. i have doom 3 on my hard drive, i downloaded it. when i try to run the .exe file using wine this is what happens. 
DOOM 1.3.1302 win-x86 May 12 2005 10:40:52
800 MHz AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
1760 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0 eth0 - /
Found interface: wlan0 wlan0 - 
Sys_InitNetworking: adding loopback interface
doom using MMX & SSE & SSE2 & SSE3 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Current search path:
Z:\home\dustin\.cache\.fr-An51aT\Doom 3/base
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg

is there anyway i can fix this problem? thanks in advance.

---

### Post by suppo84 on 2011-01-28
Doom series was one of my favourites, it is very nice that doom 3 work native in linux. Sorry for my bad english skills...

---

### Post by sakuramboo on 2011-01-28
> **kineticenrage said:**
> I know this is an old thread but i have a doom3 related question. i have doom 3 on my hard drive, i downloaded it. when i try to run the .exe file using wine this is what happens. 
DOOM 1.3.1302 win-x86 May 12 2005 10:40:52
800 MHz AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
1760 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0 eth0 - /
Found interface: wlan0 wlan0 - 
Sys_InitNetworking: adding loopback interface
doom using MMX & SSE & SSE2 & SSE3 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Current search path:
Z:\home\dustin\.cache\.fr-An51aT\Doom 3/base
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg

is there anyway i can fix this problem? thanks in advance.

Use the native client.

---

### Post by CharlesA on 2011-01-28
Old thread is old.

Closed.

---

