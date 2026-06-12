---
title: "Deja Dup restore problems"
date: 2012-04-03
forum: Desktop Environments
---

### Post by CJ_Hudson on 2012-04-03
I get "status 500" error code whilst trying to restore my system after a fresh install (because of a video driver bug, see [_here_)]("http://ubuntuforums.org/showthread.php?t=1948019") and [_here_]("http://ubuntuforums.org/showthread.php?t=1942272")
Not sure if it's a problem with Ubuntu One, where my files are stored, or Deja Dup.
Please, the files Deja Dup restores (almost my full 5GB allowance of free storage here,) are not those same files I can see in my Ubuntu One folder. I could just manually copy them across. That can't be the backup files.


In fact it's more complex than that, far from adding extra folder as suggested [here]("https://bugs.launchpad.net/deja-dup/+bug/882699?comments=all") I have in fact already have two "Devices connected with my personal cloud" both with the same name listed in "devices" tab of the control panel.  When I reinstalled Ubuntu Obviously I called the computer the same name so I guess it is now trying to restore itself from the wrong folder i.e. the new folder generated when I reinstalled Ubuntu with the same name which has nothing in it. Any suggestions as to which one I should delete? There is one with no settings and one with boxes to tick for "Show activity notifications" and "Limit file synch bandwidth usage". Both have a 'Remove' button glaring at me.

EDIT:
Ah there is a box to tick in Ubuntu 1 which synchronises it with your Deja Dup backup. However it still gives Error 500.

---

### Post by CJ_Hudson on 2012-04-09
Bump

---

### Post by CJ_Hudson on 2012-04-14
Aha! I discovered you have to change the location of the restore folder. I initially thought Deja Dup would restore my files by downloading them. However if I am correct I surmise it in fact synchronises first to a local folder, then you restore them from there. How silly of me to think it just restored them simultaneously whilst downloading them from the Ubuntu One cloud! I simply had to browse to change the location of the 'restore' folder from the default (Ubuntu One) to the following folder (I assume synched to my local disc after the fresh install of Ubuntu) : /home/*myname*/deja-dup/*myname*-System-Product-Name

YAY!! All files successfully restored saving me no end of uneccessary labour.
:guitar:

I would like to thank the creators of Deja Dup, it's a great program. :-)

---

