---
title: "Unreal Tournament 2004 fails to start with Assertion error"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by Enverex on 2007-05-13
I used to play this but something must have changed at some point because it doesn't run anymore. When I try and run it from the terminal I get...

```
Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 149]

History: 

Exiting due to error

```

Immediately (well, the splash screen flashes up for about 1/10th of a second.

Any ideas about this? I can't think of anything that would cause it to be honest.

---

### Post by audax321 on 2007-05-13
A google search brought up some possibilities:

[http://www.liflg.org/forum/viewtopic.php?=&p=3834](http://www.liflg.org/forum/viewtopic.php?=&p=3834)

[http://ubuntuforums.org/showthread.php?t=291826](http://ubuntuforums.org/showthread.php?t=291826)

[http://www.ataricommunity.com/forums/archive/index.php/t-377447.html](http://www.ataricommunity.com/forums/archive/index.php/t-377447.html)


I'd try a fresh install using the latest installer and see if that works. First run the game without any patches and see if a completely clean install runs, then install the patches. But I don't see why the game would stop running in Feisty. I'd check it with Feisty, but I still have Dapper on my desktop and my laptop is too slow to do anything with UT2004 :]

---

### Post by Enverex on 2007-05-14
Been through all that, none of it helps, neither does a fresh install.

I did find out what seems to be causing it though. It only happens AFTER I install the MegaPack, if I don't install it then the game works... kinda need to update it though :(

---

