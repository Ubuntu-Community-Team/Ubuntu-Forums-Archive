---
title: "Winecfg and desktop Emulation"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by savage.stoo on 2007-07-09
Hi, still a complete newbie I'm afraid so please be gentle!

Ive been trying to run TES4 Oblivion through wine and have managed to royally screw myself whilst doing it.

By trying to getting it running in a full screen and playing with the desktop emulation setting Ive accidentally set the emulate desktop res to 14x0! oops!

Was wondering if I can reset this Via terminal or if there is a config that could edited.

thanks in advance,

Stoo

PS
Not sure where I should be posting this, sorry if its wrong.

---

### Post by jacob01 on 2007-07-09
you could try uninstalling wine then reinstalling it

---

### Post by cogadh on 2007-07-09
That won't work, the setting is in one of the registry files that are stored in your home directory. Uninstalling Wine does not delete the files in your home directory.

Do this instead:
```
gedit $HOME/.wine/user.reg
```
Scroll down to the bottom of the page, you will find the virtual desktop settings there. Change it to at least 800x600 and everything will be fine.

---

### Post by savage.stoo on 2007-07-09
Didnt think it would have.

Ideal mate,  knew it would be somewhere, but a needle in a haystack.

big thank you.

---

### Post by cogadh on 2007-07-09
No problem. Been there, done that myself once or twice.

Hey, before you tear your hair out trying to get Oblivion to work, did you check out Wine's AppDB entry for the game? It has a very inconsistent performance at best, depending on your Wine version and *nix distribution:
[http://appdb.winehq.org/appview.php?iAppId=3150](http://appdb.winehq.org/appview.php?iAppId=3150)

---

### Post by jacob01 on 2007-07-09
ok then delete the registry files i alway delete them when i mess something up

---

### Post by cogadh on 2007-07-09
Unless you also delete the entire .wine directory from  your home folder, just deleting the registry files is a really bad idea. For Wine to work in any kind of stable fashion, you really need to treat the .wine directory as a complete Windows installation. You can't delete a key part of Windows (i.e. the registry) and expect it to work correctly the next time you use it. You're better off doing a complete removal and recreation of your .wine directory, if you don't want to simply edit the registry file. Personally, I have way too much stuff installed in Wine to go through deleting the whole directory just to fix a simple problem that can be corrected with a text editor.

---

