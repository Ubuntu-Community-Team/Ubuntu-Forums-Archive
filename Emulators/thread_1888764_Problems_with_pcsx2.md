---
title: "Problems with pcsx2"
date: 2011-11-30
forum: Emulators
---

### Post by Cavid on 2011-11-30
Hello everyone. I just downloaded pcsx2 (Seemed like only hope to play good game on Linux (( ). And I think plugins and bios is ok. But I tried to play Dark cloud 1, but nothing. A window showed up, and was hearing the start sound of ps2. But unfortunately, the window wasn't showing anything, just fps( and it was around 40-50). So I want to know if the problem in game or something. And i'd really appreciate if someone could post here which games he.she played with this emu. And if possible user who have experience with this emu, post help maybe I configured plugins bad or something.

P.S>Well my video card isn't "brilliant" I am using Toshiba satellite L300 with it's standard videocard. It's Vram should be around 368 (Checked when I used Windows, don't know if it is same in Linux)  
Sorry for this long long post:P

---

### Post by frostwork on 2011-11-30
at least it's the only hope to play good ps2 games under linux.
pcsx2 is very hardware demanding.
I've got a GeForce GTX 460 and a Q9550 and sucessfully played through  FFX and FFXII under ~x86 gentoo with pcsx2 svn. pcsx2 settings have been  more or less default afair. no chance to play f.e. wipeout fusion in  full speed with this machine though, at least not with those settings.

---

### Post by Cavid on 2011-11-30
Well, I found what the problem is. My plugins (video, usb and cd/dvd) are null, which I've figured out is just for testing, that's why I heard the music but not the video. I tried to find something from other forums, but I am totally noob, there was something about compiling, and svn I don't understand anything. Isn't there any plugins just to download and apply?

---

### Post by frostwork on 2011-12-01
I'd try the official build from 
[http://pcsx2.net/downloads.php](http://pcsx2.net/downloads.php)
can't help with ubuntu packages

---

### Post by satanselbow on 2011-12-01
I got it running on 11.10 by following the install routine found in the Arch PKGBUILD in their AUR which will give you a good list of dependencies ;)

Unfortunately my current machine is not really powerful enough in the gfx department to make best use of it :(

---

### Post by Cavid on 2011-12-02
Can anyone just upload plugins? As I said I am totally noob, to that dark side of computer(Compiling, source code and etc. What the hell is this) . Pls pls help

---

### Post by thatguruguy on 2011-12-02
You may want to try the following.

First, remove your copy of pcsx2.

Second, install the [micove console gaming ppa]("https://launchpad.net/%7Emicove/+archive/console") by opening a terminal and typing the following:
```
sudo add-apt-repository ppa:micove/console
```
You'll be prompted for your password, and then asked to confirm adding the ppa to your repositories.

After the ppa has been added, type the following in your terminal:
```
sudo apt-get update
sudo apt-get install pcsx2
```

The benefit of doing it this way is that all necessary plugins should be installed, along with all dependencies.

---

### Post by Cavid on 2011-12-02
Thank you very much!!!!! You are the man!!! I can't find words to thank you!! Oh, oh, I am gonna cry:lolflag:

---

### Post by heminder on 2012-01-07
hey. 

i'm having trouble with this too. at first i was using the GSnull plugin and it was just showing a grey window while playing the PS2 bootup sound. i realised it was a "null" plugin, so i changed it to ZZ Ogl. it wouldn't do anything. when i booted it, it just threw up an error with an invisible window which i have to xkill to get past to clicking anything behind it. i've installed it using the PPA method now, and it's still doing the same thing.

help?

here's my bios log:```
PCSX2 0.9.8.r0  - compiled on Nov  5 2011
Savestate version: 0x9a010000

Host Machine Init:
	Operating System =  Linux 2.6.32-37-generic-pae i686
	Physical RAM     =  3014 MB
	CPU name         =  Genuine Intel(R) CPU           T2300  @ 1.66GHz
	Vendor/Model     =  GenuineIntel (stepping 08)
	CPU speed        =  1.662 ghz (2 logical threads)
	x86PType         =  Standard OEM
	x86Flags         =  bfe9fbff 0000c1a9
	x86EFlags        =  00100000

x86 Features Detected:
	MMX.. SSE.. SSE2.. SSE3

Installing POSIX SIGSEGV handler...
Reserving memory for recompilers...

Loading plugins...
	Binding GS	: /usr/lib/games/pcsx2/plugins/libzzogl.so 
	Binding PAD	: /usr/lib/games/pcsx2/plugins/libonepad.so 
	Binding SPU2	: /usr/lib/games/pcsx2/plugins/libzerospu2.so 
	Binding CDVD	: /usr/lib/games/pcsx2/plugins/libCDVDnull.so 
	Binding USB	: /usr/lib/games/pcsx2/plugins/libUSBnull.so 
	Binding FW	: /usr/lib/games/pcsx2/plugins/libFWnull.so 
	Binding DEV9	: /usr/lib/games/pcsx2/plugins/libdev9null.so 
Plugins loaded successfully.

(GameDB) 9082 games on record (loaded in 680ms)
HLE Notice: ELF does not have a path.


Initializing plugins...
	Init GS
	Init PAD
	Init SPU2
	Init CDVD
	Init USB
	Init FW
	Init DEV9
Plugins initialized successfully.

Opening plugins...
	Opening GS
Closing plugins...
	Closing GS
Plugins closed successfully.
Shutting down plugins...
(pxActionEvent) GS plugin failed to open!(thread:MTGS)(thread:EE Core)
Plugins shutdown successfully.
User-canceled plugin configuration after plugin initialization failure.  Plugins unloaded.

```

---

