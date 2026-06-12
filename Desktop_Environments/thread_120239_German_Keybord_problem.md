---
title: "German Keybord problem"
date: 2006-01-21
forum: Desktop Environments
---

### Post by appopson on 2006-01-21
hi,
I begin in linux since two years with mandrake and migrate to Suse. I am using  KUBUNTU now.

My problem is on my german keybord I dont know how to activate latin fonts (like é, à, ...). ](*,) 

Every help will be appreciated.

Thank's

---

### Post by Witty Name on 2006-01-21
Several files can help.

~/.xmodmaprc is one.

What you are looking for, is probably being able to use "dead keys" for your diacritics, that is, type " and e and get an e with umlaut.

I don't quite see why you can't do this in KDE, but I suppose you could modify your file to add for example "keycode  24 = apostrophe quotedbl dead_acute dead_diaeresis".

---

