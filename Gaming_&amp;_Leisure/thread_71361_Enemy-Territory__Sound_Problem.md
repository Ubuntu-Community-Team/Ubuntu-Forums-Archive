---
title: "Enemy-Territory  Sound Problem"
date: 2005-10-03
forum: Gaming &amp; Leisure
---

### Post by daejavu on 2005-10-03
i know that there are alot of threads on it already but none worked for me and i wanted to give my own output from the console...
game works like a charm ... no graphic or fps issues .. just a sound problem .. no sound at all .. not even music of the game !  heres the output ..

===============================================
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/shoshe/.etwolf/etmain/vlasterx_ss_skins_v1-0.pk3 (125 files)
/home/shoshe/.etwolf/etmain/temple_final.pk3 (57 files)
/home/shoshe/.etwolf/etmain/pak90.pk3 (1 files)
/home/shoshe/.etwolf/etmain/pak7322.pk3 (2 files)
/home/shoshe/.etwolf/etmain/mlb_daybreak.pk3 (158 files)
/home/shoshe/.etwolf/etmain/gameradius.pk3 (2 files)
/home/shoshe/.etwolf/etmain/dubrovnik_final_1104.pk3 (186 files)
/home/shoshe/.etwolf/etmain/CNH-09031103.pk3 (8 files)
/home/shoshe/.etwolf/etmain/7map7.pk3 (1 files)
/home/shoshe/.etwolf/etmain/3map3.pk3 (1 files)
/home/shoshe/.etwolf/etmain/10map10.pk3 (1 files)
/home/shoshe/.etwolf/etmain
/home/shoshe/enemy-territory/etmain/pak2.pk3 (22 files)
/home/shoshe/enemy-territory/etmain/pak1.pk3 (10 files)
/home/shoshe/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/shoshe/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/shoshe/enemy-territory/etmain

----------------------
4305 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/shoshe/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------


------- sound initialization -------
/dev/adsp: Input/output error
Could not mmap /dev/adsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/shoshe/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/shoshe/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/shoshe/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/shoshe/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa5f51f40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: Osiris
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.202 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
=================================================

i know its ne heck of an output but nothing is like working for me .. 
need some help with it ! 
thanks in advance 
(btw im using Ubuntu Hoary)

---

### Post by Zimmer on 2005-10-03
This works for me, and I have SIS onboard sound in a Biostarbox. You do not mention which soundcard you have...
I found the answer was the way the ESD worked...
so in a terminal session try
[killall -9 esd]
and then
[sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss']

....I do not use the killall statement any more as I have re configed ESD as follows:-
how to re configure esd to release to other applications, change the esd.conf file (make a backup first..)
located at /etc/esound to read thus:-

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

..******....but I still have to type  this in Terminal to get it to produce sound....*******

[sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss']
please note the single and double quotes !!! to get sudo to interpret the command correctly.
or try
[esddsp --mmap et]
  (This did nothing for me..but if you still have problems, like me, you will try anything)

PLAYING HINTS
SEE
[http://velocity.lunarpages.com/basicskills.html](http://velocity.lunarpages.com/basicskills.html)
As for PUNKBUSTER, I have it DISABLED as it was not right a month or so ago, and screwed the game , I may try it again soon.
Good Luck
Zimm

---

