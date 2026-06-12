---
title: "Wine Steam Error please help"
date: 2006-07-04
forum: Gaming &amp; Leisure
---

### Post by battleroyalex on 2006-07-04
I've been trying to figure this out for over 5 hours now. I will give you a run through of all my problems.

First it wouldn't install past 26% i read up as it being a known error and to just keep trying, it finally worked.

Then I couldn't get on the login menu. Trying to command line run it I would get a bunch of errors. Running it by clicking the steam Icon I would get "Module cannot load Bin/Vgui2.dll" yes the dll file was there.

After bringing in files from my windows version of steam I got it to the login menu. I tried logging in. After it says "connecting to account name" I get this error:

```
ccerr:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod
```

When I try clicking on the icon I get the same VGUI2.dll error. I don't know what to do anymore :(

---

### Post by HAARP on 2006-07-04
Download [Cedega's mozcontrol](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz) and extract it into **C:\Program Files\mozcontrol** of your wine. (eg. **/home/*username*/.wine/drive_c/Program Files/mozcontrol**)
In Terminal, type:
```
cd /home/*username*/.wine/drive_c/Program Files/mozcontrol
regsvr32 mozctlx.dll
```

Then make a script: (**steam.sh** for example)

```
#!/bin/sh
cd /home/*username*/.wine/drive_c/Program Files/Steam
WINEDEBUG="-all" wine Steam

```

Replace all paths with your own

Make it executable and launch it to start Steam. Have fun! :D

---

### Post by battleroyalex on 2006-07-04
OMG YES THANK YOU! IT WORKED! but now when I click launch game nothing happens :(

---

### Post by HAARP on 2006-07-04
Replace **WINEDEBUG="-all" wine Steam**
with **WINEDEBUG="-all" wine Steam -applaunch 10**

And see if it works. The number is the game to launch, you should be able to google up the corresponding number for your game. 10 is CS1.6

---

### Post by battleroyalex on 2006-07-04
ok I got CSS to launch it looks like theres a few video issues but still looks better than cs1.6.

The only problem is I can't connect to any of the servers. The server lists pop up but I can connect. I try to manually connect to them and it just times out :(

---

### Post by battleroyalex on 2006-07-04
Ok I got it working! Heres a screenshot:
[IMG]http://img296.imageshack.us/img296/7272/multiplayer6lv.jpg[/IMG]
Is there a way to fix the ultra bright textures? Is that a gfx driver problem or emulation? I have a 7800GTX I get around 200fps on windows.

---

### Post by Blacktalon on 2006-07-05
So, would you guys mind telling how I get wine and steam on my laptop and working....I am running Dapper Drake.


Thanks for any help you can provide

~BT

---

### Post by Craftkiller on 2006-07-11
sudo apt-get install wine

[then follow the instructions here]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam") for cs:s

---

