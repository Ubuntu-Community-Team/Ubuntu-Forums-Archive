---
title: "Savage installation"
date: 2006-10-04
forum: Gaming &amp; Leisure
---

### Post by christooss on 2006-10-04
I have installed Savage succesfully but it doesn't run.

This are instructions that I followed

Linux:~

Just follow the following links installing each as you go:~

(Ask for help on the forum if you get stuck)

> 1. Full:
    [http://downloads.s2games.com/online_orders/savage_linux.sh.gz](http://downloads.s2games.com/online_orders/savage_linux.sh.gz)
   

2. Patch:
    [http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run](http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run)
   

3. Then install either:

    Mod SEP-3T (Recommended):
    [http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=58](http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=58)

    OR

    Mod EX2 (No Auth):
    [http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=54](http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=54)

(Note for linux users: If your processor doesn't support SSE instructions (such as the original Athlon), extract this over the 2F install:         [http://www.notforidiots.com/autoupdater/SEP-2F-i686.tar.gz](http://www.notforidiots.com/autoupdater/SEP-2F-i686.tar.gz))

4. After following the above steps place the libs directory within your savage folder into your linux libary directory path. Consult your distro's documentation for your libary directory path.

5. For the manual to savage download this file:
    [http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=56](http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=56)

The only problem is number 4. I don't know what to do cause when running savage from my home dir it gives me this error from where you can see that it can't find libs

> 
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out

Thanks for the anwsers

---

### Post by christooss on 2006-10-04
Ok I found out the souluttion

 sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

But when Im connecting server game crashes. It goes to desktop but I can't move mouse than I have to restart X

---

### Post by christooss on 2006-10-04
No problem at all. It was a patch problem. So everything is solved

---

### Post by siman on 2006-10-16
the installation instructions with your small "ln -s"  fix worked great.

thank you... all other howtos if found have at least one broken link

---

