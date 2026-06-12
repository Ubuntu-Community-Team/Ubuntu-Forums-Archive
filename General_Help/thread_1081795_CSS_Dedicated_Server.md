---
title: "CS:S Dedicated Server"
date: 2009-02-26
forum: General Help
---

### Post by xovox on 2009-02-26
So as the title says I'm trying to run a dedicated counter strike source server.  I get everything going, download the files and get it all updated, but when I try to start the server I get some errors.  Here they are:

**Console**

[I]./srcds_run -console -game cstrike -port 27015 +ip xxx.xxx.xxx.xxx +map cs_office +maxplayers 8 -debug
Auto detecting CPU
Using default binary.
Enabling debug mode
Server will auto-restart if there is a crash.

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
Bus error (core dumped)
Cannot access memory at address 0xb7fee658
Cannot access memory at address 0xbfedc51c
/home/loc/srcds_l/debug.cmds:3: Error in sourced command file:
Cannot access memory at address 0xb7fee658
email debug.log to [email]linux@valvesoftware.com[/email]
Thu Feb 26 21:21:10 CST 2009: Server restart in 10 seconds
Thu Feb 26 21:21:13 CST 2009: Server Quit[/I]

**This is the error log file**

[I]----------------------------------------------
CRASH: Thu Feb 26 20:59:20 CST 2009
Start Line: ./srcds_i486 -console -game cstrike -port 27015 +ip xxx.xxx.xxx.xxx +map cs_office +maxplayers 8 -debug
#0  0xb7f7c58f in ?? ()
No symbol table info available.
End of Source crash report
----------------------------------------------[/I]

Naturally, I can read and I see the "Cannot access memory..." lines... my problem is I've done a memtest and it checked out fine... so I really dont know whats wrong with it.  Does anyone have any ideas?  ANY help would be really appreciated.

I'm not beyond a simple solution, even the smallest idea could help... I'm new to linux so its very possible I just didnt set something up or misconfigured something.

Thanks for your time!

---

### Post by justleen on 2009-02-27
perhaps one of the files is damaged/bugged? Dunno.. 

I had success with this: [http://www.cstrike-planet.com/tutorial/1-Linux-Install-CS-Source/5](http://www.cstrike-planet.com/tutorial/1-Linux-Install-CS-Source/5)

---

