---
title: "Frustrating Ubuntu stability problems"
date: 2005-07-28
forum: Desktop Environments
---

### Post by Statik on 2005-07-28
I'm getting frustrated with an odd problem with Ubuntu. I'm having applications, often when I go to save documents, suddenly closing without any notice. No errors are produced, no warnings are given. This originally was happening with Firefox alone, especially when opening a new tab. Then with saving files/links from firefox. Now it happens with other text files (using GEdit). Any ideas on what could be causing it? Or a way I can test for it?

Statik

---

### Post by varunus on 2005-07-28
This is very strange, as I've never experienced any of the issues you're talking about.  Try opening gedit and firefox from a terminal and reproducing the crashes; do they produce error messages in the terminal?

---

### Post by strikeforce on 2005-07-28
I had a similar issue when I transferred my bookmarks from my winxp partition to my linux partition.

Make sure the permissions are correct.

---

### Post by Statik on 2005-07-29
well, for some reason, moving the computer off of the mini KVM I had seems to have made things more stable. No more trouble as yet. Now if I can get WineX to install properly . . . CVS version that is. Same error all the time:
> make[2]: Entering directory `/root/temp/winex-stable/winex/dlls/x11drv'
gcc -c -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__  -D_REENTRANT -I/usr/X11R6/include -o desktop.o desktop.c
desktop.c: In function `GetDisplayModeCount':
desktop.c:179: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:179: error: (Each undeclared identifier is reported only once
desktop.c:179: error: for each function it appears in.)
desktop.c:186: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `GetRealMode':
desktop.c:196: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:199: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `X11DRV_EnumDisplayModes':
desktop.c:217: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:239: warning: implicit declaration of function `X11DRV_XF86VM_GetCurrentMode'
desktop.c:256: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `X11DRV_ChangeDisplayMode':
desktop.c:285: error: `xf86vm_allow_mode_changes' undeclared (first use in this function)
desktop.c:317: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:319: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c:356: warning: implicit declaration of function `X11DRV_XF86VM_SetCurrentMode'
make[2]: *** [desktop.o] Error 1
make[2]: Leaving directory `/root/temp/winex-stable/winex/dlls/x11drv'
make[1]: *** [x11drv/libx11drv.so] Error 2
make[1]: Leaving directory `/root/temp/winex-stable/winex/dlls'
make: *** [dlls] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: GetWineX.sh) 

Any ideas?

Statik

---

### Post by Statik on 2005-08-05
Wow, just wow. On a whim I decided to run a memory checker on my RAM. Just on the odd chance it might have a bad bit somewhere that was causing my occasional lockups. . . It was about 30% bad. Incredible. Usually, windows wouldn't even install with errors like that. Linux installs and only presents the occasional instability. Incredible. Well, I'll replace the RAM monday and my problems should be solved. Thanks for the help guys.

Statik

---

### Post by neighborlee on 2005-08-06
[QUOTE=Statik]Wow, just wow. On a whim I decided to run a memory checker on my RAM. Just on the odd chance it might have a bad bit somewhere that was causing my occasional lockups. . . It was about 30% bad. Incredible. Usually, windows wouldn't even install with errors like that. Linux installs and only presents the occasional instability. Incredible. Well, I'll replace the RAM monday and my problems should be solved. Thanks for the help guys.

Statik[/QUOTE]

I had similar problems as well and found bad ram via memtest...is that what you used also ?

my problem is my system uses that dain expensive  rambus crud so I may have to get entirely new computer LOL..gee thanks dell ( never buying dell again )

l8r

---

### Post by Statik on 2005-08-06
heh, yeah, I've got a client with ram bust ram. Good stuff . . . when it works. Probably worth your while to turf it. It's about 3 times more expensive than the new RAM and I don't think you can get the newer sizes or the equivalent speed grades now. You can probably get a new CPU, Motherboard and RAM for the same price as replacing that RAM.

Statik

---

