---
title: "Problems with Alien Arena online"
date: 2010-04-03
forum: Gaming &amp; Leisure
---

### Post by emaloli on 2010-04-03
Hi!

I've installed both Alien Arena and Alien Arena Browser Tool, but when i try to join a server it starts the black screen with the acid green script, saying it's downloading files (slow as hell) on some /maps/..... or similar and saying it cannot find other files (.bm2?) and it quits the game.

is there a package or lib I can download once for all?
I couldn't find one on the official site! 

thanks!
ema

---

### Post by Perfect Storm on 2010-04-03
First it would be a good idea to tell us how you install it (step by step if necessary).
Next, run it via the terminal and see if any output is made that can be useful.

---

### Post by emaloli on 2010-04-04
I just used the "ubuntu software center" tool I found under Applications.
I'm running Ubuntu 9.10

The single-player game is working ok, but if I try to join a server I get (on the terminal):

> 
Dismal Outpost
Server does not have file players/slashbot/tris.md2.
Server does not have file players/commander/tris.md2.
Server does not have file players/slashbot/w_blaster.md2.
Server does not have file players/commander/w_blaster.md2.
misc/headshot.wav is a stereo sample
*** buffer overflow detected ***: /usr/lib/games/alien-arena/crx.sdl terminated


then 

> 
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x493ed8]
/lib/tls/i686/cmov/libc.so.6[0x492f10]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0x492284]
/usr/lib/games/alien-arena/crx.sdl[0x80ba182]
======= Memory map: ========
00110000-0023a000 r-xp 00000000 08:01 2986       /usr/lib/libX11.so.6.2.0
0023a000-0023b000 ---p 0012a000 08:01 2986       /usr/lib/libX11.so.6.2.0
0023b000-0023c000 r--p 0012a000 08:01 2986       /usr/lib/libX11.so.6.2.0



with 50 lines of this memory map thing

and at last

> 
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xa4
  Serial number of failed request:  88
  Current serial number in output stream:  91


---

### Post by Perfect Storm on 2010-04-04
Which video card do you have?


> X Error of failed request: BadValue (integer parameter out of range for operation)

This could mean that AA is starting up in a resolution that your computer don't support or is not set up for.

---

### Post by emaloli on 2010-04-04
I have a (lspci | grep -i vga)

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

It's quite old.. but how come i play allright on singleplayer?

I tried to change the video options to 800-640, but the game shuts and I get this 

> 
======== CRX Initialized ========

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xa4
  Serial number of failed request:  85
  Current serial number in output stream:  88


---

### Post by Perfect Storm on 2010-04-04
You may try to get the latest of Alien Arena. It could be that you're trying to connect with an older version which have a bug. And mostly other players uses the latest. Try check playdeb.net and see if there's a package available.

---

### Post by emaloli on 2010-04-04
Thanks a lot!!
I'll try now


seems that i've allready installed the current version... 
thank for the hint, anyway!

---

### Post by Irritant on 2010-04-05
Nah, you're definitely using an old version, I can tell by the missing files and the "headshot.wav is a stereo sample".  Somebody should really update where ever this is getting installed from, if I recall it's a version that's over 2 years old.

---

