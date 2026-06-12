---
title: "kde 4.3.5 not in backports?"
date: 2010-02-02
forum: Desktop Environments
---

### Post by Pasdar on 2010-02-02
I've enabled backports, but I see no updates... im currently in kde 4.3.4, i've also manually used sudo aptitude dist-upgrade and full-dist-upgrade, but nothing.

---

### Post by lykwydchykyn on 2010-02-02
Did you update/refresh sources?  Yeah I know, dumb question.  Still...

I'm running it now, but I have both backports and the kubuntu-backports ppa enabled, I don't know which it came from.

Can you post your /etc/apt/sources.list file?

---

### Post by Pasdar on 2010-02-02
Thx I figured what was wrong. For some reason enabling backports in Kpackagekit does not uncomment it in the file :/

---

