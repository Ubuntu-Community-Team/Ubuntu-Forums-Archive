---
title: "Alice, Diablo, Emperor, Star Trek"
date: 2006-04-17
forum: Gaming &amp; Leisure
---

### Post by RAV TUX on 2006-04-17
:confused: :confused: :confused: :confused:

I am wondering if there is any way to get a few games to play on Ubuntu...

American McGee's: Alice 

Blizzard Entertainment's: Diablo I and II, & Lords of Destruction

Sierra's: Emperor, Rise of the Middle kingdom

Raven Games': Star Trek Voyager: Elite Force

---

### Post by Perfect Storm on 2006-04-18
American McGee's: Alice, Blizzard Entertainment's: Diablo I and II, & Lords of Destruction knows woorking with cedega (I have them myself) [http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by RAV TUX on 2006-04-18
[QUOTE=Artificial Intelligence]American McGee's: Alice, Blizzard Entertainment's: Diablo I and II, & Lords of Destruction knows woorking with cedega (I have them myself) [http://www.transgaming.com/](http://www.transgaming.com/)[/QUOTE]

Thats great ! Is anybody able to use Emperor or Star Trek ?

:mrgreen:

---

### Post by bakie on 2006-04-18
i can play diablo 2 and lord of destruction with wine.
dont know or the other games will work on wine

---

### Post by Praetorian on 2006-04-18
According to the wine site Emperor and Star Trek runs flawless under wine:
[Star Trek ]("http://appdb.winehq.org/appview.php?versionId=576") and [Emperor ]("http://appdb.winehq.org/appview.php?appId=2736")

---

### Post by sYs^ on 2006-04-18
Is Diablo working on Battle.Net too?

---

### Post by wylfing on 2006-04-18
Every part of Diablo II and LOD work perfectly under wine and/or cedega. The only thing that can be an irritant is the install process where you have to swap CDs back and forth.

Diablo I installs without problems for me, but getting it to play is problematic.

---

### Post by Griff on 2006-04-18
I currently play Diablo II: LOD on bnet with no problems.  After installing exactly like it shows under wine 0.9.10 (it's easier than it looks) I just downloaded the 1.11b patch from blizzard's diablo page and installed that with wine.  I have zero issues with it.  I actually prefer playing it on linux since you can change workspaces without that annoying 'flash' you get when the monitor changes resolutions like in windows.
Enjoy.  :D
[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49)

---

### Post by sYs^ on 2006-04-18
Wow, that sounds nicely, then I think I'll try it, Diablo 2 rulz :>

---

### Post by RavenOfOdin on 2006-04-18
Ahh. . .Diablo and Diablo 2.

Those bring back some rather screwed-up memories.

---

### Post by trotski on 2006-04-18
Alice and Diablo II both run for me under Wine rather well. I use a NO-CD crack for Alice due copy protection issues.  They are some of the best performing games under Wine.

Yes, life with DII on Bnet back in the day was a screwed up time.

"HUK HUK SHOW ITAM"
"lag made me lose 8mil exp!"
"Ooh, rollback didn't go back far enough to save all my 1337 items!"
"Hrm, what Cow King?  All I see is a black wall... oh... I must be dead then."

---

### Post by heyilikeyoursweater on 2007-02-09
I get this error when I run Star Trek:

```
ST:V EF v1.10 win-x86 Oct 26 2000
----- FS_Startup -----
Current search path:
C:\Program Files\Raven\Star Trek Voyager Elite Force\baseef\pak1.pk3 (67 files)
C:\Program Files\Raven\Star Trek Voyager Elite Force\baseef\pak0.pk3 (19069 files)
C:\Program Files\Raven\Star Trek Voyager Elite Force/baseef

----------------------
execing default.cfg
couldn't exec efconfig.cfg
couldn't exec autoexec.cfg
...detecting CPU, found Intel Pentium IV

------- Input Initialization -------
Skipping check for DirectInput
Joystick is not active.
------------------------------------

------- Force Feedback Initialization -------
...inhibited, not initializing

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
execing perfect.cfg
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Working directory: C:\Program Files\Raven\Star Trek Voyager Elite Force
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using desktop display depth of 24
...calling CDS: ok
...registered window class
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 24, 24, 8 )
...-1 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 24, 24, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...setting mode 3: 640 480 FS
...using colorsbits of 16
...calling CDS: ok
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 16, 16, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 16, 16, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
...assuming '3dfxvgl' is a standalone driver
...initializing QGL
...WARNING: missing Glide installation, assuming no 3Dfx available
...shutting down QGL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLW_StartOpenGL() - could not load OpenGL subsystem



```

---

