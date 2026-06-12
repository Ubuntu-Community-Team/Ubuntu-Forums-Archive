---
title: "mplayer"
date: 2006-02-09
forum: Desktop Environments
---

### Post by krcm on 2006-02-09
hello,
I have something weird going on with my mplayer. 
Moviefiles I have on my pc are working fine when I 'open with' mplayer. Everything nice and smooth.
But when I try to open the programm from the multimedia menu nothing much happens. The icon starts bouncing as if it's starting normally but then it suddenly stops.:-k 

thanks
An

---

### Post by Kiwinote on 2006-02-09
Applications > System tools > Applications Menu Editor
Find mplayer => view properties => make sure that the command that is there works in the terminal, if not locate mplayer and and make new command. In my case the command is "gmplayer"

Kiwinote

---

### Post by gingermark on 2006-02-09
[QUOTE=Kiwinote]Applications > System tools > Applications Menu Editor
Find mplayer => view properties => make sure that the command that is there works in the terminal, if not locate mplayer and and make new command. In my case the command is "gmplayer"

Kiwinote[/QUOTE]
I believe these are GNOME instructions.

In KDE: K Menu-->Multimedia, then right-click on MPlayer and select "Edit Item". The Menu Editor should then open at the MPlayer entry. You can then follow Kiwinote's instructions. (ie make sure the command works in the terminal, or just change it to "gmplayer").

---

### Post by krcm on 2006-02-10
The command is already set to gmplayer.
how do I check that it works in the terminal?
I tried ticking off the box where terminal is mentioned in the menu editor, (it's in dutch on my pc, I don't know exactly what it says in english). When I then tried to open mplayer again, a terminal window popped up, but it closed after 2 sec so I couldn't see what happened here.
I added a snapshot (I reset the editor after I tried with the ticked off terminal thing) so maybe you can tell me what I have to change.
thx
An

---

### Post by gingermark on 2006-02-10
Go K-Menu-->System and run "Konsole". This will open a terminal window. type 'gmplayer', press enter, and then post the output here, and maybe someone can help you further.

Is odd though.

---

### Post by Kiwinote on 2006-02-10
[QUOTE=gingermark]I believe these are GNOME instructions.

In KDE: K Menu-->Multimedia, then right-click on MPlayer and select "Edit Item". The Menu Editor should then open at the MPlayer entry. You can then follow Kiwinote's instructions. (ie make sure the command works in the terminal, or just change it to "gmplayer").[/QUOTE]

Yes, they are, hadn't noticed that this was in the kubuntu section

Kiwinote

---

### Post by krcm on 2006-02-12
this is the result:


MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Intel  1501 MHz (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf
Warning unknown option skin at line 50
Reading config file /home/an/.mplayer/config
MPlayer was compiled WITHOUT GUI support.
Reading /home/an/.mplayer/codecs.conf: Can't open '/home/an/.mplayer/codecs.conf': Onbekend bestand of map
Reading /etc/mplayer/codecs.conf: 73 audio & 180 video codecs
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
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
 up or down       seek backward/forward  1 minute
 pgup or pgdown   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 z or x           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *


grtz
An

---

### Post by gingermark on 2006-02-12
Did you compile your own version of MPlayer or install it from the repositories. Looks like you need the GUI package anyways, in addition to the player package (and I think the 686 package is most appropriate).

I'm not sure about those audio codec errors though, hopefully someone else can help there.

Sorry.

---

