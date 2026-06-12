---
title: "Game Server Need packets"
date: 2008-02-27
forum: Gaming &amp; Leisure
---

### Post by Shinitenshi on 2008-02-27
Ok I installed Ubuntu and the only thing I want it to run is a Half Life Game server Mod called Natural Selection. Well all the is fine but I installed Amx mod x to administrate that server and I added couple plugins to spice it up a bit and i keep getting an error message. I looked over the web and its aperantly a C++ deal a packet I dont have installed or what eva.

[http://www.nsmod.org/forums/index.php?showtopic=9444&view=findpost&p=44387](http://www.nsmod.org/forums/index.php?showtopic=9444&view=findpost&p=44387)

same error as him but he got it resolved. only problem is he wasnt specific on how he solved it he just left the forum lol. do you guys know what packets to install?

here the actual error message i get:
L 02/27/2008 - 18:02:33: [META] ini: Read plugin config for: <amxmodx_mm_i386.so>
L 02/27/2008 - 18:02:33: [META] ini: Read plugin config for: <extralevels3_i386.so>
L 02/27/2008 - 18:02:33: [META] ini: Read plugin config for: <libwhichbot.so>
L 02/27/2008 - 18:02:33: [META] ini: Finished reading plugins list: /home/shinitenshi/servers/hlds/ns/addons/metamod/plugins.ini; Found 3 plugins to load
L 02/27/2008 - 18:02:33: [META] dll: Loading plugins...
L 02/27/2008 - 18:02:33: [META] dll: Loaded plugin 'AMX Mod X': AMX Mod X v1.8.0.3660 Oct 25 2007, AMX Mod X Dev Team
L 02/27/2008 - 18:02:33: [META] ERROR: dll: Failed query plugin '<extralevels3_i386.so>'; Couldn't open file '/home/shinitenshi/servers/hlds/ns/addons/extralevels3/extralevels3_i386.so': libstdc++.so.6: cannot open shared object file: No such file or directory
L 02/27/2008 - 18:02:33: [META] ERROR: dll: Skipping plugin '<extralevels3_i386.so>'; couldn't query
L 02/27/2008 - 18:02:33: [META] ERROR: dll: Failed to load plugin 'extralevels3_i386.so'

loaded 3 plugins but the extralevels3 doesnt load because it doesnt have a certain file. PLEASE HELP!!

---

### Post by Cappy on 2008-02-27
```
sudo apt-get install libstdc++6
```

---

### Post by Shinitenshi on 2008-02-28
Ok i totally erased ubuntu and installed the most latest version 7. something. well now its even worse! lol now no one can join my server  because it crashes when ppl do. here the error

pipes.cpp (484) : Assertion Failed: bRet
pipes.cpp (536) : Assertion Failed: bRet
steamclient.cpp (371) : Assertion Failed: pClientPipe->BWriteAndReadResult( buf, bufRet )
steamclient.cpp (373) : Assertion Failed: bufRet.TellPut() == ( sizeof(HSteamUser) + sizeof(uint8) )

---

