---
title: "UT2004 Segmentation Fault?"
date: 2009-06-18
forum: Gaming &amp; Leisure
---

### Post by Wa1k3rTXRang3r on 2009-06-18
when i try to run ut2004 it shows the splash screen then just crashes and gives this error.

Help?


Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.

---

### Post by simeon87 on 2009-06-18
Did you update to the latest version (3369)?

UT2004 on Linux used to crash randomly for me as I had forgotten to download the latest patch.

---

### Post by Wa1k3rTXRang3r on 2009-06-18
no i havent tried that. ill try it out. thanks

---

### Post by Technophobia on 2009-06-19
Did you feed it 

sudo apt-get install libstdc++5

yet?

---

### Post by crunchtime on 2009-06-19
I've got the same SIGSEGV error, and I'm running Jaunty. A friend of mine is running Intrepid and hasn't had any problems.

Strangely, the game ran fine until this morning, when all this started up. I've thought about what I did in-game prior to these problems and can't come up with anything odd (the only setting I changed was FOV to 100; after the problem arose, I switched it back in the .ini, to no avail). Nor can I recall installing any updates through Update Manager.

I have the latest libstdc++5 and am running version 3369.

Here's my ut2004.log file.

```
Log: Log file open, Fri Jun 19 15:48:45 2009
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec 16 2005 13:23:47
Init: Command line: 
Init: (This is Linux patch version 3369.2)
Init: Character set: Unicode
Init: Base directory: /home/crunchtime/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 1.640062...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=crunchtime?Class=Engine.Pawn?Character=Romulus?team=0?Sex=M?SpectatorOnly=1
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33871->33868; refs: 350196
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 2.000184...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x874bdd9]
Log: [ 2]  [0xb80d7400]
Log: [ 3]  ./ut2004-bin(_ZN15FConfigCacheIni10GetSectionEPKwPwiS1_+0x3b) [0x816decb]
Log: [ 4]  ./ut2004-bin(_Z9CacheLoadI13UCachePlayersEvRT_+0x758) [0x8886d68]
Log: [ 5]  ./ut2004-bin(_Z8CacheGetI13UCachePlayersEPT_v+0xa3) [0x88864b3]
Log: [ 6]  ./ut2004-bin(_ZN6UxUtil19execGetPlayerRecordER6FFramePv+0xb7) [0x8882967]
Log: [ 7]  ./ut2004-bin(_ZN7UObject15execHighNative2ER6FFramePv+0x5f) [0x86f0d9f]
Log: [ 8]  ./ut2004-bin(_ZN7UObject16execClassContextER6FFramePv+0x1ca) [0x86d113a]
Log: [ 9]  ./ut2004-bin(_ZN7UObject7execLetER6FFramePv+0x25c) [0x86d28fc]
Log: [10]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86f6015]
Log: [11]  ./ut2004-bin(_ZN7UObject12CallFunctionER6FFramePvP9UFunction+0x47e) [0x86f5cee]
Log: [12]  ./ut2004-bin(_ZN7UObject19execVirtualFunctionER6FFramePv+0x46) [0x86d2d26]
Log: [13]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86f6015]
Log: [14]  ./ut2004-bin(_ZN7UObject12ProcessEventEP9UFunctionPvS2_+0x1f7) [0x86f6337]
Log: [15]  ./ut2004-bin(_ZN11UGameEngine4InitEv+0x1953) [0x82bbc83]
Log: [16]  ./ut2004-bin [0x8165f39]
Log: [17]  ./ut2004-bin(main+0x33f0) [0x8160af0]
Log: [18]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7dff775]
Log: [19]  ./ut2004-bin(readdir+0x91) [0x815d4b1]
Log: Unreal Call Stack: FConfigCacheIni::GetSection <- UxUtil::CacheLoad <- UxUtil::CacheGet <- UxUtil::execGetPlayerRecord <- UObject::execClassContext <- UObject::ProcessEvent <- UGameEngine::Init <- InitEngine
Exit: Exiting.
Log: FileManager: Reading 0 GByte 39 MByte 993 KByte 252 Bytes from HD took 0.098790 seconds (0.098790 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Fri Jun 19 15:48:47 2009
```

---

### Post by Wa1k3rTXRang3r on 2009-06-20
yea thats what happened to me it was running perfectly and then all of a sudden i just kept getting sigsev errors.

ill have to reinstall it later and try out some of your suggestions.

---

### Post by crunchtime on 2009-06-22
Update: I tried reinstalling in my old directory (/home/username/ut2004); even after patching, the game continued to SIGSEGV. Finally, I installed the game in its default directory (/usr/local/games/ut2004) and it works fine.

If it crashes again, I'll update again.

---

### Post by Wa1k3rTXRang3r on 2009-06-22
how can i give the installer permission to save it to the default directory?

---

### Post by crunchtime on 2009-06-22
I had to copy linux-installer.sh to my hard drive, then run it with sudo ("sudo sh linux-installer.sh"). That way, I could install it to any directory and eject the disks as needed.

---

### Post by Wa1k3rTXRang3r on 2009-06-23
o ok. thanks. as soon as i get the time to try it out, ill let you guys know the results

---

### Post by Adrenilator on 2009-06-27
Really Not a Reply, but same thing...
Just Started a server, works fine till we use the vehicle guns i made...
then at random i get the sigsegv mania....
no other info, and says crash info will be saved to log file, unless thats the logfile i'm reading it off of, don't know where it is...
yes as u can see, i'm a noob admin, and the stuff u were talking about in this post, made me feel even more noobish, for a lamo admin, can someone please explain what the "lib blah blah blah" is that i'm supposed to "feed" my server?
and Hurry, cause this sigsegv thing is about to drive me insane!!!!!!

---

