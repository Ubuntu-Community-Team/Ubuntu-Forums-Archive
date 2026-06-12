---
title: "Zuma deluxe with Wine"
date: 2006-12-15
forum: Gaming &amp; Leisure
---

### Post by Mizipzor on 2006-12-15
Hi!

Im trying to get Zuma to work. 

* I run the installer with wine.
* Change the install location to /home/user/games/zuma.
* Press "Install".
* Get an error saying the Zuma.exe could not be created (although the file shows up in that folder).
* I go into the folder and try to run Zuma.exe with wine.
* It says it needs some ActiveX controller for Firefox which isnt installed and asks if it should do it automatically (I thought this was a standalone game? It is on Windows at least, cant see where it needs firefox plugin).
* I press "Yes" but the same box pops up again.
* After pressing "Yes" a couple of times I get something that looks like a Winrar selfextractor.
* I dont know what it is, but it was called Autopatch/Patcher or somthing so I just press extract and let it do its work.
* Wine exits so I hoped that something was updated but when I run Zuma.exe with wine again the same box pops up.

So there Im stuck. I couldnt find much on the forums on Zuma. Some posts but no hands-on tips. 

This is my first time using wine to so Im unsure what to try now. Any help is greatly appriciated. :)

---

### Post by bobpaul on 2007-02-28
Looks like people are having luck with [newer versions of wine]("http://appdb.winehq.org/appview.php?iVersionId=2424"). In fact, someone tested it on Debian Etch on wine 0.9.25, and someone had it on Suse with 0.9.29. I notice the wine in Fiesty is 0.9.30, so maybe?

> * It says it needs some ActiveX controller for Firefox which isnt installed and asks if it should do it automatically (I thought this was a standalone game? It is on Windows at least, cant see where it needs firefox plugin).

I just installed it using a VNC link to my Fiesty box at home and it seemed to install fine. When I try to run it I'm presented with an empty "Buy Zuma Delux" window. This probably contains an embedded internet explorer window (if you were on windows). This might explain why you saw the thing about the Firefox ActiveX stuff. I really need to get back to work, so I'll try more later.

> * I run the installer with wine.
* Change the install location to /home/user/games/zuma.
I think it's generally best to let apps install to "C:\program files\" or ~/.wine/drive_c/Program\ Files/ 

If you want to keep your apps in seperate wine "bottles" you can use the WINEPREFIX variable to set a new location. EG, you might use:
```
~ $ WINEPREFIX="/home/user/games/zuma" wine ZumaSetup.exe
``` to create a new wine settings folder to install zuma. Specifying the environment variable on the command line like that will make the change only effect the next executable. So if you later did 
```
~$ wine "C:\program files\dvdshrink\dvdshrink.exe"
``` it would load the dvdshrink stored in the ~/.wine settings folder, not the zuma one you just created. 

This isn't why your game didn't run, just a tip.

**Edit** You can play the in browser versions using IE6 on wine: [http://ubuntuforums.org/showthread.php?t=111597&highlight=zuma](http://ubuntuforums.org/showthread.php?t=111597&highlight=zuma)

---

