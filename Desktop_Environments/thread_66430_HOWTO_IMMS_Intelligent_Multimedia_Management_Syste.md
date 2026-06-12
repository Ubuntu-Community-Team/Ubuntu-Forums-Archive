---
title: "HOWTO: IMMS: Intelligent Multimedia Management System"
date: 2005-09-17
forum: Desktop Environments
---

### Post by danst0 on 2005-09-17
Small Howto:
How to install imms for beep media player.

In the reps there is only a imms plugin for xmms but since there are many reasons for switching to bmp i wanted to use a beep plugin.
I tried several times to compile the plugin from source ([http://www.luminal.org/wiki/index.php/IMMS/Download](http://www.luminal.org/wiki/index.php/IMMS/Download)). And after I installed nearly all *-dev packages available I gave up.
the error was always
```
../immscore/xidle.cc: In member function `void XIdle::query()':
../immscore/xidle.cc:50: error: `display' undeclared (first use this function)
../immscore/xidle.cc:50: error: (Each undeclared identifier is reported only
   once for each function it appears in.)
../immscore/xidle.cc: In member function `bool XIdle::query_pointer()':
../immscore/xidle.cc:82: error: `Window' undeclared (first use this function)
../immscore/xidle.cc:82: error: Fehler beim Parsen before `;' token
../immscore/xidle.cc:84: Warnung: unused variable `int dummyInt'
make[1]: *** [xidle.o] Fehler 1
make: *** [all] Fehler 2
```

I read somewhere that this might be due to a version transition in gcc... (?)

So finally I looked for other ways to install this plugin and i found several, not allways up-to-date, rpms. This is the one I installed and which seems to be working well!
[http://rpmseek.com/rpm/beep-imms-2.0.1-alt1.i586.html?hl=de&cx=1999:B:0:1874258:0:0:0](http://rpmseek.com/rpm/beep-imms-2.0.1-alt1.i586.html?hl=de&cx=1999:B:0:1874258:0:0:0) 

a little ```
alien -i ...
``` after downloading will do the job!

Looking forward to every improvment!

Daniel

---

### Post by talkingwires on 2005-09-27
Great post! I recently came across IMMS (after weeks of hand-holding GJay), and wanted to to use it with BMP instead of XMMS. (Creating a link to BMP's plug directory didn't work, so I just gave up.)

It's a shame about the old version, though. I haven't been able to find a deb or rpm of the latest stable version. And I've been trying to compile the beta of the next version, but it depends on SQLite 3.2.2, which was released months ago, but strangely Ubuntu only has version 3.2.1

---

