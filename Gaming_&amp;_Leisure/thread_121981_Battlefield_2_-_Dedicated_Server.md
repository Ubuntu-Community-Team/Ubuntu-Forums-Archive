---
title: "Battlefield 2 - Dedicated Server"
date: 2006-01-26
forum: Gaming &amp; Leisure
---

### Post by MaXiMus on 2006-01-26
Has anyone set up a dedicated server for Battlefield 2? If so, can you help me set up mine?[-o<

---

### Post by MaXiMus on 2006-01-26
Here's my problem. I downloaded the "bf2-linuxded-1.1.2554-356-installer.sh" from EA. I installed the dedicated server in a folder I created on the desktop. When I try to startup the server I get this:  

maximus@MaximusServer:~$ cd /home/maximus/Desktop/bf2
maximus@MaximusServer:~/Desktop/bf2$ ./start.sh
/home/maximus/Desktop/bf2/bin/ia-32/bf2: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
maximus@MaximusServer:~/Desktop/bf2$

I am guessing that part of the problem has to do with libstdc++.so.5? What should I do?

---

### Post by MaXiMus on 2006-01-26
I looked at other application install problems that had the same error and found the fix.

maximus@MaximusServer:~/Desktop$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gcc-3.3-base
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/446kB of archives.
After unpacking 1077kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 61054 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-8ubuntu1_i386.deb) ...
Setting up gcc-3.3-base (3.3.6-8ubuntu1) ...
Setting up libstdc++5 (3.3.6-8ubuntu1) ...

Sorry for being too anxious and not persistent enough!

---

### Post by jackmacokc on 2006-02-19
Yes, I'm runing BF2-1.2 dedicated just fine. Sounds like you need to do this..

```
 sudo apt-get install build-essential 
```

As long as you have all the dependencies, the server itself is very easy to configure and run. Just edit the ./mods/bf2/settings/serversettings.con file to your needs. So..

```
cd /path_to_your_bf2_server
sudo gedit mods/bf2/settings/serversettings.con

```

Then launch the server!

```
./start.sh
```

It should fire up and viola! Let me know if you need any more help. It took me awhile to figure it out as well. 

Also, check this site. [http://www.dragonbe.be/index.php?module=battlefield2]("http://www.dragonbe.be/index.php?module=battlefield2").
It's pretty helpful. PM me or let me know if I can help anymore. I have BFVietnam and BF2 running on my breezy box that i use for LAN parties.

Here's my serversettings.con just in case you want to see one that works. Notice no IP is specified. This forces it into local LAN mode...rather than internet mode.
```

sv.serverName "JackMac BF2 1.2-Linux"
sv.password ""
sv.internet 0
sv.serverIP ""
sv.serverPort 16567
sv.welcomeMessage "Welcome!"
sv.punkBuster 0
sv.allowFreeCam 0
sv.allowExternalViews 1
sv.allowNoseCam 1
sv.hitIndicator 1
sv.maxPlayers 16
sv.numPlayersNeededToStart 2
sv.notEnoughPlayersRestartDelay 5
sv.startDelay 15
sv.endDelay 15
sv.spawnTime 5
sv.manDownTime 20
sv.endOfRoundDelay 15
sv.ticketRatio 100
sv.roundsPerMap 1
sv.timeLimit 15
sv.scoreLimit 0
sv.soldierFriendlyFire 100
sv.vehicleFriendlyFire 100
sv.soldierSplashFriendlyFire 100
sv.vehicleSplashFriendlyFire 100
sv.tkPunishEnabled 0
sv.tkNumPunishToKick 5
sv.tkPunishByDefault 1
sv.votingEnabled 0
sv.voteTime 90
sv.minPlayersForVoting 2
sv.gameSpyPort 29900
sv.allowNATNegotiation 0
sv.interfaceIP ""
sv.autoRecord 0
sv.demoIndexURL http://
sv.demoDownloadURL http://
sv.autoDemoHook "adminutils/demo/rotate_demo.py"
sv.demoQuality 1
sv.adminScript "default"
sv.timeBeforeRestartMap 30
sv.autoBalanceTeam 0
sv.teamRatioPercent 100
sv.voipEnabled 1
sv.voipQuality 3
sv.voipServerRemote 0
sv.voipServerRemoteIP ""
sv.voipServerPort 55125
sv.voipBFClientPort 55123
sv.voipBFServerPort 55124
sv.voipSharedPassword ""
sv.useGlobalRank 1
sv.useGlobalUnlocks 1
sv.sponsorText ""
sv.sponsorLogoURL ""
sv.communityLogoURL ""
sv.radioSpamInterval 6
sv.radioMaxSpamFlagCount 6
sv.radioBlockedDurationTime 30
sv.friendlyFireWithMines 0

```

---

### Post by turbomursu on 2009-02-23
jackmacokc: thanks for your post. it helped me to set up my server. especially that link to dragonbe.be is golden!

---

