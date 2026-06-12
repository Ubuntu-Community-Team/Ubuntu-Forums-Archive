---
title: "quake4 1.4.2 Wont start"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by mblind on 2008-02-17
When I try and start quake 4 I get this error in the terminal

found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/morgan/.quake4/q4base/gamex86.so
Fatal Error: could not create destination file /home/morgan/.quake4/q4base/gamex86.so

Shutting down SDL subsystem
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: could not create destination file /home/morgan/.quake4/q4base/gamex86.so

(ALSO..)
I have looked at the Cheksums and they look fine and my computer has plenty of horsepower
Dual Core 2.2Ghz
3.5GB of RAM
Tons of free HDD space etc.
Dell latitude D830


thanks for the help

UPDATE.. Opps.. My bad.

Must type sudo ./quake4 to start..  Problem solved

---

### Post by ashmew2 on 2008-02-17
Add the [SOLVED] to your thread then , will ya ?

---

### Post by rajeev1204 on 2008-02-17
Never run the game with sudo.

This problem happens because the game doesnt have permission to write to the .quake4 folder in the home directory.

Do this step

  chown -R <username>:.quake4

Dont forget the dot before quake4 .Its a hidden folder in home.

This folder is where it writes config changes when you run the game



regards

rajeev

---

### Post by ashmew2 on 2008-02-17
whats the problem in running it with sudo ?

---

### Post by rajeev1204 on 2008-02-17
Hmm

using sudo of course gives administrative privileges to the user and if you are playing on the internet etc makes your system vulnerable .

---

### Post by mblind on 2008-02-17
Here is what happens when i try that

morgan@morgan-laptop:~$ chown -R morgan .quake4
chown: changing ownership of `.quake4/pb/pbcl.so': Operation not permitted
chown: changing ownership of `.quake4/pb/pbag.so': Operation not permitted
chown: changing ownership of `.quake4/pb/pbsv.so': Operation not permitted
chown: changing ownership of `.quake4/pb': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.tga': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Autosave_game_airdefense1.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.tga': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Autosave_game_airdefense1.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames': Operation not permitted
chown: changing ownership of `.quake4/q4base/quake4key': Operation not permitted
chown: changing ownership of `.quake4/q4base/gamex86.so': Operation not permitted
chown: changing ownership of `.quake4/q4base/config.spec': Operation not permitted
chown: changing ownership of `.quake4/q4base/Quake4Config.cfg': Operation not permitted
chown: changing ownership of `.quake4/q4base': Operation not permitted
chown: changing ownership of `.quake4': Operation not permitted

---

### Post by championboxes on 2009-09-15
> Here is what happens when i try that

morgan@morgan-laptop:~$ chown -R morgan .quake4
chown: changing ownership of `.quake4/pb/pbcl.so': Operation not permitted
chown: changing ownership of `.quake4/pb/pbag.so': Operation not permitted
chown: changing ownership of `.quake4/pb/pbsv.so': Operation not permitted
chown: changing ownership of `.quake4/pb': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint0.tga': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Autosave_game_airdefense1.txt': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Checkpoint1.tga': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames/Autosave_game_airdefense1.save': Operation not permitted
chown: changing ownership of `.quake4/q4base/savegames': Operation not permitted
chown: changing ownership of `.quake4/q4base/quake4key': Operation not permitted
chown: changing ownership of `.quake4/q4base/gamex86.so': Operation not permitted
chown: changing ownership of `.quake4/q4base/config.spec': Operation not permitted
chown: changing ownership of `.quake4/q4base/Quake4Config.cfg': Operation not permitted
chown: changing ownership of `.quake4/q4base': Operation not permitted
chown: changing ownership of `.quake4': Operation not permitted 

I know im posting in an old thread but ive been trying to get quake to run i finally did and this command ```
chown -R morgan .quake4
``` you would have to run as sudo

---

