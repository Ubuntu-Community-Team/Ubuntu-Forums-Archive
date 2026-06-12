---
title: "Network printer settings are saved but don't work in kde"
date: 2008-01-03
forum: Desktop Environments
---

### Post by Iskendar on 2008-01-03
I recently installed an HP 2605DN network printer. I used the kde printer wizard (gutsy), which seeminly worked like a charm, to change the default tray and paper type (letter ->a4). Did the same on the printer itself (it has a web interface). Now everything indicates that the settings are correct: the kde printer setup, the "properties" printing window in kpdf, the printer's webconfig page, cups' webinterface at [http://localhost:631](http://localhost:631), all state A4 at Tray2 with duplex on.
When I actually try to print a pdf file, the printer shows an error message stating that I should insert letter paper. Strange. So I tried firing up acrobat reader, looking at the printer settings there, and what do you know: letter, Tray 1 and duplex off, the default. Changing these settings to the desired ones allowed printing, but I have to do it every time.
So now I suspect that for some strange reason, even though all config options point out that I have changed the settings, in reality the system still uses the default settings. Very annoying. It is a (k)ubuntu problem, my girlfriend's windows laptop has no problem printing on the network printer.  Any suggestions?

---

### Post by Iskendar on 2008-01-05
I checked some more options: /etc/papersize is set correctly at A4, and I tried the suggestion from [this thread]("http://ubuntuforums.org/showthread.php?t=424230&highlight=print+letter") by putting 
```
LC_PAPER="POSIX" 
```
in /etc/environment. I found some threads on similar printing problems using openoffice, but that works fine for me. Printing a test page from the kde control center works fine too. So I guess it's purely a kpdf problem. Any suggestions?

---

