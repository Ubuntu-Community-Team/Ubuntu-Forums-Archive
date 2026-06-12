---
title: "True Combat crashing"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by Weaseal on 2007-03-26
Hi all, I'm having trouble running True Combat.  I get the game to open and run just fine, but when I try to host a game, it crashes to the desktop, and typically my mouse is dead too.  Restarting X brings the mouse back.

I've attached the tail of the log:

------ Server Initialization ------
Server: battery
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/ecorazeni/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
7526 files in pk3 files
Sys_LoadDll(/home/ecorazeni/.etwolf/etmain/qagame.mp.i386.so)...
Sys_LoadDll(/home/ecorazeni/.etwolf/etmain/qagame.mp.i386.so) failed:
"/home/ecorazeni/.etwolf/etmain/qagame.mp.i386.so: cannot open shared object fil e: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so)...
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so) failed:
"/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so: cannot map zero-fill  pages: Cannot allocate memory"
Sys_LoadDll(qagame) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- Server Shutdown -----
---------------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on game failed
Shutdown tty console

---

### Post by hikaricore on 2007-03-26
Did you by any chance launch the game for the first time from the installer?

This usually results in the game's "user files" being owned by root, and crashes
the game when a normal user tries to read/write them.

Try this from a terminal:

```

sudo chown -R ecorazeni:ecorazeni ~/.etwolf/
sudo chmod -R 777 ~/.etwolf/

```

(Correct the user name if I got it wrong, I posted this in a hurry) :P

After you've run the commands try running the game again.

---

### Post by Weaseal on 2007-03-26
Thanks for the tip, I applied your suggestions and the problem remains.

I'm beginning to think the situation is more related to my system configuration than the game itself; I installed Nexuiz and it's giving the exact same result.  Opening the game and fiddling with menus etc works fine, but when I try to actually start a game, it crashes to desktop, mouse nonresponsive.  Any other ideas?

---

### Post by hikaricore on 2007-03-26
I hate to ask the over asked question but what kinda video hardware do you have?  Sounds like something my integrated Intel chipset used to do 80% of the time.

And have you installed the drivers for it?

---

### Post by Weaseal on 2007-03-26
It's an Nvidia Geforce 5200.  Yeah I got the nvidia driver installed.

---

