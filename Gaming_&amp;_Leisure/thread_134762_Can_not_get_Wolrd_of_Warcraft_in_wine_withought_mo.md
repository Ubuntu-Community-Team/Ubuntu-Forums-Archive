---
title: "Can not get Wolrd of Warcraft in wine withought mouse bug!"
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by lungdart on 2006-02-22
WoW is installed and works perfect except for the mouse bug (where the background is rendered in front of the characters so you cant click on anyone, and you have to press 'v' and click on there health bar, or look at the sky and look back). I can't fix this I've tried it all.

Compiling my own wine 0.9.8 with source patched with both patches (wine-cvs-glx.diff, wine-wow-fixes.patch) goes with out a hitch. No errors standard compiling output. 

commands used to patch:
```

patch -p1 < wine-cvs-glx.diff
patch -p1 < wine-wow-fixes.patch

```

command used to compile
```
./configure && make depend && make && sudo make install
```

This gives no errors but after doing that, loading winecfg, or any non opengl program i get this:
```

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

An when i try to run WoW.exe -opengl i get this:
```

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

```

So i did sudo make uninstall && sudo make distclean and figured id go with CVS build since i read that CVS has the patches built in now.

```

export CVSROOT=:pserver:cvs@rhlx01.fht-esslingen.de:/home/wine
cvs login
cvs -z 3 checkout wine
./configure && make depend && make && sudo make install

```

Again compiles fine no errors. But i go to run winecfg or WoW.exe and get the exact same errors as above! so i uninstall the cvs and install wine 0.9.8 via apt again. Which makes wine work! but still with the mouse bug.

I've also tried runing in window mode with with wine cfg, with windowed mode option in WoW, and with both. I heard sometimes this works, but it didnt. Finally i tried a command before i launch wine in a script called wow.sh with chmod +x wow.sh. this is the script:
```

export WINEPRELOADER_SETVALEGACY="no"
cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
wine WoW.exe -opengl

```

This had one enemy clickable! hearthed to town and no npcs were clickable. Restarted and no enemies were clickable again. This could of been me looking at the sky and then back down from moving arround (as i heard this fixes it), but never again was an enemy clickable.

My system is:
intel celeron (i beleive) @ 1.42ghz
Nvidia Geforce FX 5200 128mg ram, with nvidia drivers for linux
768mb DDR ram
Ubuntu 5.10 with wine 0.9.8 via apt configured with winetools. and other blizzard games installed (starcraft, diablo II) working fine.

HELP! any help what so ever would be greatly appreciated! :confused:

---

### Post by lungdart on 2006-02-22
UPDATE/BUMP

I was able to get the current wine cvs compiled and working normally, but unfortunatly WoW.exe still gives the same opengl.dll error. There were some packages missing that were needed to compile (but never gave out errors) Doing a "sudo apt-get build-dep wine" did the trick (manually installed all the deps myself or so i though, by doing a ./configure and isntalling everything it error'd on)

Anyone know why the im getting the error? and I dont seem to be the only one when compiling. I read something about some guy replacing files that were removied from x11 when installing the ATI drivers, but I use an nvidia card, with nvidia drivers.

More research I guess, if anyone knows something dont hesitate to post, btw.

---

