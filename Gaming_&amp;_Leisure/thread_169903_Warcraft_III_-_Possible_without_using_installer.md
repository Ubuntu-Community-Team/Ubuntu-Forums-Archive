---
title: "Warcraft III - Possible without using installer?"
date: 2006-05-03
forum: Gaming &amp; Leisure
---

### Post by Pulani on 2006-05-03
Hi

I'm running 5.10 and just wondering if it's possible to get war3 running without using the installer.

I copied the game from my windows parition straight over to ~./wine/drive_c/ and proceeded to try running it with wine.

I get this error message saying the game can't find my war3 cdkey.

Is there a possible workaround for this or must I resort to using the installer?
Thx in advance! :P

---

### Post by MBro on 2006-05-04
did you try just mounting your xp drive and running it straight from there?  It probably searches your windows reg for the cd key.

---

### Post by Clement on 2006-05-07
i have tryed this method and it doesn"t work :)
I am on dapper and i have installed it with wine(0.9.9) roc then tft but it doesnt work until i upgrad to the latest version of war3 1.20d

dont forget to write CD-ROM in advanced>type for your cdrom after an autodetection in wine cfg !

now it works well except for the resolution ( [http://www.ubuntuforums.org/showthread.php?t=171191](http://www.ubuntuforums.org/showthread.php?t=171191))

---

### Post by czhu on 2006-06-11
I'm running 1.20d on dapper with wine using the copy method.
Just like in windows, if you use this method you gotta fix up the registry settings a bit, pointing the ProgramPath and InstallPath + ProgramPathX InstallPathX (if you're using FT) to the directory ur war3 resides in (mine is C:\war3\)
Assuming you still have windows, u can export these keys from win regedit easily, they're in HKEY_CURRENT_USER\Software\Blizzard Entertainment i think

i'm using the latest version of wine 0.9.15 and using nocd patch

---

