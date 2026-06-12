---
title: "need to remove kpanel"
date: 2005-04-25
forum: Desktop Environments
---

### Post by usergentoo on 2005-04-25
Is there a way to remove the kpanel, shut it down or comment it out so it dosent startup or run.

I have shrunk it down and set it for autohide but its still there.

The reason I ask cause Im using ksmoothdock and superkaramba with the osx menubar theme.And I just dont use it anymore.

Heres a snapshot of my desktop if anyones interested.
[snapshot](http://bellsouthpwp.net/u/s/usergentoo/snapshot3.jpeg)


[COLOR=Red][solved][/COLOR] In order to remove kpanel go to  /usr/share/autostart inside this directory there will be  panel.desktop remove it and the kpanel will not load  when you start kde.

The only drawback to this is you nolonger have a application menu. At the moment Im currently creating my own to solve this problem.

---

### Post by usergentoo on 2005-04-27
I know someone has the answer to this question. Im sure all I need to do is edit a script, just finding the right one and what to change is my problem.

I guess in reality thats the solution to most everybodys problem. Knowing what file to change and what to add to them. ;-)

---

### Post by uberlinux on 2005-04-27
how'd ya get ksmoothdock to work under 3.4????

---

### Post by usergentoo on 2005-04-28
I downloaded it from its site. Then dpkg -i ksmoothdoc_3.5.1_i386.deb and it installed did say some minor error but I checked the packaged, it installed and works fine. Using it for 2 weeks now with no problems.

---

