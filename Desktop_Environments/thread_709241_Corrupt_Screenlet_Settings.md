---
title: "Corrupt Screenlet Settings"
date: 2008-02-27
forum: Desktop Environments
---

### Post by mtbsoft on 2008-02-27
I have installed a number of screenlets but a couple of them seem to have become corrupt - two instances of both binclock and copystack are appearing, one from a previous install and one from the current;  some are not appearing until I perform a "restart all screenlets" and not all are obeying my widget layer settings.

I've tried performing a complete uninstall but something is still being left behind as, after the reinstall, a number of them went back to previous locations.

Does anyone have any idea where all the settings for screenlets are located or centralised so I can strip them out after my next uninstall/reinstall?

I'm running Compiz on Gutsy with the restricted ATI drivers and custom display settings enabled.

---

### Post by aashay on 2008-02-27
~/.screenlets

---

### Post by jryprt on 2008-02-27
Open home folder press Ctrl+h look for .config open it go to Screenlets
open it delete any or all in there . & check you /home/username/.config/autostart folder

---

### Post by mtbsoft on 2008-02-29
I'd tried removing the .screenlets directory without effect but I'll check the .config this time.  Cheers.

---

### Post by mtbsoft on 2008-03-05
Well, I cleaned both locations thoroughly this time and checked my session autostart.  Discovered that there seemed to be a bit of conflict between the autostart and the session save state for a couple of the screenlets.  

So I now have an almost behaving set of screenlets.  However, RandomPassword is still doubling up every time I run it and won't stop properly, despite me reloading everything from the archives.  Also, a number of my favourites came back exactly where I left them and not in default positions, so they must be recording state somewhere other than the locations mentioned already.  

Any other ideas or am I going to have to discover how these things are written to find where the state is stored?

---

