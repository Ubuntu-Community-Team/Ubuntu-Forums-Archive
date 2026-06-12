---
title: "Nexuiz Startup Problem"
date: 2009-07-27
forum: Gaming &amp; Leisure
---

### Post by adejoseph on 2009-07-27
Hey,

So I have downloaded and installed Nexuiz 2.4 for ubuntu jaunty twice now, two different ways. I first downloaded three different files, one being the music, one an info file and thirdly the game data. This gave me a problem so I uninstalled that stuff completely and downloaded the nexuiz 24 archive file that holds all the game data (its like 300 mb) and extracted the nexuiz folder inside my home directory, and from there ran the 

*nexuiz-linux-glx.sh* 

and I even tried the sdl version. The same issue happens with both and its the same issue as the last install! 



What happens: I click Nexuiz from the games menu/ or run the .sh file in the terminal (from home) and the game boots up. My screen then turns black and the power light on my monitor power button, normally a solid green, begins to blink green every 5 secs. 



The sound for the game works fine, with the warm "Welcome the NEX E US" greeting and spooky music. 



Whats more is that the only thing that shuts it down and returns me to the desktop is hitting f10, and whats even stranger is that when I take a screen shot while the game is running and my screen is black, the game exits and I can see in the screen shot pref. box a picture of the Nexuiz menu!!! Wtf ... i've searched all over for a few days now and im frustrated ...


help?

---

### Post by Ericj1186 on 2009-07-27
Did you try:
```
sudo apt-get install nexuiz
```

That worked for me when I did.  It just took a while to install.

I do not know which version of the game this is though.

---

### Post by adejoseph on 2009-07-27
Yeah, the installations went in fine - get this, i tried another game, called warsow, and the monitor itself gave me a message saying "out of range" - I installed Warsow from the package manager


ps the music on warsow works just as the nexuiz music works - I feel like its the same problem

---

### Post by Ericj1186 on 2009-07-27
Stupid question, but did you update your video card?  I doubt it would show those kinds of errors for it, but that was what I thought of immediately.  What kind of card do you have?

So, even through the package manager, it installed, but still doesn't play?

---

### Post by adejoseph on 2009-07-27
I have the geforce4 mx440 (yeah I know its a dinosaur) - The linux drive for my card is installed and works fine and I have easy access to its menu and all - and I don't see how its not the latest one; I installed linux ... maybe two months ago.

And it no it does not play, at least the screen or the monitor or something won't work, i'm thinkin it has to do with a resolution problem? I'm not sure

---

### Post by jwatne on 2010-01-02
Hi; did you eventually find a solution to this problem? The same thing is happening for me - only the power button on my monitor behaves slightly differently after starting nexuiz, showing the solid yellow that it does when it goes into standby mode.

The monitor is an old Gateway FPD1810.  Graphics card info:

```

john@UBUNTU-DESKTOP:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

```

To avoid various problems that can arise using the proprietary ATI display driver, documented in several spots in the forums, I followed the instructions [here]("https://help.ubuntu.com/community/RadeonDriver") and made sure that it is not installed.  As a check:

```

john@UBUNTU-DESKTOP:~$ dpkg --get-selections | grep xorg-driver-fglrx
john@UBUNTU-DESKTOP:~$ 

```

[i.e. no results = package not installed.]

I do not have an /etc/X11/xorg.conf file; to quote from the link above, "From Ubuntu 7.10 and onwards, the driver and server autodetect most settings. You can often just take away your xorg.conf and it will run fine."

I usually run compiz, but, as I do to solve problems with playing YouTube videos, I use the Compiz Fusion Icon to set the Window Manager to Metacity (the GNOME default) before trying to launch nexuiz.

Any ideas on something else to try?  Is there any more information I can provide that would further help diagnose what is going on?

Thanks much!

---

### Post by jwatne on 2010-01-05
Still stuck, but here is some more information.

I downloaded the latest version directly from the Nexuiz site, rather than using the version available through the repositories. I still have the monitor going into sleep mode problem.

Here are the results of attempting to run nexuiz-linux-glx.sh:

```
Nexuiz Linux 08:38:42 Oct  1 2009 - release
Trying to load library... "libz.so.1" - loaded.
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/data20091001.pk3 (9053 files)
Trying to load library... "libcurl.so.4" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
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
couldn't exec unit_repulsor.cfg
execing default25.cfg
execing physics25.cfg
execing balance25.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Initializing Video Mode: fullscreen 1024x768x32x60hz
Loading OpenGL driver libGL.so.1
GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
GL_VERSION: 1.3 Mesa 7.4
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
Sound format: 48000Hz, 2 channels, 16 bits per sample
ioctl CDROMREADTOCHDR failed
CDAudio_Init: No CD in player.
Initial CD volume: 1
CD Audio Initialized
```

Here are the results of attempting to run nexuiz-linux-sdl.sh:

```
Nexuiz Linux 08:38:45 Oct  1 2009 - release
Trying to load library... "libz.so.1" - loaded.
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/data20091001.pk3 (9053 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
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
couldn't exec unit_repulsor.cfg
execing default25.cfg
execing physics25.cfg
execing balance25.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.13
GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
GL_VERSION: 1.3 Mesa 7.4
0 SDL joystick(s) found:
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
```

The sound was much less choppy for the sdl version, but the monitor was still put into sleep mode.

Anything in the log files ring a bell?

Thanks much!

---

### Post by jwatne on 2010-01-06
Hello, all.

I got a solution from "Ed" on the alientrap.org forums, at [http://alientrap.org/forum/viewtopic.php?f=3&t=5783&p=74310#p74310]("http://alientrap.org/forum/viewtopic.php?f=3&t=5783&p=74310#p74310"):

> It sounds like what might happen if you are asking the monitor to display something out of range. Many monitors do now have an 'out of range' message but not all. You could refer to your monitors documentation to see what it's out of range behaviour is.

What resolution are you running the desktop at? Nexuiz by default will try 800x600 initially. You could try running Nexuiz from the command line and appending '-window' to see if running Nexuiz in window mode allows the screen to be displayed properly. You could then try editing ~/.nexuiz/config.cfg and setting (or adding) vid_width and vid_height to different values to see if other resolutions start OK.

I found the complete path for the file was actually ~/.nexuiz/**data/**config.cfg on my machine.  I added the following lines to the end of the file:
```
vid_height "624"
vid_width "832"
```
Try some of the options found in the "Resolution" dropdown in System > Preferences > Display.  Since I remembered having weird screen flickering when I first tried attempting [old] installations of fedora and ubuntu with 640x480 resolution, which stopped when I bumped up to the 1024 x 768 resolution, I thought it would be best to try the next higher resolution option above 800x600 for a first test.

adejoseph, does this solve your problem with the game as well?

---

