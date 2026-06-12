---
title: "Counterstrike source dedicated server"
date: 2008-12-21
forum: General Help
---

### Post by dragon9114 on 2008-12-21
Hi,

i want to set up a dedicated counterstrike source server. everything installed wel but when i try to start the program for the dedicated server is get this error .

> Auto detecting CPU
Using AMD Optimised binary.
Enabling debug mode
Server will auto-restart if there is a crash.
Illegal instruction (core dumped)
Cannot access memory at address 0xb7f43658
/home/dragon/hlds/debug.cmds:3: Error in sourced command file:
Cannot access memory at address 0xb7f43658
email debug.log to [email]linux@valvesoftware.com[/email]
zo dec 21 16:15:45 CET 2008: Server restart in 10 seconds

does any one know what this error means ?

i am using ubuntu server 8.04.

here is the log file

> CRASH: zo dec 21 22:04:46 CET 2008
Start Line: ./srcds_amd -game cstrike -autoupdate +maxplayers 20 +map de_dust2 -debug
#0  0xb7dab913 in ?? ()
#1  0x00000000 in ?? ()
No symbol table info available.
End of Source crash report


---

### Post by dragon9114 on 2008-12-24
doesn't any one have an idea of what could be wrong whit the system ?:(:confused:

---

