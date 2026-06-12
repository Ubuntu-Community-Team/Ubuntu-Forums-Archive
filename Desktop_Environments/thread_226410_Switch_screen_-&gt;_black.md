---
title: "Switch screen -&gt; black"
date: 2006-07-31
forum: Desktop Environments
---

### Post by jonathanhayward on 2006-07-31
When I run VMware and hit control-alt-f9, about one time in three I get a black screen. When this has happened, I haven't found anything that lets me get back to a normal window. (I've mainly tried repeatedly hitting control-alt-f7 to get to X and control-alt-f1 to get a plain vanilla terminal.) Similar behavior happens with Basilisk II fullscreen: I frequently get what looks like a snow crash.

I do not experience any trouble switching between virtual terminals: only when going fullscreen on VMware and BasiliskII.

What can I do to ensure that my system loads the intended window properly, or barring that, that I can get out if it doesn't work? Is there any way in Basilisk II to go between full screen emulation and regular X windows?

Thank you,

---

### Post by jonathanhayward on 2006-08-03
Correction: This also does happen without switching terminals. I haven't isolated the cause, but my computer has given an Inescapable Black Screen and turning off the screensaver apparently solves the problem.

---

### Post by jonathanhayward on 2006-08-03
Help? Anyone? This is really nasty. Is there an easy to migrate to a different version of X or the relevant software so I'm not changing my behavior every day to circumvent this bug?

---

### Post by jonathanhayward on 2006-08-06
Note on the logs: I looked through, and the last line after a crash was "Ok, leaving now..." 

(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fec18)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xffff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Ok, leaving now...

The full logs are at [http://haywardfamily.org/jonathan/xorg_log.txt](http://haywardfamily.org/jonathan/xorg_log.txt) . Do these logs, and in particular the "Ok, leaving now..." explain why I would be getting a black image on the screen (displaying black; it isn't black the way it is when the computer is turned off).

---

