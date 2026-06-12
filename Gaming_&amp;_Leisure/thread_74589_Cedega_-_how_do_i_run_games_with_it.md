---
title: "Cedega - how do i run games with it?"
date: 2005-10-12
forum: Gaming &amp; Leisure
---

### Post by Hack4ev3r on 2005-10-12
hi i would like to know how can i run games with cedega? 

i've tried to install Diablo 2 (from cd not iso is that ok?) and i keep getting this error

paradox@bzq-82-81-196-144:~$ cd /cdrom
paradox@bzq-82-81-196-144:/cdrom$ dir
autorun.inf  d2readme.htm  diabloii.ico  dsetup32.dll  install.exe  support
binkw32.dll  d2sfx.mpq     directx7      dsetup.dll    setup.exe
d2data.mpq   d2speech.mpq  dsetup16.dll  extras        setup.mpq
paradox@bzq-82-81-196-144:/cdrom$ clear

paradox@bzq-82-81-196-144:/cdrom$ cedega install.exe
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
paradox@bzq-82-81-196-144:/cdrom$

ive tried cedega install.exe LANG=en__US doesnt seem to work
so i was wondering is diablo2 just not supported ? am i doing something wrong? or is it beacuse my Locale is hebrew?

Thanks ahead,
Tommy.

---

### Post by jasmuz on 2005-10-12
Did you check at transgaming's webpage to see if Diablo 2 is supported?

---

### Post by Hack4ev3r on 2005-10-12
Yeah, it is supported i even saw screenies of people running it, i've installed the nvidia drivers no problem with that

i think im doing something wrong with cedega :(
thanks for quick replay anyway :)

---

### Post by seethru on 2005-10-12
try LANG=en_US; export LANG then run the command.

---

