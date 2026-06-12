---
title: "aplication that worked with WINE and now don't"
date: 2005-11-10
forum: Desktop Environments
---

### Post by flamarro on 2005-11-10
Hi guys,
I have a little aplication called directsub156 (version 1.56 but with higher ones some problem ) that is meant to correct subtitles for especific dvd players firmwares, that i managed to use very often with wine. In Hoary i installed wine with the repos, then, to learn, i installed following a topic in our forum, the cvs version one, the program worked just fine.
Done the upgrade to breezy, used the program , no problem, then, because of another program that i needed at the time (Now, i don't) i started to play with wine, uninstalled the cvs one, in the sources list, added a line with winehq, installed that version, uninstalled, tryed the cvs one again, uninstalled, remove the line in the sources list, try the version in the repos, now, i think i f**** up the wine instalation, because i cant make it work. As soon i start, it show a box saying " External Exception 80000101". I press OK in the box, it appears again, several times until the program shows in the end, but then, it stucks, cant do a thing.
When i start the program in the console and that box appears, the console shows this line ```
 run.c:115: ME_CharOfsFromRunOfs: Assertion `pRun->type == diRun' failed.
```
Does Anyone knows what's wrong? What have i done wrong?
Thanks in advance

---

### Post by dcstar on 2005-11-11
[QUOTE=flamarro]Hi guys,
I have a little aplication called directsub156 (version 1.56 but with higher ones some problem ) that is meant to correct subtitles for especific dvd players firmwares, that i managed to use very often with wine. In Hoary i installed wine with the repos, then, to learn, i installed following a topic in our forum, the cvs version one, the program worked just fine.
Done the upgrade to breezy, used the program , no problem, then, because of another program that i needed at the time (Now, i don't) i started to play with wine, uninstalled the cvs one, in the sources list, added a line with winehq, installed that version, uninstalled, tryed the cvs one again, uninstalled, remove the line in the sources list, try the version in the repos, now, i think i f**** up the wine instalation, because i cant make it work. As soon i start, it show a box saying " External Exception 80000101". I press OK in the box, it appears again, several times until the program shows in the end, but then, it stucks, cant do a thing.
When i start the program in the console and that box appears, the console shows this line ```
 run.c:115: ME_CharOfsFromRunOfs: Assertion `pRun->type == diRun' failed.
```
Does Anyone knows what's wrong? What have i done wrong?
Thanks in advance[/QUOTE]
You may have a corrupted Wine installation now, rename the hidden ".wine" directory in your Home directory and run wine again - it will recreate a fresh environment.

You may have to reinstall your windows apps, but you may do better than you are doing now!

---

