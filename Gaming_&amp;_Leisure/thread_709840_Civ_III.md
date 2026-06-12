---
title: "Civ III?"
date: 2008-02-27
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2008-02-27
Hi,

I'd like to know if someone is able to play Civilization III under Ubuntu with Wine or Cedega? If so, what version are u using?

Thanks

---

### Post by Vadi on 2008-02-28
This is what I found on appdb:

> Download wine-0.9.46 source.
* Apply the patch from: bugs.winehq.org/show_bug.cgi?id=3498
(I suggest that you remove the line FIXME(":stub\n"); at line 1806 in dlls/gdi32/freetype.c as well. Less prints.)
* Compile wine and install.
* Copy all 3 Civlization Complete CDs to your harddrive.
* Copy dsetup.dll from the directx/ directory to the same directory as setup.exe is located.
* Run winecfg and tell wine to load native windows dsetup.dll for setup.exe
* Run setup.exe
* It will still complain about missing dsetup.dll, but installation continues anyway.
* Install the game.
* Meanwhile, find a no-CD patch for Civilization Complete (Conquest v1.22)
* When asked for the "CD 1" give the path where you install from. The installation will just plainly quit afterward, but it is complete.
* Install the no-CD patch.
* Run regedit and set DirectDraw renderer to GDI:
HKEY_CURRENT_USER\Software\Wine\Direct3D\DirectDrawRenderer="gdi"
(Remember, this is a global setting, you might have to reset it to opengl for other games.)
* Run Civ3Conquest.exe with the custom build wine. 

---

### Post by taylorsmithereens on 2009-07-07
I'm not sure about this step:

Run winecfg and tell wine to load native windows dsetup.dll for setup.exe



While installing the first disk I got the following error message:

Feature transfer error
error: -1603 fatal error during installation
 

Any ideas would be very much appreciated.

---

### Post by Ascendaeus on 2009-07-25
hello peeps i am ver very new at all this lixun please helps myse stpud asces. i set up all the other games in the graphical manner and they installed fine but won't play halo worked for like 33 minutes annayingly laggy and morrowind gives me error number 256 when i go to play it but installed fine. fallout three the same. but civ 4 doens't evin rspnd whin i clik on the exe,.. like the other ones. harumph. i'm stupid. help me

---

### Post by lestatto on 2009-07-25
My Civilization 4 works pretty nice, just crunching a bit when map is traded. It should work almost flawlessly on new Wine.
More info : [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514)
Cheers.

---

