---
title: "Swedish spellchecking in latest OOffice"
date: 2006-01-26
forum: Desktop Environments
---

### Post by Kimm on 2006-01-26
Hi,

I was woundering how I can get swedish spellchecking for the latest OO version, downloaded from the OO website. Ubuntu's myspell wount work with it.

I managed to find swedish language support and thought that that included spellchecking... man was I dissapointed..

---

### Post by Garyu on 2006-01-27
I had  a lot of difficulties with spellchecking earlier, and I finally found a very simple solution: at the login splash you can choose language for the session, so just choose swedish and everything should fall in place, at least it did for me. :)

---

### Post by glinsvad on 2006-01-27
In the menu bar of OpenOffice.org2 Writer you select File -> Wizards -> Install new dictionaries. If nothing happens, you need to download the wizard called DicOOo.sxw from:
[http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw]("http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw")

Place the file in this folder:
/usr/share/myspell/dicts

Easiest way to make the changes stick is to have administrative rights for the program, so in terminal just start OpenOffice.org2 Writer with:
```
sudo oowriter2
```

Alternatively, you must change read/write-permissions for certain files as described in DicOOo.sxw.

Well, the rest should be self-explanatory :-k

EDIT: Also check out [this]("http://ubuntuforums.org/showthread.php?t=100695") thread

---

