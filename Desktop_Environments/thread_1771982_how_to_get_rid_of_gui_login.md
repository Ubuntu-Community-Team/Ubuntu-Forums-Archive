---
title: "how to get rid of gui login"
date: 2011-05-30
forum: Desktop Environments
---

### Post by Skawt_S on 2011-05-30
I was wondering how to switch to a text login rather than gui

I was under the impression that you had to change the initdefault to 3 in the /etc/inittab file but I can not find the file. 

Any one know how to do this would be great.

---

### Post by Oxwivi on 2011-05-31
Remove the GDM.```
sudo apt-get remove gdm
```

Note though, I do not know how to load a regular graphics session without using GDM - you need to wait for someone else to clarify it for you.

---

### Post by dFlyer on 2011-05-31
> **Skawt_S said:**
> I was wondering how to switch to a text login rather than gui

I was under the impression that you had to change the initdefault to 3 in the /etc/inittab file but I can not find the file. 

Any one know how to do this would be great.

Here is a link:

[http://ubuntuforums.org/showthread.php?t=167949](http://ubuntuforums.org/showthread.php?t=167949)

I would recommend that you do google search or forum search before asking a question.

---

### Post by jerrrys on 2011-05-31
or a google forum search

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+gui+login&as_qdr=all&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+gui+login&as_qdr=all&sa=Google+Search&lang=en#881)

---

### Post by Krytarik on 2011-05-31
> **dFlyer said:**
> Here is a link:

[http://ubuntuforums.org/showthread.php?t=167949](http://ubuntuforums.org/showthread.php?t=167949)

I would recommend that you do google search or forum search before asking a question.
Those thread is from 2006 and the suggestions made there won't work anymore, for several reasons.

See this recent post instead:
[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400)

Greetings.

---

