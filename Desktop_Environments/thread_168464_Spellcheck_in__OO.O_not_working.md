---
title: "Spellcheck in  OO.O not working?"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Trab on 2006-04-30
hey,
i cant get spellcheck in OO.O to work, its quite annoying, as i write alot of essays, and have to use an online spell checker.....
i really have no clue why this isnt working....
also, i would like to be able to switch to a spanish spell-checker in OO.O (i have to write essays for my spanish class as well, and it would be nice to have that option). 

any advice please? this has been haunting me for a while.

---

### Post by huckem on 2006-04-30
what version of OpenOffice are you running?

---

### Post by Trab on 2006-04-30
OO.O "2"
but in help/about it says
OO.O 1.9.129
thanks

---

### Post by huckem on 2006-04-30
hmmmmmmmm...
That's weird.  try this:
BACKUP your data files (documents, etc.) then reinstall it.

Add one of the mirrors for the openoffice.org files to the /etc/apt/sources.list. Debian mirrors for OpenOffice.org can be found at -   [http://openoffice.debian.net/mirrors.html](http://openoffice.debian.net/mirrors.html) 

do one of these:
sudo apt-get --purge remove (or remove --purge, I cant remember the order) openoffice.org

then reinstall with 

sudo apt-get install openoffice.org




see if that helps, just dont forget to back up your files.

---

