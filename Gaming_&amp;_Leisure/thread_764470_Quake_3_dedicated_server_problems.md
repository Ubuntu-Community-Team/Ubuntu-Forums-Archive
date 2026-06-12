---
title: "Quake 3 dedicated server problems"
date: 2008-04-23
forum: Gaming &amp; Leisure
---

### Post by dlovley on 2008-04-23
I'm try to run a dedicated server using scq3a but the I get the following error when I run the "go" file in console. Any suggestions would be great. I noticed that it thinks I'm running in restricted demo mode when I have a valid full install. Plz give me linux newbi instructions.



cd: 14: can't cd to /usr/local/q3a
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/darrel/.q3a/scq3a
/usr/local/q3a/scq3a
./q3ded/scq3a
/home/darrel/.q3a/baseq3
/usr/local/q3a/baseq3
./q3ded/baseq3

----------------------
0 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/darrel/.q3a/demota
/usr/local/q3a/demota
./q3ded/demota

----------------------
0 files in pk3 files
Sys_Error: Couldn't load default.cfg

---

### Post by joobuntjoo on 2008-04-24
Hi,

I'm guessing the key is in the first error. "can't cd to /usr/local/q3a". It looks like the q3 dedicated binary can't find the pak files. Don't assume it will know.

What you can do is start q3ded and point it to wherever the install is. So ...

./q3ded +set dedicated 1 +set fs_basepath /home/whereisq3/q3a +set fs_homepath /home/whereisq3/q3a +exec server.cfg

