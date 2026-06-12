---
title: "I did something wrong with fonts"
date: 2009-03-06
forum: General Help
---

### Post by AlmaTlust on 2009-03-06
I did something stupid and deleted a few system fonts (I searched for doublettes and deleted the symlinks). Now konqueror crashes if started without arguments, but if I right-klick on a folder in dolphin and let it open in konqueror, it works. Opening a website from the command prompt works.
Firefox starts up, but does not display any text. I tried reinstalling the fonts I deleted (msttcorefonts), but it doesn't help.
Tried to rename .mozilla, .kde, but no help either.
Any one who knows how to fix this?

---

### Post by AlmaTlust on 2009-03-08
Update: It got solved when I renamed the .fontconfig directory to .fontconfig-bak. It then recreated it, and voilá - everythings fine again...

---

