---
title: "Mplayer trouble"
date: 2006-06-01
forum: Desktop Environments
---

### Post by SweVoyager on 2006-06-01
Hello,

Just upgraded from Breezy to Dapper, and everything works fine except Mplayer.  When I try to start it it just throws up a small error window which disappears real quickly.

Anybody care to guess why?

Should I try and delete Mplayer and reinstall it, or whats the usual way to go from here (reinstalling seems a bit Windowsish)?

---

### Post by Nikos.Alexandris on 2006-06-01
Just want to verify this conflict... ! I have the same problem. Greetings.

---

### Post by Jasper Houtman on 2006-06-01
I just upgraded to 6.06 aswell.
Mplayer completely stopped working (doesn't even start up).
I reinstalled mplayer but that didn't help.
Hope someone finds a solution to this.

---

### Post by linuchsan on 2006-06-01
if you do mplayer file in a terminal....what does it say?

---

### Post by Jasper Houtman on 2006-06-01
Can nolonger check that I'm afraid. I deinstalled mplayer completely and switched to kaffeine now. 

Did read something about this in another thread though (can't find it but I'll post it in here if i stumble into that thread again).

Had something to do with codecs nolonger being supported or "illegal" and as far as I can tell mplayer is nolonger available in the add programs section, via apt-get and in the synaptic package manager.

also installed vlc but somehow I can't get that to work with firefox (kaffeine works fine though).

I recall someone saying you could still get mplayer through the add programs if you did made some changes somewhere which would allow "multiverse packages" (???)

couldn't get that to work but then again I'm quite new at linux

Quite happy with kaffeine and VLC though, although I would still prefer mplayer.

---

### Post by mcpish on 2006-06-01
you may want to completely remove your old mplayer configuration directory.  It should be a hidden folder named ".mplayer" in your home directory.  Then reinstall the new package from the repositories.

---

### Post by Rondonjin on 2006-06-01
[QUOTE=Jasper Houtman]Can nolonger check that I'm afraid. I deinstalled mplayer completely and switched to kaffeine now. 

Did read something about this in another thread though (can't find it but I'll post it in here if i stumble into that thread again).

Had something to do with codecs nolonger being supported or "illegal" and as far as I can tell mplayer is nolonger available in the add programs section, via apt-get and in the synaptic package manager.

also installed vlc but somehow I can't get that to work with firefox (kaffeine works fine though).

I recall someone saying you could still get mplayer through the add programs if you did made some changes somewhere which would allow "multiverse packages" (???)

couldn't get that to work but then again I'm quite new at linux

Quite happy with kaffeine and VLC though, although I would still prefer mplayer.[/QUOTE]

MPlayer works fine here on Dapper. Google for easyubuntu or automatix. Easyubuntu will setup the repositories you need to install the codecs you need to play most MM files. Automatix will install everything but the kitchen sink :) 

Wayne

---

### Post by deadgobby on 2006-06-01
After I upgraded I did too loose Mplayer and after reinstalling Automatix. Still Mplayer has been lost. This is what I get in the terminal
[COLOR="Blue"]ubuntu:~$ mplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>   play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <timepos>    seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *
[/COLOR]

---

### Post by deadboy on 2006-06-02
If you run gmplayer in terminal and you get an error message about skins missing.  Then simply reinstall the package called mplayer-skins in synaptic, this worked for me.  If it still doesn't work try reinstalling both mplayer and mplayer-skins.

If this still doesn't work, run gmplayer in terminal and paste the output that you get.

---

### Post by mikketeve on 2006-06-02
To install Mplayer you need to enable the Multiverse Repositories in Synaptic.
See [this wiki page]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29").

If you upgrade without enabling multiverse repositories, this may be the cause of your problems?

---

### Post by Jasper Houtman on 2006-06-02
Activated the multiverse repositories as instructed. I can install a lot of other programs now but when I select mplayer I get a message that the package is refered to but nolonger available (???).

I'll try looking for the mplayer site and see if I can manually install it

---

### Post by Jasper Houtman on 2006-06-02
Gotten a lot further now. Manual install failed but I can select the package in synaptic package manager now.

The only problem I have now is that I have a dependency that wont install (libjack0.80.0-0).

aparently the (new) version of jackd is not compatible (and I can't find the one it's refering to).

is there any way to get this to work?

---

