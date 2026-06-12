---
title: "Is there a way to create a &quot;clone&quot; system file under apt, like you can in yast?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by frank_y on 2006-06-28
I know that yast has a feature that makes a config file if you want to "clone" the set-up of a particular system if you want to install it on multiple machines or if you simply want to save your set up for the next reinstall. Is there a way to do this with apt or dpkg?

Secondly, not so related, synaptic has that package search feature. Is this accessible from the terminal?

---

### Post by Qrk on 2006-06-28
I don't believe Ubuntu has this feature. You can choose to install in "OEM" mode that will allow a blank slate for the new user to use; but it isn't quite the same thing. 

As for searching from the command line, I like to use aptitude (like apt-get but with more features) "aptitude search *packagename*" will do it.

---

