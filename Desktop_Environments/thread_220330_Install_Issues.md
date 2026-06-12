---
title: "Install Issues"
date: 2006-07-21
forum: Desktop Environments
---

### Post by jazzman14 on 2006-07-21
Hi,

I downloaded the desktop edition iso, I didn't check the Md5 sum thing and i just burned it and tried to run it from boot and it wont run. I'm ready to redownload the file, which I have, but I'm extremely confuzed with this md5sum thing, can someone run me through how to do it using windows XP? Thanks.

---

### Post by jimbob on 2006-07-21
how to do md5sum on windows xp
download a copy of md5sum.exe to c:\windows\system32

(I got mine from [http://downloads.activestate.com/contrib/md5sum/Windows/](http://downloads.activestate.com/contrib/md5sum/Windows/))

open command prompt (start -> run -> 'cmd')

cd to the directory where the file you want to check is e.g. cd c:\downloads

type md5sum filenameoffileyouwanttocheck.foo

This will return a string of numbers and letters - compare to the one listed against the file you downloaded (i.e. the one usually listed somewhere on the page where you downloaded the file from)
Posted at 09:22 by rick :: link
Friday, August 06, 2004
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

