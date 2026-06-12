---
title: "Enemy-territory Radar map Crash?"
date: 2005-10-20
forum: Gaming &amp; Leisure
---

### Post by nitricacid on 2005-10-20
Ok, I installed Wolfenstien Enemy-territory on ubuntu and everything ran fine till i needed to delete the files where ET installed to so i could change somethings around.

I re-installed ET sat up everything as I had done be for but only this time when ever the rotation gets to the Wersburge Radar map the server crashes/
It only ever crashes on this map in the rotation. The other five maps play perfectly.


Here is the entire start up module:
```
sudo /usr/local/enemy-territory/enemy-territory_2.55/etded ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/nitricacid/.etwolf/etmain
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak2.pk3 (22 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak1.pk3 (10 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak0.pk3 (3725 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/mp_bin.pk3 (6 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
^3PunkBuster Server: pb_sv_SsNext = 730008 (0 to 999999)
^3PunkBuster Server: pb_sv_LogNext = 9 (1 to 999999)
^3PunkBuster Server: 0 Power Players loaded from /home/nitricacid/.etwolf/pb/pbpower.dat
^3PunkBuster Server: 0 PB Rcon Filters loaded from /home/nitricacid/.etwolf/pb/pbrcon.dat
^3PunkBuster Server: 0 Map lines loaded from /home/nitricacid/.etwolf/pb/pbsvmaps.cfg
^3PunkBuster Server: PunkBuster Server (v1.160 | A1360 C1.202) Enabled
usage: set <variable> <value> [unsafe]
execing server.cfg
usage: set <variable> <value> [unsafe]
execing campaigncycle.cfg
g_gametype will be changed upon restarting.
------ Server Initialization ------
Server: fueldump
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/nitricacid/.etwolf/etmain
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak2.pk3 (22 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak1.pk3 (10 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak0.pk3 (3725 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/mp_bin.pk3 (6 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain

----------------------
7526 files in pk3 files
Sys_LoadDll(/home/nitricacid/.etwolf/etmain/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xafcf1890
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: shrubet
gamedate: Jan 11 2004
ResetXP: 0 were saved.
ResetXP: 0 were saved.
------------------------------------------------------------
InitGame: \shrubbot\0\modversion\1.2-TEST13\g_maxlivesRespawnPenalty\0\voteFlags\0\g_balancedteams\0\g_maxGameClients\0\g_bluelimbotime\30000\g_redlimbotime\30000\gamename\shrubet\g_medicchargetime\10000\g_engineerchargetime\10000\g_ltchargetime\10000\g_soldierchargetime\10000\g_covertopschargetime\10000\g_heavyWeaponRestriction\100\g_gametype\2\g_antilag\1\g_voteFlags\0\g_alliedmaxlives\0\g_axismaxlives\0\g_minGameClients\0\g_needpass\0\g_maxlives\0\g_friendlyFire\1\sv_allowAnonymous\0\sv_floodProtect\1\sv_maxPing\400\sv_minPing\0\sv_maxRate\25000\sv_minguidage\0\sv_maxclients\20\sv_hostname\Enemy-Territory\sv_privateClients\0\mapname\fueldump\protocol\84\timelimit\0\version\ET 2.60 linux-i386 Mar 10 2005\sv_punkbuster\1
Start of warmup.
SBLoadConfig: Loaded 2 admins
SBLoadConfig: Loaded 6 level templates
SBLoadConfig: Loaded 0 bans
Gametype changed, clearing session data.
Enable spawning!
Disable spawning!
0 teams with 0 entities
-----------------------------------
^3PunkBuster Server: 0 Aliases Written to /home/nitricacid/.etwolf/pb/pbalias.dat
^3PunkBuster Server: 0 Stat Records Written to /home/nitricacid/.etwolf/pb/pbstat.dat
Setting MOTD...
Skill 0: 20 50 90 140 | 0
Skill 1: 20 50 90 140 | 0
Skill 2: 20 50 90 140 | 0
Skill 3: 20 50 90 140 | 0
Skill 4: 20 50 90 140 | 0
Skill 5: 20 50 90 140 | 0
Skill 6: 20 50 90 140 | 0
broadcast: print "Server: timelimit changed to 30\n"
broadcast: print "Server: g_balancedteams changed to 1\n"
^1Warning: setstate called and no entities found
^1Warning: setstate called and no entities found
Setting Allied autospawn to Allied Entrance Spawn
Setting Axis autospawn to Tunnel Store Room
-----------------------------------
execing campaigncycle.cfg
==== ShutdownGame ====
ShutdownGame:
------------------------------------------------------------
SBReset: Cleared 2 admins from memory
SBReset: Cleared 6 level templates from memory
SBReset: Cleared 0 bans from memory
------ Server Initialization ------
Server: fueldump
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/nitricacid/.etwolf/etmain
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak2.pk3 (22 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak1.pk3 (10 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak0.pk3 (3725 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/mp_bin.pk3 (6 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain

----------------------
11289 files in pk3 files
Sys_LoadDll(/home/nitricacid/.etwolf/etmain/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xafcf1890
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: shrubet
gamedate: Jan 11 2004
ResetXP: 0 were saved.
ResetXP: 0 were saved.
------------------------------------------------------------
InitGame: \shrubbot\enabled\modversion\1.2-TEST13\g_maxlivesRespawnPenalty\0\voteFlags\122367\g_balancedteams\1\g_maxGameClients\0\g_bluelimbotime\15000\g_redlimbotime\15000\gamename\shrubet\g_medicchargetime\10000\g_engineerchargetime\10000\g_ltchargetime\10000\g_soldierchargetime\10000\g_covertopschargetime\10000\g_heavyWeaponRestriction\100\g_gametype\2\g_antilag\1\g_voteFlags\0\g_alliedmaxlives\0\g_axismaxlives\0\g_minGameClients\0\g_needpass\0\g_maxlives\0\g_friendlyFire\1\sv_allowAnonymous\0\sv_floodProtect\1\sv_maxPing\400\sv_minPing\0\sv_maxRate\25000\sv_minguidage\0\sv_maxclients\20\sv_hostname\Enemy-Territory\sv_privateClients\0\mapname\fueldump\protocol\84\timelimit\30\version\ET 2.60 linux-i386 Mar 10 2005\sv_punkbuster\1
Start of warmup.
SBLoadConfig: Loaded 2 admins
SBLoadConfig: Loaded 6 level templates
SBLoadConfig: Loaded 0 bans
Enable spawning!
Disable spawning!
0 teams with 0 entities
-----------------------------------
^3PunkBuster Server: 0 Aliases Written to /home/nitricacid/.etwolf/pb/pbalias.dat
^3PunkBuster Server: 0 Stat Records Written to /home/nitricacid/.etwolf/pb/pbstat.dat
Setting MOTD...
Skill 0: 20 50 90 140 | 0
Skill 1: 20 50 90 140 | 0
Skill 2: 20 50 90 140 | 0
Skill 3: 20 50 90 140 | 0
Skill 4: 20 50 90 140 | 0
Skill 5: 20 50 90 140 | 0
Skill 6: 20 50 90 140 | 0
^1Warning: setstate called and no entities found
^1Warning: setstate called and no entities found
Setting Allied autospawn to Allied Entrance Spawn
Setting Axis autospawn to Tunnel Store Room
-----------------------------------
execing preset_high.cfg
Invalid command or cvar.  Use 'say' to display message to server.
Hitch warning: 2254 msec frame time
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27950
Sending heartbeat to etmaster.idsoftware.com
Hitch warning: 3680 msec frame time
^3PunkBuster Server: Game Version [ET 2.60 linux-i386 Mar 10 2005]
```

