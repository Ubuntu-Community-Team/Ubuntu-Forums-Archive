---
title: "Need help installing warcraft 3 from .exe's from battle.net"
date: 2011-01-28
forum: Gaming &amp; Leisure
---

### Post by CoorsMan on 2011-01-28
Hey guys first post here! Installed ubuntu 10.10 and I'm very impressed. It's clean and I doubt I'll go back to windows for a good while as I'm learning pretty quickly here. Alright so here we go.
 
 I'm trying to install warcraftIII roc and tft from .exe installers from battle.net. When I try to run the installer's it gives me this error.

Archive:  /home/levi/Downloads/Downloader_Warcraft3_Reign_of_Chaos_enUS.exe
[/home/levi/Downloads/Downloader_Warcraft3_Reign_of_Chaos_enUS.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/levi/Downloads/Downloader_Warcraft3_Reign_of_Chaos_enUS.exe or    /home/levi/Downloads/Downloader_Warcraft3_Reign_of_Chaos_enUS.exe.zip, and cannot find /home/levi/Downloads/Downloader_Warcraft3_Reign_of_Chaos_enUS.exe.ZIP, period.

 I have wine installed and I'm not too sure what to do from here. I'm not installing these from cd's I'm installing from exe's from battlenet which are tied to my cd keys. Any help is appreciated. Thanks guys. 

 -Levi

---

### Post by DoktorSeven on 2011-01-28
You need to install Wine and associate .exe files with /usr/bin/wine -- for some reason it thinks of them as ZIPs by default, apparently.

Or you can open a terminal and do something like:

[b]cd /home/levi/Downloads/
wine Downloader_Warcraft3_Reign_of_Chaos_enUS.exe[/b]

---

### Post by CoorsMan on 2011-01-28
> **DoktorSeven said:**
> You need to install Wine and associate .exe files with /usr/bin/wine -- for some reason it thinks of them as ZIPs by default, apparently.

Or you can open a terminal and do something like:

[b]cd /home/levi/Downloads/
wine Downloader_Warcraft3_Reign_of_Chaos_enUS.exe[/b]

 Thanks for replying Dok,
  I don't see where I choose to associate wine with .exe's. I tried to right click and open with wine. I tried to open wine configuration and tried to add the exe as an application but no dice. Can you please give me a little extra walk through?

---

