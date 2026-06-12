---
title: "WINE Native DLL Override"
date: 2005-12-06
forum: Desktop Environments
---

### Post by the_purulent on 2005-12-06
Does anyone know how to force wine to use a native .dll file I copied from a windows install rather than the builtin one? 

I'm trying to get a game that needs function from quartz.dll to run, and I copied the .dll file into wine's windows/system and system32 folders with no success.  In winecfg there is a tab for setting .dll overrides but all the buttons are grayed out and I cannot setup anything.

thanks in advance.
-Clay

---

### Post by bunty on 2005-12-06
depends what wine you're using . Pre-june 2005 you need to edit ~/.wine/config , you will see when you get in there .

More recent wine uses a gui tool called winecfg which is also pretty self explanitory.

Try 'man wine' , visit winehq.com for info , howtos and see if your game is in the appDB (with luck someone has sussed it for you). or use google or the wine-user mailing list. It is not usually a simple task to get games running and here is not the best place to get advice on wine.

HTH

---

