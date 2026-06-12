---
title: "Steam on Wine will not connect account"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by Ryutatsu on 2006-06-12
I've set up Steam and the activex control but when I put in "wine .wine/drive_c/Program\ Files/Steam/Steam.exe" it will get to the point where it says it's connecting account but it will display this error in the terminal and steam will freeze 

fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod

Does anyone have any idea how to fix this? Games are the only thing keeping me on windows and this would almost get rid of that problem.

---

### Post by dubnmike on 2006-06-13
Not sure if It will do anything but cd into the Steam dir and run this:

```
WINEDEBUG="-all" wine Steam.exe
```

I used [*this guide*]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam") to get steam going for me.  Still tackling other issues though.

---

### Post by HAARP on 2006-07-02
This may be 2 weeks old, but I just had the same issue, and perhaps, you still need help.

Download [Cedega's mozcontrol](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz) and extract it into **C:\Program Files\mozcontrol** of your wine. (eg. **/home/*username*/.wine/drive_c/Program Files/mozcontrol**)
In Terminal, type:
```
cd /home/*username*/.wine/drive_c/Program Files/mozcontrol
regsvr32 mozctlx.dll
```
Have fun! :D

---