or similar (while since I've done it). Make sure your server.cfg has a valid start map as well.

---

### Post by dlovley on 2008-04-24
> **joobuntjoo said:**
> Hi,

I'm guessing the key is in the first error. "can't cd to /usr/local/q3a". It looks like the q3 dedicated binary can't find the pak files. Don't assume it will know.

What you can do is start q3ded and point it to wherever the install is. So ...

./q3ded +set dedicated 1 +set fs_basepath /home/whereisq3/q3a +set fs_homepath /home/whereisq3/q3a +exec server.cfg

or similar (while since I've done it). Make sure your server.cfg has a valid start map as well.

 That was a big help, I think I'm on my to getting this running thank you.

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/darrel/.q3a/scq3a
/usr/local/games/quake3/scq3a
./q3ded/scq3a
/home/darrel/.q3a/baseq3
/usr/local/games/quake3/baseq3/zzz_opc_x_hairs.pk3 (12 files)
/usr/local/games/quake3/baseq3/z-console.pk3 (6 files)
/usr/local/games/quake3/baseq3/ts_q3dm13.pk3 (9 files)
/usr/local/games/quake3/baseq3/tourney3remix.pk3 (17 files)
/usr/local/games/quake3/baseq3/spaced-out.pk3 (30 files)
/usr/local/games/quake3/baseq3/quarea51.pk3 (61 files)
/usr/local/games/quake3/baseq3/q3megamix.pk3 (23 files)
/usr/local/games/quake3/baseq3/q3dm9remix.pk3 (37 files)
/usr/local/games/quake3/baseq3/q3dm7remix.pk3 (31 files)
/usr/local/games/quake3/baseq3/q3dm6remix.pk3 (15 files)
/usr/local/games/quake3/baseq3/q3dm4remix.pk3 (21 files)
/usr/local/games/quake3/baseq3/q3dm3remix.pk3 (17 files)
/usr/local/games/quake3/baseq3/q3dm2remix.pk3 (14 files)
/usr/local/games/quake3/baseq3/q3dm13remix.pk3 (15 files)
/usr/local/games/quake3/baseq3/q3-a51.pk3 (1157 files)
/usr/local/games/quake3/baseq3/platform6.pk3 (62 files)
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3/nquit5.pk3 (7 files)
/usr/local/games/quake3/baseq3/neonx-skin-pak.pk3 (176 files)
/usr/local/games/quake3/baseq3/nedmaj.pk3 (16 files)
/usr/local/games/quake3/baseq3/morpheusx.pk3 (42 files)
/usr/local/games/quake3/baseq3/map-durdm1.pk3 (35 files)
/usr/local/games/quake3/baseq3/lsdm17_map.pk3 (3 files)
/usr/local/games/quake3/baseq3/laststand.pk3 (10 files)
/usr/local/games/quake3/baseq3/hrodm01.pk3 (59 files)
/usr/local/games/quake3/baseq3/dc-mappack.pk3 (451 files)
/usr/local/games/quake3/baseq3/chronic.pk3 (260 files)
/usr/local/games/quake3/baseq3/Bal3dm2.pk3 (33 files)
/usr/local/games/quake3/baseq3/a51models-1.pk3 (336 files)
/usr/local/games/quake3/baseq3/17t6remix.pk3 (22 files)
/usr/local/games/quake3/baseq3/17t6ctf.pk3 (24 files)
/usr/local/games/quake3/baseq3/17Remix.pk3 (7 files)
/usr/local/games/quake3/baseq3/15+1remix.pk3 (17 files)
/usr/local/games/quake3/baseq3
./q3ded/baseq3

----------------------
7098 files in pk3 files
execing default.cfg
execing q3config.cfg
com_zoneMegs will be changed upon restarting.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: Rig
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing server.cfg
execing scq3a.cfg
execing maprotation.cfg
------ Server Initialization ------
Server: q3ctf1
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/darrel/.q3a/scq3a
/usr/local/games/quake3/scq3a
./q3ded/scq3a
/home/darrel/.q3a/baseq3
/usr/local/games/quake3/baseq3/zzz_opc_x_hairs.pk3 (12 files)
/usr/local/games/quake3/baseq3/z-console.pk3 (6 files)
/usr/local/games/quake3/baseq3/ts_q3dm13.pk3 (9 files)
/usr/local/games/quake3/baseq3/tourney3remix.pk3 (17 files)
/usr/local/games/quake3/baseq3/spaced-out.pk3 (30 files)
/usr/local/games/quake3/baseq3/quarea51.pk3 (61 files)
/usr/local/games/quake3/baseq3/q3megamix.pk3 (23 files)
/usr/local/games/quake3/baseq3/q3dm9remix.pk3 (37 files)
/usr/local/games/quake3/baseq3/q3dm7remix.pk3 (31 files)
/usr/local/games/quake3/baseq3/q3dm6remix.pk3 (15 files)
/usr/local/games/quake3/baseq3/q3dm4remix.pk3 (21 files)
/usr/local/games/quake3/baseq3/q3dm3remix.pk3 (17 files)
/usr/local/games/quake3/baseq3/q3dm2remix.pk3 (14 files)
/usr/local/games/quake3/baseq3/q3dm13remix.pk3 (15 files)
/usr/local/games/quake3/baseq3/q3-a51.pk3 (1157 files)
/usr/local/games/quake3/baseq3/platform6.pk3 (62 files)
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3/nquit5.pk3 (7 files)
/usr/local/games/quake3/baseq3/neonx-skin-pak.pk3 (176 files)
/usr/local/games/quake3/baseq3/nedmaj.pk3 (16 files)
/usr/local/games/quake3/baseq3/morpheusx.pk3 (42 files)
/usr/local/games/quake3/baseq3/map-durdm1.pk3 (35 files)
/usr/local/games/quake3/baseq3/lsdm17_map.pk3 (3 files)
/usr/local/games/quake3/baseq3/laststand.pk3 (10 files)
/usr/local/games/quake3/baseq3/hrodm01.pk3 (59 files)
/usr/local/games/quake3/baseq3/dc-mappack.pk3 (451 files)
/usr/local/games/quake3/baseq3/chronic.pk3 (260 files)
/usr/local/games/quake3/baseq3/Bal3dm2.pk3 (33 files)
/usr/local/games/quake3/baseq3/a51models-1.pk3 (336 files)
/usr/local/games/quake3/baseq3/17t6remix.pk3 (22 files)
/usr/local/games/quake3/baseq3/17t6ctf.pk3 (24 files)
/usr/local/games/quake3/baseq3/17Remix.pk3 (7 files)
/usr/local/games/quake3/baseq3/15+1remix.pk3 (17 files)
/usr/local/games/quake3/baseq3
./q3ded/baseq3

----------------------
14196 files in pk3 files
Loading dll file qagame.
Sys_LoadDll(/usr/local/games/quake3/scq3a/qagamei386.so)... 
Sys_LoadDll(/usr/local/games/quake3/scq3a/qagamei386.so): succeeded ...
Sys_LoadDll(qagame) found **vmMain** at  0xb2544be0  
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: baseq3
gamedate: Dec 19 2001
------------------------------------------------------------
InitGame: \g_gametype\1\sv_maxclients\20\sv_hostname\PUT YOUR HOSTNAME HERE\sv_maxRate\10000\sv_minPing\0\sv_maxPing\0\sv_floodProtect\1\dmflags\0\fraglimit\30\timelimit\20\g_maxGameClients\0\capturelimit\8\sv_punkbuster\0\version\Q3 1.32b linux-i386 Nov 14 2002\protocol\68\mapname\q3ctf1\sv_privateClients\0\sv_allowDownload\0\g_motd\PUT YOUR MOTD HERE\Administrator\HANDLE OF ADMIN\Email\EMAIL OF ADMIN\URL\WEBSITE\Location\BRIEF LOCATION INFO\CPU\400MHZ P2\Clan\CLAN ASSOCIATION\Connection\T1\g_obeliskRespawnDelay\10\sc_voteflags\511\gamename\baseq3\g_needpass\0\sc_version\1.6
Gametype changed, clearing session data.
Warmup:
15 items registered
2 teams with 4 entities
15 items registered
-----------------------------------
-----------------------------------
Resolving master.quake3arena.com
master.quake3arena.com resolved to 192.246.40.56:27950
Sending heartbeat to master.quake3arena.com
Resolving master0.gamespy.com
master0.gamespy.com resolved to 207.38.11.34:27950
Sending heartbeat to master0.gamespy.com
Resolving master0.scta.reqoning.com
Couldn't resolve address: master0.scta.reqoning.com
PunkBuster Server: Preparing to Disable PB Server... (/home/darrel/.q3a/pb/)

---

