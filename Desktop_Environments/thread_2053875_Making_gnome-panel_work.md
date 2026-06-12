---
title: "Making gnome-panel work"
date: 2012-09-06
forum: Desktop Environments
---

### Post by lesliek on 2012-09-06
I upgraded from 10.04 to 12.04, but don't want to waste time learning about Unity. It seemed that I could return to what I was used to by installing gnome-panel, so I did. However, when I boot up, I'm not given the option to select the Gnome Classic session, as I thought I would be (see, for instance: [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)).

Is there something else I need to do to be able to choose Gnome Classic?

Later: I found I had to double-click on my name to be given the option, rather than its just appearing.

---

### Post by cmcanulty on 2012-09-06
```
sudo apt-get install gnome-session-fallback
```

---

