---
title: "Game Mxx Payne"
date: 2007-05-25
forum: Gaming &amp; Leisure
---

### Post by burt_57 on 2007-05-25
I am tired of trying to make that game work in ubuntu/i386 lates version.
I have tried lot of suggestion made in these forum , but no luck.
i use this program " max.payne_105-english-2.run
[http://liflg.org/?page=cat&catid=1](http://liflg.org/?page=cat&catid=1)
It does the install but I get this message saying
Local not supported by C library.
It does created a folder call maxpayne  with all files in it and folders.
But when I go to play it ......... it is a no go.

yours truly Burt 

eg: am getting to old for this  :D

---

### Post by Sockerdrickan on 2007-05-25
Just install retail with wine and boom, you are done.

---

### Post by burt_57 on 2007-05-26
> **Tux0r said:**
> Just install retail with wine and boom, you are done.

What do you mean by retail?
I have try with Wine so many time and it will not work :(

---

### Post by DoktorSeven on 2007-05-26
Run winecfg, make sure your cdrom drive is in the Drives tab (/media/cdrom usually).
Mount Max Payne CD.
Start setup with **wine d:\setup.exe** (or whatever the installer is called)
Download the maxpayne1-05patch.exe (search for it) and run it with Wine to patch the game to latest version.
from terminal **cd ~/.wine/drive_c/Program\ Files/Max\ Payne **
then **wine MaxPayne.exe**

If you have trouble running it because it asks for the CD, the CD protection might not work and you'll have to look for a way to bypass that (don't ask about that here, but there are places you can get such a thing).

It works perfectly here.

---

### Post by burt_57 on 2007-05-26
> **DoktorSeven said:**
> Run winecfg, make sure your cdrom drive is in the Drives tab (/media/cdrom usually).
Mount Max Payne CD.
Start setup with **wine d:\setup.exe** (or whatever the installer is called)
Download the maxpayne1-05patch.exe (search for it) and run it with Wine to patch the game to latest version.
from terminal **cd ~/.wine/drive_c/Program\ Files/Max\ Payne **
then **wine MaxPayne.exe**

If you have trouble running it because it asks for the CD, the CD protection might not work and you'll have to look for a way to bypass that (don't ask about that here, but there are places you can get such a thing).

It works perfectly here.
I have the CD ...I never cheat or use software which are ot legal....thank for advise... will let you know if that work :D

---

### Post by burt_57 on 2007-05-28
> **DoktorSeven said:**
> Run winecfg, make sure your cdrom drive is in the Drives tab (/media/cdrom usually).
Mount Max Payne CD.
Start setup with **wine d:\setup.exe** (or whatever the installer is called)
Download the maxpayne1-05patch.exe (search for it) and run it with Wine to patch the game to latest version.
from terminal **cd ~/.wine/drive_c/Program\ Files/Max\ Payne **
then **wine MaxPayne.exe**

If you have trouble running it because it asks for the CD, the CD protection might not work and you'll have to look for a way to bypass that (don't ask about that here, but there are places you can get such a thing).

It works perfectly here.
I get this error now:
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

---

