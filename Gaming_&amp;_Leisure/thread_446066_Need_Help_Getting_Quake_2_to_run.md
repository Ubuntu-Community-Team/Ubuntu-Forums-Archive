---
title: "Need Help Getting Quake 2 to run"
date: 2007-05-16
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-05-16
I installed quake2 running the command        sudo aptitude install quake2 in the terminal

so now ive tried running it with the terminal and i got the warnings below


ubuntu@ubuntu:~$ quake
bash: quake: command not found
ubuntu@ubuntu:~$ quake2
***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.   

   See for an possibly non-exhaustive list of issues:
   [http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html](http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html)
   [http://www.r1ch.net/stuff/r1q2/](http://www.r1ch.net/stuff/r1q2/)
   [http://bugs.debian.org/280573](http://bugs.debian.org/280573)

*******************

Do you understand the security implications of continuing?
yes
QuakeIIForge 0.3
using /home/ubuntu/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't load pics/colormap.pcx
ubuntu@ubuntu:~$ 

So does anyone know what my problem is and how i can fix it?

---

### Post by gorkur on 2007-05-16
You need the game data files :)

---

