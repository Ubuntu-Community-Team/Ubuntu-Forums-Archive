---
title: "cedega problem"
date: 2006-01-13
forum: Gaming &amp; Leisure
---

### Post by ClubShewty on 2006-01-13
cedega says this error:
```

Warning: Language 'en_FI' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09; 
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
```

I have other error too. During the game it says that and freezes for some time:
```
WARNING: wait4 timed out
WARNING: wait4 timed out
WARNING: wait4 timed out
```

anyone can help me to solve these please? I would be thankful.

---

### Post by IsSuE on 2006-01-13
looks like u need to define your LANG variable.
open a shell and type echo $LANG you should get an output. if not set the LANG variable according to your Language :D
like LANG=de_AT.UTF-8 is the right one for me, as i am austrian and using german language :)

hope this helps

---

### Post by ClubShewty on 2006-01-13
```
shewty@tarnu:~$ echo $LANG
en_US.UTF-8
```

Still it wont work. says same error still.

---

### Post by ClubShewty on 2006-01-13
okay I solved language problem. still need to solve that wait4 warning.
someone help?

---

### Post by Mr_Grieves on 2006-01-13
A thought. Isn't Cedega a commercial product - wich has a commercial support for thier product? I'm sure they have some kind of support forum wich might be a good place to look in.

---

### Post by handy on 2006-01-13
I would think that support could be very limited if you use the WineCVS to make Cedega.

There is a forum that you can read but not write to unless you are a subscriber to Cedega:

[http://transgaming.org/forum/](http://transgaming.org/forum/)

---

