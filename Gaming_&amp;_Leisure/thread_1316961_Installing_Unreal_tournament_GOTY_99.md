---
title: "Installing Unreal tournament GOTY 99"
date: 2009-11-06
forum: Gaming &amp; Leisure
---

### Post by Majin Zero on 2009-11-06
using ubuntu 9.10 64bit

Ok, I enter:

./unreal.tournament_436-multilanguage.goty.run


and this is what outputs:

error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


I followed a guide and manually copied some files from an extracted i386 deb package to my lib32 folder, and that didn't solve the issue.

I tried copying the files to my /lib folder, and I got a different error output:

error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS32

any ideas?

---

### Post by Menthu_Rae on 2009-12-11
Try this from terminal (I'm installing it as I type this):

```
linux32 sh unreal.tournament_436-multilanguage.run
```

Thanks to this post by **msch**!

[http://ubuntuforums.org/showpost.php?p=4858603&postcount=6](http://ubuntuforums.org/showpost.php?p=4858603&postcount=6)

---

### Post by wardy277 on 2011-09-02
i appriciate that this is a old post but i am trying to get my copy of UNreal tournament to run on my ubuntu 11.04 x64 box. Every way i try i get the error from the original post
```

Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/xbmc/.setup18519: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

i have tried searching for libgtk-1.2.so.0 in various i386 deb (and even form rpms) but it keeps saying
```
/home/xbmc/.setup18288: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS32

``` 

i have even gone to the trouble of compiling gtk+1.2 as described at [http://aimbots.net/enemy-territory-cheats-linux/18509-how-ubuntu-9-10-karmic-koala-libgtk1-2-a.html](http://aimbots.net/enemy-territory-cheats-linux/18509-how-ubuntu-9-10-karmic-koala-libgtk1-2-a.html) which did work and i compiled and installed both glib and gtk (gtk as i386) but that didnt seem to do anything.

I have tried running it through linux32 but the same thing happens.

i cant believe its this complicated to get to work. When i try to run ut itself i get:
```

Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

```

looking up that error brung me to running the unreal.tournament_436-multilanguage.run script.

has anyone got Unreal tournament running on ubuntu 11.04 x64? Any help would be greatly appreciated.

---

### Post by Rustybolts on 2011-09-03
Would of been best starting your own thread!
Have you installed ia32-libs from the ubuntru software centre?
Also if its a specific lib that your still missing you need to download it and use a program called getlibs to install it. This thread here should help you do that [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by HolgerB on 2011-09-03
If you want to save your time and do not feel like tinkering around simply installing UT99 under WINE works also nicely. Set the renderer to OpenGL and you have close to no overhead although UT99 runs a blazing > 150 FPS on somewhat recent hardware.

Judge yourself:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=124)

This is of course only an option if you can live with running Windows software under Linux even though an alternative exists :)

---

### Post by wardy277 on 2011-09-03
I have installed getlibs and ia32-libs but that didnt seem to help. running getlibs returned:
```
libgtk-1.2.so.0: libgtk1.2
The following i386 packages will be installed:
libgtk1.2
Continue [Y/n]? y
E: No packages found
libgtk1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

I have managed to get around the libgtk issue by symlinking a x11 version i founf in lib32 
/usr/lib/libgtk-1.2.so.0 -> /usr/lib32/libgtk-x11-2.0.so.0

then it aske for libglib so i used the following to get that:
```
wget http://cz.archive.ubuntu.com/ubuntu/pool/universe/g/glib1.2/libglib1.2ldbl_1.2.10-19build1_i386.deb

getlibs -i libglib1.2ldbl_1.2.10-19build1_i386.deb
```

now the installer runs (i hasd to add the -noexec to remove a "undefined symbol: GTK_TYPE_SPIN_BUTTON_UPDATE_POLICY" error:
linux32 bash ./unreal.tournament_436-multilanguage.run --noexec

well that didnt seem to do anything (no errors but no complete messages or anything)

but running ut and linux32 ut just returned the same errors:
```
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

```

I didnt try it through wine but i got a "serious error" message, it would be nice to get native Linux version of this working.

Has anyone actually got Unreal tournament running on Ubuntu 11.04 x64 or am i wasting my time?

---

### Post by HolgerB on 2011-09-03
> **wardy277 said:**
> I didnt try it through wine but i got a "serious error" message, it would be nice to get native Linux version of this working.

Has anyone actually got Unreal tournament running on Ubuntu 11.04 x64 or am i wasting my time?
May I ask why you haven't tried UT99 GOTY under WINE ?

It runs perfectly here (U10.04 x64 though). You know in Linux there are often situations where you can choose the pragmatic approach (WINE = instantly works) or the "I want to do it native" (using native installers = "wasting" / spending a lot of time). 

I have often experienced issues with games which are available as Linux native but I ended up simply installed the Windows counterparts in WINE.

Using Windows games under WINE doesn't give me bad dreams either. 

Decide yourself...

---

### Post by wardy277 on 2011-09-03
I would have thought native woud be better. I'll give wine another go. Thanks for your help

---

### Post by HolgerB on 2011-09-04
> **wardy277 said:**
> I would have thought native woud be better. I'll give wine another go. Thanks for your help
You are welcome !

Of course native is / should be better in terms of performance, compatibility, etc

The mayor disadvantage I have run into are either external dependencies (native game port has been build ages ago and the required libs might not be available anymore, native port uses sound sub-system XY but your distrib uses AB) or that the native installer is build for a certain windows version of the games (UT99 vs. UT99 GOTY, UT2k4 vs. Unreal Anthology).

Using Windows games under WINE might have the disadvantage that they run slower compared to their native pendant but 
a) you will most likely not have any issues with the native sound system
b) not miss any dependency since the Windows games already brings all required lib or the are emulated via WINe
c) are not bound to a specific version of the installer.

If you check out my old crappy video you will notice that UT99 runs flawlessly under WINE: [http://www.youtube.com/watch?v=HGiOk239koM](http://www.youtube.com/watch?v=HGiOk239koM)

To me making games run natively might make sense if they run flawlessly in a few minutes or if you like to tinker around but for the pure purpose of playing the games I always check out WINEs AppDB first and try to give WINE a go.

This will of course hurt the heart of each open-source / Linux enthusiast but I am gamer in the first place and Linux user in the second 
:guitar:

---

