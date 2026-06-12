---
title: "update whatis db?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Tink on 2006-08-18
Hi,

I just installed manpage-dev, but the functions don't show in
man -k  (e.g. man -k printf only returns 
aa_printf (3)        - print text to AA-lib output buffers.
printf (1)           - format and print data ).

How do I make whatis and apropos aware of the new man-pages?
There's no makewhatis command, and the suggested 
whatis -M /usr/share/man -w '*' | sort > /usr/share/man/whatis
from the whatis man-page ran but didn't fix the problem.

Any help greatly apreciated.


Cheers,
Tink

---

### Post by aysiu on 2006-08-19
I'm not sure if you've tried this (it sounds as if you have from your subject heading), but maybe... ```
sudo updatedb
```

---

### Post by Tink on 2006-08-19
Thanks for the try mate, but updatedb modifies the locate/slocate
database and is completely unrelated to the man-pages.  I found
out (on the debian site) that one uses mandb instead of makewhatis
these places (go figure).


Cheers,
Tink

---

### Post by aysiu on 2006-08-19
So *sudo mandb* works? Good to know. Thanks.

---