Here is what happens when console switches to the Radar Map:
```
==== ShutdownGame ====
ShutdownGame:
------------------------------------------------------------
SBReset: Cleared 2 admins from memory
SBReset: Cleared 6 level templates from memory
SBReset: Cleared 0 bans from memory
------ Server Initialization ------
Server: radar
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/nitricacid/.etwolf/etmain
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak2.pk3 (22 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak1.pk3 (10 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/pak0.pk3 (3725 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain/mp_bin.pk3 (6 files)
/usr/local/enemy-territory/enemy-territory_2.55/etmain

----------------------
15052 files in pk3 files
Sys_LoadDll(/home/nitricacid/.etwolf/etmain/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xafcf1890
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: shrubet
gamedate: Jan 11 2004
ResetXP: 0 were saved.
ResetXP: 0 were saved.
------------------------------------------------------------
InitGame: \shrubbot\enabled\modversion\1.2-TEST13\g_maxlivesRespawnPenalty\0\voteFlags\122367\g_balancedteams\1\g_maxGameClients\0\g_bluelimbotime\15000\g_redlimbotime\15000\gamename\shrubet\g_medicchargetime\10000\g_engineerchargetime\10000\g_ltchargetime\10000\g_soldierchargetime\10000\g_covertopschargetime\10000\g_heavyWeaponRestriction\100\g_gametype\2\g_antilag\1\g_voteFlags\0\g_alliedmaxlives\0\g_axismaxlives\0\g_minGameClients\0\g_needpass\0\g_maxlives\0\g_friendlyFire\1\sv_allowAnonymous\0\sv_floodProtect\1\sv_maxPing\400\sv_minPing\0\sv_maxRate\25000\sv_minguidage\0\sv_maxclients\20\sv_hostname\Enemy-Territory\sv_privateClients\0\mapname\radar\protocol\84\timelimit\30\version\ET 2.60 linux-i386 Mar 10 2005\sv_punkbuster\1
Start of warmup.
SBLoadConfig: Loaded 2 admins
SBLoadConfig: Loaded 6 level templates
SBLoadConfig: Loaded 0 bans
Map changed, clearing player stats.
Enable spawning!
********************
ERROR: G_Script_ScriptParse(), Error (line 2207): unknown action: set.

********************
----- Server Shutdown -----
Sending heartbeat to etmaster.idsoftware.com
==== ShutdownGame ====
ShutdownGame:
------------------------------------------------------------
SBReset: Cleared 2 admins from memory
SBReset: Cleared 6 level templates from memory
SBReset: Cleared 0 bans from memory
---------------------------
Hitch warning: 837 msec frame time
```

I am also using the latest version of shrubet for admining perposes.

---

### Post by Wang80 on 2007-03-27
The problem is not with your OS or even ET it is with Shurbet version 1.2test13 for some reason
it will not load radar, and on a few other choice maps it hangs at the end of the map or will not
load at all (like with radar)...

I recommend using ETpub (you can get it from etpub.org) it is the replacement of shrubet by a
fan of shrub. Plus tjw is kind enough to have his source for etpub as open source for others to
use.

ETpub make use of the shrubbot.cfg among other things... ETpub has only left a few choice things
out of their mod that was in shrubet... (i.e. !shake, !ftime, !glow, etc.) other than that I find it
a fun mod to use and an pretty good replacement of shrubet (although I would rather Ryan
Mannon (the creator of Shrubet) would have finished his mod, or at least released the souce for
someone else to take over!


[COLOR="Lime"]Wang[/COLOR]

---

