---
title: "ut-goty error"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by ELD on 2006-07-16
Hi all after using the loki installer for ut-goty (unreal tournement game of the year addition) i get these errors when trying to play:

> 
liam@ubuntu:~/ut-goty$ ./ut
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down


Help please?

---

### Post by ELD on 2006-07-19
Bump, can anyone help me get it working?

Thanks.

---

### Post by vem0m on 2006-07-19
try installing the newest patch if u haven't already

---

### Post by ELD on 2006-07-19
Any ideas where i might get that for linux?

---

### Post by vem0m on 2006-07-19
[http://liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.goty.run](http://liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.goty.run) download that file then where ever u d/led it to open terminal and goto that directory and type "chmod +x unreal.tournament_436-multilanguage.goty.run" then type "./unreal.tournament_436-multilanguage.goty.run" and it should start the updater enjoy!

---

### Post by ELD on 2006-07-19
I got this error dude:

> 
liam@ubuntu:~/Desktop$ ./unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................
/home/liam/.setup5735: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


What did i miss for gtk?

---

### Post by vem0m on 2006-07-19
try typing into terminal:
```
sudo apt-get install libgtk1.2 libgtk1.2-common libgtk1.2-dev
```
then try the install of the patch again hope this works :)

---

### Post by ELD on 2006-07-19
That sorted it out, nice one :)

---

### Post by vem0m on 2006-07-19
great to hear :) enjoy the game :)

---

### Post by Fsngruv on 2006-11-15
I followed your advice on this and got GOTY working, and well, until I tried to change to Linux-686 and install the GLX-Composite deal on dapper then everytime I would start Unreal it would open, but as soon as I attempted to start a match it would crash.  I tried uninstalling and reinstalling Unreal, but now as soon as I start I get this message

 sh unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................

Gdk-WARNING **: locale not supported by C library
loki_setup: Can't create /home/owenby/ut: File exists
loki_setup: Read failure on /media/dvdrecorder/./Help/UnrealTournamentSetupLogo.bmp


If you've got any ideas let me know, i'm stuck and this is probably my favorite game of all time thanks...

---

