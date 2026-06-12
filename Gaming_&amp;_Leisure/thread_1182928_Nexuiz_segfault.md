---
title: "Nexuiz segfault"
date: 2009-06-09
forum: Gaming &amp; Leisure
---

### Post by Scouto2 on 2009-06-09
Hi,
I just downloaded the 32-bit version of Nexuiz for Ubuntu Jaunty Jackalope (that is the version that is included on the most recent live-cd, right?), and I got it to work after installing all three parts (launcher, data, and music). The game has a segmentation fault whenever I either
A) Join a game online
B) Have a single-player game

Therefore, the program can only be used as a very flashy menu, no game. If I wanted just a very flashy menu whose actual program didn't work, I would have installed Windows Vista.

Here's the Terminal log:
james@Z60t:~$ /usr/games/nexuiz
Nexuiz Linux 15:48:25 Apr 21 2009 - debug
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (7505 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (12 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" "libmodplug.so" "/usr/games/libmodplug.so.0" "/usr/games/libmodplug.so" - failed.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/games/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics25.cfg
execing newhook.cfg
execing ctfscoring-div0.cfg
execing weapons.cfg
execing normal.cfg
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.13
get fences failed: -1
param: 6, val: 0
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 915GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.4
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
    Channels  : 2
    Format    : 0x8010
    Frequency : 48000
    Samples   : 2048
Obtained audio specification:
    Channels  : 2
    Format    : 0x8010
    Frequency : 48000
    Samples   : 2048
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized

Trying to connect...

Trying to connect...

Trying to connect...
"challenge WV^QcDD})Vc" received, sending connect request back to 79.170.88.122:26000
Got challenge response
"challenge WV^QcDD})Vc" received, sending connect request back to 79.170.88.122:26000
Got challenge response
"challenge WV^QcDD})Vc" received, sending connect request back to 79.170.88.122:26000
Got challenge response
"challenge WV^QcDD})Vc" received, sending connect request back to 79.170.88.122:26000
Got challenge response
"challenge WV^QcDD})Vc" received, sending connect request back to 79.170.88.122:26000
Got challenge response
Accepted

Connection accepted to 79.170.88.122:26000
--> client to server keepalive
<-- server to client keepalive

Server: Nexuiz build 13:53:05 May  1 2009 8941 release (progs 30888 crc)

<===================================>


CDAudio: Bad track number 0.
Segmentation fault

---

### Post by prshah on 2009-06-09
> **Scouto2 said:**
> 
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized

CDAudio: Bad track number 0.
Segmentation fault

Maybe you need to pop in an audio CD?

---

### Post by Scouto2 on 2009-06-09
I'll try that and get back in a minute...

EDIT:
Nothing new besides...
Yellow text in the terminal?

james@Z60t:~$ /usr/games/nexuiz
Nexuiz Linux 15:48:25 Apr 21 2009 - debug
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (7505 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (12 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" "libmodplug.so" "/usr/games/libmodplug.so.0" "/usr/games/libmodplug.so" - failed.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/games/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics25.cfg
execing newhook.cfg
execing ctfscoring-div0.cfg
execing weapons.cfg
execing normal.cfg
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.13
get fences failed: -1
param: 6, val: 0
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 915GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.4
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
    Channels  : 2
    Format    : 0x8010
    Frequency : 48000
    Samples   : 2048
Obtained audio specification:
    Channels  : 2
    Format    : 0x8010
    Frequency : 48000
    Samples   : 2048
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
Can't get initial CD volume
CD Audio Initialized

Trying to connect...
"challenge -<O3_aUui*K" received, sending connect request back to 194.50.163.207:28000
Got challenge response
Accepted

Connection accepted to 194.50.163.207:28000
--> client to server keepalive
<-- server to client keepalive

Server: Nexuiz build 19:36:08 May  1 2009 - release (progs 30888 crc)

<===================================>

[COLOR=Yellow]Soylent Space[/COLOR]
CDAudio: Bad track number 0.
Segmentation fault
james@Z60t:~$

---

### Post by detrate on 2009-06-10
I've never installed the game from the repository as it's usually out of date (though this actually seems to be a 2.5.1 release which is surprisng).

Regardless, I'd recommend downloading the zip from the website, [www.nexuiz.com](www.nexuiz.com) and see if it works for you then.

For more information, refer to my [installation guide](http://www.ubuntumagazine.net/?p=1984).


If it's still not working, please share more information about your computer hardware.

---

### Post by LinuxFox on 2009-06-10
> **detrate said:**
> Regardless, I'd recommend downloading the zip from the website, [www.nexuiz.com](www.nexuiz.com) and see if it works for you then.
I also say to try that seeing that's what I use to play Nexuiz.  You shouldn't need an audio CD, I've played it plenty of times without the CD.  Though, I never had that problem.  I put the Nexuiz game folder in the home directory and run it by opening "nexuiz-linux-glx.sh" (I made a shortcut to it in the Games menu and on the desktop).

I don't know if it would work for you, but it wouldn't hurt to try it.

---

### Post by detrate on 2009-06-10
That's just legacy quake code trying to 'load a cd' -- the cd tracks are ogg files in the music or data pack (depending on how you installed the game).

The audio track error is nothing to fret.

---

### Post by Scouto2 on 2009-06-10
Thanks Detrate!

I wish there was some form of a "kudos" system on this board.

Got the game to work, it is awesome! I love the platformer characteristics on some of the maps. This is a great game.

---

### Post by Scouto2 on 2009-06-10
Okay, now I have a new problem.

The game will randomly freeze while loading objects (usually with a "g" in the name IE G_242080)

---

### Post by Scouto2 on 2009-06-11
So, umm... any reason why it freezes? And any workarounds?

---

### Post by Scouto2 on 2009-06-12
Bump.

---

### Post by blmartech on 2009-10-11
"Got the game to work, it is awesome! I love the platformer characteristics on some of the maps. This is a great game."

Love the fact he got it to work, confused as to why he didnt post his solution!

---

