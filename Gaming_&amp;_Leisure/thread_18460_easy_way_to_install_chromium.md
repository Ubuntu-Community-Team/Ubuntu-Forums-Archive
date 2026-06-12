---
title: "easy way to install chromium?"
date: 2005-03-07
forum: Gaming &amp; Leisure
---

### Post by Lupis52 on 2005-03-07
hi, im currently running the hoary hedgehog version of ubuntu (amd64 version as well). i was told by a friend to try out chromium, an overhead 3d arcade shmup type of game. however, i cannot find it in synaptic. ive been to their website, and found tars of the source, but im quite a newb at this and dont know how id go about installing that. if there is any easier way of getting this game installed, it would be appreciated.

---

### Post by poofyhairguy on 2005-03-07
[QUOTE=Lupis52]hi, im currently running the hoary hedgehog version of ubuntu (amd64 version as well). i was told by a friend to try out chromium, an overhead 3d arcade shmup type of game. however, i cannot find it in synaptic. ive been to their website, and found tars of the source, but im quite a newb at this and dont know how id go about installing that. if there is any easier way of getting this game installed, it would be appreciated.[/QUOTE]


I don't think so. Its in the i386 Universe...maybe you can try installing it from there? I don't know.

---

### Post by jdodson on 2005-03-07
[QUOTE=Lupis52]hi, im currently running the hoary hedgehog version of ubuntu (amd64 version as well). i was told by a friend to try out chromium, an overhead 3d arcade shmup type of game. however, i cannot find it in synaptic. ive been to their website, and found tars of the source, but im quite a newb at this and dont know how id go about installing that. if there is any easier way of getting this game installed, it would be appreciated.[/QUOTE]

enable the universe respositories according to this guide:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) - follow the add extra repositories link

then follow the manual update/upgrade link.

now type the following:

```
sudo apt-get install chromium
``` 

you should be all set to play!  if the link does not appear in the games menu open a terminal and type "chromium"

good luck!

---

### Post by Lupis52 on 2005-03-07
another question, is there an easy way to get these things added to my games menu, and possibly have it do it automagically in the future?

---

### Post by HungSquirrel on 2005-03-08
> is there an easy way to get these things added to my games menu
In Gnome, unfortunately, no.  It boggles my mind how the Gnome devs insist upon making such an attractive desktop environment as uncustomizable as possible.  [/rant]

---

### Post by jdodson on 2005-03-08
[QUOTE=HungSquirrel]In Gnome, unfortunately, no.  It boggles my mind how the Gnome devs insist upon making such an attractive desktop environment as uncustomizable as possible.  [/rant][/QUOTE]

cant you do it by typing in applications:/// in nautilus?

---

### Post by arobinson on 2009-05-01
> **jdodson said:**
> enable the universe respositories according to this guide:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) - follow the add extra repositories link

then follow the manual update/upgrade link.

now type the following:

```
sudo apt-get install chromium
``` 

you should be all set to play!  if the link does not appear in the games menu open a terminal and type "chromium"

good luck!

Avoid the Chromium PPA version in Jaunty amd64 - it will lock up your system.

---

