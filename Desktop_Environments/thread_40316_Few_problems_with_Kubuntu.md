---
title: "Few problems with Kubuntu"
date: 2005-06-08
forum: Desktop Environments
---

### Post by dabotsonline on 2005-06-08
I'm running a Celeron 2.8GHz laptop with 512MB RAM and a SiS M661FX chipset with integrated graphics.  I have installed w32codecs for video.  My problems are as follows:

1.  My sound playback is quiet and crackly, even after having adjusted the settings in KMix and switching between ALSA and OSS.  The SiS chipset has AC97 sound.  The following information is provided under "Sound" in KInfoCenter:

> Sound Driver: 3.8.1a-980706 (ALSA v1.06 emulation code)

Installed drivers: 
Type 10: ALSA emulation

Card config:
SiS SI7012 with VT1616i at 0xe200, irq 18

Audio devices:
0: SiS SI7012 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

MIDI devices: NOT ENABLED IN CONFIG

Timers: 
7: system timer

Mixers:
0: ICEnsemble VT1616i

2. When I try to play back a DVD in Kaffeine or VLC the picture is slightly grainy, and more jerky than in WinDVD or PowerDVD on Windows XP.  One Kaffeine, if I try to select any buttons in the DVD's menu, I get the error "Video Encode Assist" in big letters.  Again, cycling through all the xine video and audio codec options makes no difference.  In MPlayer, the DVD only plays if I select "DVB audio output", and then it still gives the warning "Could not open/initialize audio device - no sound", and plays with no sound.  With all other video and audio codec combinations, I get the error:

> MPlayer interrupted by signal 11 in module: unknown
- MPlayer crashed by bad usage of CPU/FPU/RAM.
Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
gcc version. If you think it's MPlayer's fault, please read
DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
won't help unless you provide this information when reporting a possible bug.

3.  I have installed NeroLinux and KTrafficAnalyzer from .deb files (the latter having been converted from an RPM using alien), but typing "nerolinux" or "ktrafficanalyzer" at the terminal gives a "command not found" error,

4.  In Vim, is there any way to copy text from outside Vim (e.g. a web page) into Vim?  "Shift+Ins" and "p" do not work.

5. Is there any way that I can click on a packet number on an XDCC site (e.g. IRCSpy or PacketNews) and then automatically paste the details into KVIrc (as you can do on Windows with IE and mIRC)?


I should point out that I am a Linux novice/newbie, as my only experience is from last Septermber, using Fedora Core 2 at uni.

Thanks for your help,

Nick

---

### Post by dabotsonline on 2005-06-08
Another thing, I have Firestarter set up to start automatucally on load-up, and indeed Kubuntu says "Loading Firestarter" during boot-up and "Closing Firetstarter" during shutdown.  However, it does not appear in the Process Table when KDE loads up, so I have to type "sudo firestarter" at the terminal to load it.  How can I correct this?

Thanks.

---

### Post by ltmon on 2005-06-08
I can't answer all your problems but I'll give a few a quick try:

1. Try running "kmix" or "kamix" (I can't remember which is which).  In some kind of advanced tab you can turn on and off settings such as 3d sound.  Turning off 3d sound helped my ac97 sound card immensely

4. Installing "kvim" or "xvim" might help with better desktop integration (i.e. copy and paste) than just plain command line vim.  I usually just select text in my browser, press "i" in Vim to begin inserting and middle click on the cursor.

Firestarter problem.  I don't use this, but guarddog is a similar program with better KDE integration.  I haven't had any problems with guarddog.

L.

---

### Post by dabotsonline on 2005-06-09
I realised that I could achieve what I wanted in Vim anyway, by middle clicking, so that's sorted!  I tried out GuardDog and that seems good.  However, all the other problems persist  :mad: 

Another thing, where are the Firefox bookmarks stored?  It doesn't seem to be /etc/mozilla-firefox/profile .  I've done a search for "bookmarks.html" but it comes up with no results.

---

