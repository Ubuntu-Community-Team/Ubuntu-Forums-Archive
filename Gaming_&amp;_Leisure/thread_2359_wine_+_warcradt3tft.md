---
title: "wine + warcradt3tft"
date: 2004-10-27
forum: Gaming &amp; Leisure
---

### Post by fng on 2004-10-27
anyone got warcraft3 tft to work with wine?

i get this error after installing war3tft and clicking the "Play Warcraft 3 The Frozen Throne"-link : ```
fng@butters:~ $ wine /media/cdrom0/autoplay.exe
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
fixme:console:SetConsoleCtrlHandler ((nil),1) - no error checking or testing yet
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:shell:Stream_WriteLocationInfo writing empty location info
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
err:menubuilder:InvokeShellLinker failed to extract icon.
fixme:shell:Stream_WriteLocationInfo writing empty location info
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
err:menubuilder:InvokeShellLinker failed to extract icon.
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_BE' was not recognized, defaulting to 'en_US'.
Wine failed with return code 101
fng@butters:~ $ 
```

after this i try to run wine Frozen\ Throne.exe.  It nags about not finding the cdkey and not able to find the cd in the cdrom.

---

### Post by jdong on 2004-10-27
read the howto here: [http://appdb.winehq.org/appview.php?appId=1377](http://appdb.winehq.org/appview.php?appId=1377)

Always check the winehq database.

---

### Post by NEtX on 2005-01-06
Hi,

I've tried to copy my WarcraftIII win installation (alredy patched to 1.17), which i've already cracked, onto my ubuntu  drive and executed it with this parameters "Frozen\ Throne.exe -- -opengl", like its written in [http://appdb.winehq.org/appview.php?appId=1377](http://appdb.winehq.org/appview.php?appId=1377), but i got the same failure. It nags about not finding the cdkey and beeing not able to find the cd in the cdrom.

Thanks for helping,
Nikolaus

---

### Post by fng on 2005-01-06
I'll my problems went away when i uninstalled wine and installed cedega 4.1.
Warcraft 3 is running excellent.  Even with BattleNet.

---

