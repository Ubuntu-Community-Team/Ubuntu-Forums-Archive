---
title: "XFCE problem"
date: 2005-09-02
forum: Desktop Environments
---

### Post by ConnorP on 2005-09-02
i am running XFCE4 (downloaded off of "apt-get")...and when i set XFCE as my default, the desktop backround dissapears and i cannot right click on the desktop! anybody else have this problem? anybody have an answer to this problem?
..edit...i think i fixed it by Alt-F2 xfdesktop..but i have to do that every startup :(

---

### Post by GOwin on 2005-09-03
this is due to nautilus being launched without --no-desktop option

do the following:
ps -ef | grep nautilus
kill -9 <pid>
xfdesktop &

---

### Post by ConnorP on 2005-09-03
[QUOTE=GOwin]this is due to nautilus being launched without --no-desktop option

do the following:
ps -ef | grep nautilus
kill -9 <pid>
xfdesktop &[/QUOTE]
 dont worry..i fixed everything..LOCK the topic please

---

