---
title: "Enemy Terrirory won't start"
date: 2009-02-14
forum: Gaming &amp; Leisure
---

### Post by n3had on 2009-02-14
```
et
```

gives this

```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/tru3m0sl3m/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: wrong ELF class: ELFCLASS64
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```


There was a suggestion to add "libGL.so.1" to the game folder.. Prior to this it used to ask for that file now as i have pasted it from /usr/lib .. i got the above error.. is it related to 64bit libGL? .. i Don't have 32bit one.. anyways running jaunty 64

Any help would be appreciated

n3had

---

### Post by tkmn on 2009-02-14
There is a guide in the top sticky thread.

"wrong ELF class" means it wants a 32 bit library
I think you need to install **ia32-libs** atleast.

---

### Post by Cresho on 2009-02-14
Here is my installation notes.

```
install this if 64 bit os system
sudo apt-get install ia32-libs






chmod +x ETQW-client-1.5-full.x86.run
./ETQW-client-1.5-full.x86.run

Now go to System->Preferences->Advanced Desktop Effects Settings. Click on "General Options", and un-check "Unredirect Fullscreen Windows". This will fix some bugs with input and snapping to windowed mode. You may have better performance if you disable any GL desktop effects (Compiz) entirely.
```

Mind you I have never ran this in windowed mode but I can't find anything different or can't recall If I needed to do anything special to get it running.  I did create a special script to auto disable compiz and re-enable.  I noticed if I jump into too many games, the game locks up but ctrl+alt+backspace and log back in reveals etqw running in the background so I kill it in system monitor.  THen I can reload game.  Other than this, everything works including mic.

are you running 64bit?  I am on 32 bit hardy heron.

---

### Post by n3had on 2009-02-14
Yes i am running jaunty jackelope 64 bit.. I've installed it with no errors using the guide in the sticky thread.

now when i tried this
```
sudo apt-get install ia32-libs
```
got
```
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

```

EDIT: btw its Wolfenstein: Enemy Territory

installed using [http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy](http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy)


EDIT2: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.

```

and i removed libGL.so.1 from the game directory.. now i get this

```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/tru3m0sl3m/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

IS it because of the patch ET 2.60b??

---

### Post by Cresho on 2009-02-15
well, what can I say, you are running a very beta ubuntu!  Expect delays.  did you fix your repositories to main server in software sources?  Also, did you try putting a check on all minus source code?

then in terminal do a ```
sudo apt-get update
sudo apt-get upgrade
```

then

```
sudo apt-get install ia32-libs
```


Just going through those steps.  Wolfenstein also runs on my pc just fine.

---

### Post by Perfect Storm on 2009-02-15
The Guide havn't been tested with jaunty jackelope 64 bit. It's properly a bug with Ubuntu 9.04 as it doesn't happen in 8.10


It's recommandable to use a stable version of OS, you might consider it.

---

### Post by n3had on 2009-02-15
> **Artificial Intelligence said:**
> The Guide havn't been tested with jaunty jackelope 64 bit. It's properly a bug with Ubuntu 9.04 as it doesn't happen in 8.10


It's recommandable to use a stable version of OS, you might consider it.

thankyou once again. I've posted in jaunty section. There are some out there who have no problem with ET. Anyways i'll stick to Urban terror for now :)

---

### Post by Holmen on 2009-02-15
I also get this error - but with Enemy Territory Quake Wars.

---

### Post by Perfect Storm on 2009-02-15
Just remember to bug report it to the ubuntu devs, so they can fix this.

---

### Post by Dizzle7677 on 2009-02-17
You have to install the 32-bit Video driver files. If you install the nVidia binaries there's an option to install the 32-bit version alongside 64-bit. Dunno about ATI's drivers ....

---

