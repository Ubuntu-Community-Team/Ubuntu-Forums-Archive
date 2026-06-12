---
title: "Problem with starting dedicated quake 3 arena server"
date: 2008-10-24
forum: Gaming &amp; Leisure
---

### Post by anomit on 2008-10-24
I'm trying to run a dedicated quake 3 arena server on my LAN. I have installed the point1.32b release. This is the configuration file(q3ded.cfg) I am using for the dedicated server. I pulled it off some online guide, but that didn't help me either.
```

// ********************** START OF Q3A SERVER FILE **********************
// // FILENAME : q3ded-osp.cfg
//
//
// // q3a server config
// // vq3 ffa
// // make sure the map rotation file 'maprotate-osp-ffa.cfg' exists
// // written by spirit, based on the config from holarse.net
//
//
// // --- contact and admin ---
// sets ".Admin"  "change_me"			// admin name
// sets ".email" "change_me"			// admin email
// sets ".www"   "change_me"		        // www site that offers maps rotated on the server etc
//
//
// // --- basic stuff ---
// seta rconPassword "change_me"           	// remote console admin password
seta g_gametype "0"				// gametype (0 = ffa, 1 = tourney,  2 = ffa, 3 = tdm, 4 = ctf)
//
//
seta sv_strictauth "0"
// // --- banner stuff ---
seta sv_hostname "deadbox"		        // how the server shows up in q3a game browser
// seta g_motd "change_me"		                // message of the day, shown on client connect
//
//
// // --- misc ---
// seta r_smp "0"					// whether the server has multiple CPUs
seta sv_pure "1"				// whether .pk3-files are cheat checked
//
//
// // --- clients and slots ---
// g_password "change_me"		        	// server password for clients who try to connect
// g_needpass "0"					// whether the password is enabled / needed to connect
// seta sv_maxClients "8"				// max players allowed on server, includes spectators
// seta sv_privateClients "2"			// reserved slots for players who know the private password
// seta sv_privatePassword "change_me" 		// private slot password
// seta g_syncronousClients "0"			// whether clients are allowed to record demos
// seta g_allowvote "0"				// map - map restart - kick - g_gametype
//
//
// // --- annoyances ---
// // Note that you need to turn punkbuster off on the command line when you start the server (q3ded +set sv_punkbuster 0 ...)
// // because you can't change the setting anymore once the server process has started! Removing the next line (or putting 'sv_punkbuster 0'
// // into your config file will NOT turn off punkbuster.
// pb_sv_enable					// enable punkbuster server
// pb_sv_guidrelax 7				// disable punkbuster CD-check
// seta sv_strictauth "0"				// whether CD-key is checked on client
//
//
// // --- network ---
// seta sv_allowdownload "0"			// whether clients are allowed to d/l maps etc from server
// seta sv_maxRate "10000" 			// download speed limit
// seta sv_floodProtect "1" 			// whether server uses flood-protection
// seta sv_master1 "master0.gamespy.com:28900"     // master servers where the server registers itself
// seta sv_master2 "master.gamershut.de:27950" 	//   to be found by players.
// seta sv_master3 "master.gnw.de:27950"		//   use +set dedicated x to tell the server whether or not
// seta sv_master4 "master3.idsoftware.com:27950"  //   to register itself there, x = 2 : register x = 1 : don't
//
//
// // --- weapons ---
// seta g_quadfactor "3"				// quad damage multiplier, default = 3
// seta g_weaponrespawn "5" 			// weapon respawn time in secs, default = 5
// seta g_friendlyfire "0"				// whether you can do damage to your team members
// seta g_teamAutoJoin "0"				// whether players are automatically added to a team
// seta g_teamForceBalance "0"			// whether teams are auto-balanced by the server
// seta g_forcerespawn "2"				// time after which players are forced to respawn, 0 = never
//
//
// // --- movement ---
// seta pmove_fixed "1"				// whether movement is independent of client framerate
// seta pmove_msec "16" 				// dont ask me
// seta sv_fps "30"				// server frame rate
//
//
// // --- bots ---
// seta bot_enable "1"				// whether bots are allowed on the server
// seta bot_minplayers "0" 			// minimum players number, filled up with bots if fewer
// seta bot_nochat "1"				// whether bots are allowed to chat
//
//
// // --- map rotation ---
exec maprotation.cfg
```

....and this is the shell script that starts the server

```
#!/bin/sh
ip="192.168.1.9"
port="27960"
name="q3a-deadbox"
 
echo running server $name on $ip : $port
 
screen -A -m -d -S $name /usr/local/games/quake3/q3ded +set sv_punkbuster 1 +set fs_basepath /usr/local/games/quake3/ +set dedicated 1 \
+set com_hunkMegs 32 +set net_ip $ip +set net_port $port +set g_log $name.log +exec q3ded.cfg
```

So, after starting the server, when I reattach to the started screen session, I see a hitch warning. Secondly, the server isn't displayed in the in-game browser window in quake 3 for all the other computers on the LAN. Where could I be going wrong?

---

