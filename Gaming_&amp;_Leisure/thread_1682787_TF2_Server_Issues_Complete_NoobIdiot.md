---
title: "TF2 Server Issues Complete Noob/Idiot"
date: 2011-02-06
forum: Gaming &amp; Leisure
---

### Post by nitramneb on 2011-02-06
Hi all,

I have been experimenting with ubuntu for a little while, but am still a complete Noob. 
Recently I have tried to install srcds (source engine server.

I have followed the below guide (using putty) and have had an issue with the section called **Running the server processes the right way.**

[http://stevenbenner.com/2010/11/how-to-set-up-a-team-fortress-2-dedicated-server-on-ubuntu/](http://stevenbenner.com/2010/11/how-to-set-up-a-team-fortress-2-dedicated-server-on-ubuntu/)

**issue number 1**
entering ./srcds_run -game tf +map ctf_2fort will not work.

however ./orangebox/srcds_run -game tf +map ctf_2fort will although with a lot of error messages (below) I can however still pick up the server via LAN (won't turn up on the main search).

[I]Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Sun Feb  6 17:17:13 2011 from octopus05.home
tf2@ben-desktop:~$ ./orangebox/srcds_run -game tf +map ctf_2fort
Auto detecting CPU
Using default binary: ./srcds_linux
Server will auto-restart if there is a crash.
Using breakpad minidump system
Using breakpad crash handler

Console initialized.
Game.dll loaded for "Team Fortress"
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Installing breakpad exception handler for appid(440)/version(4426)
Particles: Missing 'particles/error.pcf'
maxplayers set to 24
Unknown command "r_decal_cullsize"
Unknown command "startupmenu"
Network: IP 192.168.1.65, mode MP, dedicated Yes, ports 27015 SV / 27005 CL
ConVarRef room_type doesn't point to an existing ConVar
Executing dedicated server config file
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient.dll. Continuing with current version anyway.
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Failed to load Steam ServiceServiceStart: failed to start--------------------------------------------------------
sv_pure set to 1.
Note: Changes to sv_pure take effect when the next map is loaded.
--------------------------------------------------------
exec: couldn't exec ctf_2fort.cfg
Connection to Steam servers successful.
   VAC secure mode is activated.[/I]

**issue  number 2**
My other issue (may be more in this forums expertise)is i am advised to set up a script.

by entering.
sudo nano /etc/init.d/srcds

and then
/etc/init.d/srcds start

However I always get the error message

tf2@ben-desktop:~$ /etc/init.d/srcds start
-bash: /etc/init.d/srcds: Permission denied

In the GUI in init.d the file looks different to the other files (maybe I have to specify a file extension?)

I am completely lost, and have spent ages trying to get this working. Sorry if I seem a bit rambling but I am trying to give as much info as possible.
Any help would be greatly appreciated.
Thanks

---

### Post by Perfect Storm on 2011-02-06
[quote=issue 2]tf2@ben-desktop:~$ /etc/init.d/srcds start[/quote]
run it with sudo infront.

---

### Post by nitramneb on 2011-02-06
Thanks for the quick reply. I tried adding sudo before and got


tf2@ben-desktop:~$ sudo /etc/init.d/srcds start
[sudo] password for tf2:
sudo: /etc/init.d/srcds: command not found
tf2@ben-desktop:~$

Is it defiantly not an issue with the srcds file which in properties identifies it's self as a plain text document?

Maybe I need to change the permission of the file so it is executable as a program?

---

### Post by nitramneb on 2011-02-06
Solved it I need to make the file executable.

sudo chmod +x

---

