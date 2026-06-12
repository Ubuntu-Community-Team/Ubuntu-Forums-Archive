---
title: "I love Epiphany, but I borked it -- how to completely remove/reinstall?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by NexusOfNow on 2006-02-28
I'd posted a query in [a prior thread]("http://www.ubuntuforums.org/showthread.php?t=137429"), but I think I could have asked better.  All I really need to know is, how can I completely, totally, wholly remove all records of a buggy Epiphany install?

I managed to bork my epiphany by selecting what may have been a bad combo from epiphany-extensions (via Automatix), and after trying to completely uninstall then reinstall via Synaptic, I still get a message asking if I wanna recover from my old session, and then a crash error.  If I can find a way to undo it all and restart, I could trace back the source of my other problems myself. :)

For the fifteen minutes I got to use Epiphany, I fell in love with it, so ANY help here would be quadruply appreciated!

Thanks a billion ~

Paula

---

### Post by o_fortuna on 2006-02-28
[QUOTE=NexusOfNow]I'd posted a query in [a prior thread]("http://www.ubuntuforums.org/showthread.php?t=137429"), but I think I could have asked better.  All I really need to know is, how can I completely, totally, wholly remove all records of a buggy Epiphany install?

I managed to bork my epiphany by selecting what may have been a bad combo from epiphany-extensions (via Automatix), and after trying to completely uninstall then reinstall via Synaptic, I still get a message asking if I wanna recover from my old session, and then a crash error.  If I can find a way to undo it all and restart, I could trace back the source of my other problems myself. :)

For the fifteen minutes I got to use Epiphany, I fell in love with it, so ANY help here would be quadruply appreciated!

Thanks a billion ~

Paula[/QUOTE]
Do this in the command line (Applications-->Accessories-->Terminal) to completely remove epiphany:
```
sudo apt-get remove --purge epiphany-browser epiphany-browser-dev epiphany-browser-extensions
```
Then, to reinstall, do it the normal way through synaptic. It should have been totally removed from the system, so it should work fine.

---

### Post by doclivingston on 2006-02-28
You Epiphany profile is stored in "~/.gnome2/epiphany/", removing that folder should fix your problems.

---

### Post by NexusOfNow on 2006-02-28
You both are totally faboo, it worked (of course)!

Thank you very very muchly, I deeply appreciate it ~

Paula

---

