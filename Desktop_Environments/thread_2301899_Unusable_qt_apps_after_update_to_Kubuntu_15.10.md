---
title: "Unusable qt apps after update to Kubuntu 15.10"
date: 2015-11-05
forum: Desktop Environments
---

### Post by GiulioGx on 2015-11-05
Hi, 

I've updated to Kubuntu 15.10 and after some time I use the computer some qt applications like, ktorrent, okular, amarok, skype start to have a very bad look and as a consequence they are unusable. If I reboot my computer everything works fine for some time but eventually the problem reappears. Some other applications, instead, like kate, dolphin, vlc always behave correctly.
If launched one of the problematic application after the problem appears by the konsole I get errors like this one:

[FONT=monospace][COLOR=#000000]X Error: BadDrawable (invalid Pixmap or Window parameter) 9[/COLOR]
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0

[/FONT]Do you know what could be the cause of that? Thanks![FONT=monospace]
[/FONT]

---

### Post by David_Abergel on 2015-11-06
I also am experiencing this problem.

The trick at this link:
[https://bbs.archlinux.org/viewtopic.php?id=200167](https://bbs.archlinux.org/viewtopic.php?id=200167)
to set
export QT_GRAPHICSSYSTEM=native
in /etc/environment may help.

---

### Post by GiulioGx on 2015-11-06
Thank you very much, that seems to work! ;)

---

### Post by GiulioGx on 2015-11-06
I may have rejoiced too soon, the problem persists!

---

### Post by GiulioGx on 2015-11-07
It seems updating to openjdk-8 solved the problem.

---

### Post by mörgæs on 2015-11-07
Good, please use Thread Tools for marking the thread solved.

---

