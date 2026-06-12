---
title: "Quake 3 Arena Demo on Ubuntu 9.04: &quot;Badmatch&quot; error"
date: 2009-09-29
forum: Game Specific Discussions
---

### Post by LeDechaine on 2009-09-29
Yes, i've managed to install this demo on Ubuntu 9.04!
(But the game still doesn't start.)

See this as a "howto" in the making, while I try to get the game to work ;)

First, i've grabbed the demo:
[ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3ademo-1.11-6.x86.gz.sh](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3ademo-1.11-6.x86.gz.sh)

Then, i've put it in a temporary "q3demo" directory on my desktop.

Then:
**tail -n +165 linuxq3ademo-1.11-6.x86.gz.sh | gzip -cd | tar xf -**
..is the command I needed, found [here]("http://blog.janus.cx/archives/268-Quake-3-Demo-on-Linux,-installation-problem-and-solution.html") (The comment).

Then:
**sudo bash ./setup.sh**
..shown the installation GUI (WOOHOO! :D)

And everything installed.
*Joy*, but my problems are not over yet.

I had this "Can't find default.cfg" problem.. solved by running "q3demo" directly from the directory
**ledechaine@QuadDamage:/usr/local/games/q3demo$ ./q3demo**
(Yes, my machine is really named "QuadDamage" ;))

Well, now, after a black screen, i'm having that X "badmatch" error...

> Q3 1.11 linux-i386 Dec  4 1999
----- FS_Startup -----
Current search path:
/home/ledechaine/.q3a/baseq3
./baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ledechaine/.q3a/demoq3
./demoq3/pak0.pk3 (1387 files)
./demoq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: QuadDamage
IP: 127.0.1.1
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
[B]XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  37
  Current serial number in output stream:  40[/B]


And i'm stuck here.
Don't know if it can help, but my graphics card is an **ATI Radeon 9250**.

And, oh, don't know if there's a way to set the resolution in command line? That would help, because after it crashes, my 19" screen stays at 640x480.. fugly! ;)

---

### Post by Giblet5 on 2009-09-29
I've never tried to set it up, but the problem is likely due to that 640x480 (mode=3 in default.cfg) resolution. Q3 does weird stuff during startup. It may be forcing the screen to 640x480, then requesting a new 800x600 window: instant Badmatch error.

Take a look at id's documentation and find out what mode=X value is appropriate for your monitor (probably not available, but at least higher res).

You may have to run it in windowed mode (not fullscreen) if your monitor isn't ... cooperative ... and there are a ton of options you can set in default.cfg to get the look that's best.

Prefer UT, m'self. Plus, it just works on linux.

Nice 'puter name. :)

---

