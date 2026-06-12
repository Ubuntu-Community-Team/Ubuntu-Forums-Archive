---
title: "Latin-English Dictionary"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Techman010 on 2006-09-11
hi all...Does anyone know of a good Latin-English, English-Latin dictionary I could add to the dictionary program in Ubuntu?  Thanks a lot.

---

### Post by Techman010 on 2006-09-24
bump?

---

### Post by cptnapalm on 2006-09-24
In either the universe or multiverse repository, there is the dict-freedict-eng-lat and dict-freedict-lat-eng

---

### Post by ropers on 2006-09-24
I've not tried this, but these might help:
[http://www.freedict.org/en/](http://www.freedict.org/en/)
[http://packages.debian.org/stable/text/dict-freedict-lat-eng](http://packages.debian.org/stable/text/dict-freedict-lat-eng)
[http://packages.debian.org/stable/text/dict-freedict-eng-lat](http://packages.debian.org/stable/text/dict-freedict-eng-lat)
You may also have to install dictd or JDictd as a local DICT server, which I don't think is running on your local Ubuntu box by default (unverified guess, I'm a 1 week Linux newbie).
[http://www.informatik.uni-leipzig.de/~duc/Java/JDictd/](http://www.informatik.uni-leipzig.de/~duc/Java/JDictd/)
[http://www.google.ie/search?hl=en&q=JDictd&btnG=Google+Search&meta=](http://www.google.ie/search?hl=en&q=JDictd&btnG=Google+Search&meta=)
[http://packages.debian.org/stable/text/dictd](http://packages.debian.org/stable/text/dictd)
[http://sourceforge.net/project/showfiles.php?group_id=605&package_id=59088](http://sourceforge.net/project/showfiles.php?group_id=605&package_id=59088)
[http://www.google.ie/search?hl=en&q=Dictd&btnG=Search&meta=](http://www.google.ie/search?hl=en&q=Dictd&btnG=Search&meta=)

---

### Post by Techman010 on 2006-09-24
I added dict-freedict-eng-lat and dict-freedict-lat-eng, but how would I set that up in the Ubuntu dictionary program?

Thanks for the reply.

---

### Post by ropers on 2006-09-24
'long time ago I created a locally installable DICT server and DICT client package for the Mac (Apple have since included a Dictionary with the OS).

This is for OS X, but if you read all thru this, it might give you an idea what you have to do:

[http://www.ropersonline.com/dicthowto.old/MacOSX.DICT.Howto.html](http://www.ropersonline.com/dicthowto.old/MacOSX.DICT.Howto.html)
[http://www.ropersonline.com/dicthowto.old/](http://www.ropersonline.com/dicthowto.old/)

Of course it's possible that Ubuntu already includes a local DICT server solution. I dunno. I'm new to Linux and clueless about anything that differs from OpenBSD and OS X...

PS: If you have to skimp on clockcycles, I would recommend using dictd over JDict, if not choose what server better suits your needs -- Both do the job but behave differently if you type in something that isn't a direct match. Also, JDictd includes a webserver/dictionary webpage.

---

### Post by Karl S. on 2007-05-26
Whitaker's Words.
[http://users.erols.com/whitaker/words.htm](http://users.erols.com/whitaker/words.htm)

Works like a charm.

---

