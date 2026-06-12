---
title: "Add Icon (application) next to name in upper right corner (gnome / ubuntu 13.04)"
date: 2013-07-16
forum: Desktop Environments
---

### Post by oddbeck on 2013-07-16
Hi!

I need to develop an application that can be visible in the upper right corner, and also clickable.

Does this HAVE to be a gnome extension or can I create an application that does this somehow in 
f.ex Java, C/C++, Python etc?

I've used to use the "system tray" when I've developed things before, but it only shows whenever I 
press the 'windows' / 'meta' key and defeats the purpose for my part.

Thanks in advance.

---

### Post by dino99 on 2013-07-16
some ideas: [http://developer.ubuntu.com/resources/technologies/notification/](http://developer.ubuntu.com/resources/technologies/notification/)

---

### Post by kostkon on 2013-07-16
If you mean the system tray then you mean indicators. Here is [the documentation]("http://developer.ubuntu.com/resources/technologies/application-indicators/").

Indicators are specific to Ubuntu, but probably your indicator will also work fine in Xubuntu and Lubuntu, albeit in fallback mode. But you will have to do extra work if you want to achieve the same behaviour in other environments (e.g. Gnome Shell) and OSes other than Ubuntu.

Hope that helps.

Correction: I think, indicators work fine in Kubuntu, definitely not in fallback mode.

---

