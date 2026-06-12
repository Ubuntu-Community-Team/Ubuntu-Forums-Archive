---
title: "PCSXE2 won't boot."
date: 2012-01-08
forum: Emulators
---

### Post by heminder on 2012-01-08
hey. 

i'm having trouble getting this PS2 emulator to work. i've got the bios loaded and i'm using the ZZogl plugin. when i boot it, it just throws up an error and an invisible window which i have to xkill to get past to clicking anything behind it. the GSnullplugin plays the PS2 startup sound but shows no video. i've tried loading it with compiz off too, but no luck.

i'd been using the official download from the website, but i've now installed it using the PPA [method]("http://ubuntuforums.org/showpost.php?p=11506329&postcount=7"), and it's still doing the same thing.

help?

here's my log:```
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

### Post by thatguruguy on 2012-01-08
That's really weird.  I can't recreate that problem.

Did you make sure to completely remove your previous installation of pcsx32 first?

---

### Post by thatguruguy on 2012-01-09
Waitaminnit.  I just noticed the following:
> 
Host Machine Init:     Operating System =  Linux 2.6.32-37-generic-pae i686

If you're running a 32-bit OS, why are you using the ppa for 64-bit Ubuntu?  Just use the "official" ppa, which is available here: [https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa")

---

### Post by heminder on 2012-01-09
yep, the first install was an executable in its own folder, and i deleted it.

hmm, i wasn't aware that the micove ppa was 64-bit. 
i've just purged my current install and used the gregory repo. 
still produces the same error though :(

---

### Post by xovertheyearsx on 2012-03-23
I'm having the same exact issue!
my hardware is slightly different, although, it works fine up until it attempts to initialize ANY game I attempt to load >.<

i've attempted the binary!
i've installed ALL dependencies!
i purged the original binaries!
i'm even using the official PPA for ubuntu!
[https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa]("https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa")

it still won't work :mad:

i need help!!!!

> 
PCSX2 0.9.8.r0  - compiled on May  2 2011
Savestate version: 0x9a010000

Host Machine Init:
	Operating System =  Linux 2.6.32-40-generic i686
	Physical RAM     =  2895 MB
	CPU name         =  AMD Turion(tm) 64 X2 Mobile Technology TL-60
	Vendor/Model     =  AuthenticAMD (stepping 02)
	CPU speed        =  0.799 ghz (2 logical threads)
	x86PType         =  Standard OEM
	x86Flags         =  178bfbff 00002001
	x86EFlags        =  ebd3fbff

x86 Features Detected:
	MMX.. SSE.. SSE2.. SSE3
	MMX2  .. 3DNOW .. 3DNOW2

Installing POSIX SIGSEGV handler...
Reserving memory for recompilers...

Loading plugins...
	Binding GS	: /usr/lib/games/pcsx2/plugins/libzzogl.so 
	Binding PAD	: /usr/lib/games/pcsx2/plugins/libPADnull.so 
	Binding SPU2	: /usr/lib/games/pcsx2/plugins/libzerospu2.so 
	Binding CDVD	: /usr/lib/games/pcsx2/plugins/libCDVDnull.so 
	Binding USB	: /usr/lib/games/pcsx2/plugins/libUSBnull.so 
	Binding FW	: /usr/lib/games/pcsx2/plugins/libFWnull.so 
	Binding DEV9	: /usr/lib/games/pcsx2/plugins/libdev9null.so 
Plugins loaded successfully.

(GameDB) 9082 games on record (loaded in 451ms)
**HLE Notice: ELF does not have a path.**

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
**(pxActionEvent) GS plugin failed to open!(thread:MTGS)(thread:EE Core)**
Plugins shutdown successfully.
Bios Found: USA     v02.20(10/02/2006)  Console


---

### Post by moocow1452 on 2012-04-06
Same here. Trying to use the Netflix .iso, seems to run framerate, but no screen. Borked myself using micove ppa too, not even doing the fps count now with the bin, the unstable svn, or any iteration. Peppermint Two.

---

