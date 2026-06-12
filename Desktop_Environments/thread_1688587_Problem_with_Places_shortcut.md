---
title: "Problem with Places shortcut"
date: 2011-02-15
forum: Desktop Environments
---

### Post by talekksna on 2011-02-15
It goes something like this....
When I try to open Download, Music or any other folder (accept Picture) from Places in upper Panel I got warning <picture not found file///home/'name'>
Thank you.

---

### Post by jerrrys on 2011-02-16
hi talekksna

seen a few other post like this, seems to be 10.10 related and not LTS.  if this is a fresh install, you may want to consider replacing it with 10o4 LTS; its very solid and supported for two years.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=folders+not+opening+in+places&as_qdr=all&sa=Google+Search&lang=en#878](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=folders+not+opening+in+places&as_qdr=all&sa=Google+Search&lang=en#878)

---

### Post by Krytarik on 2011-02-17
It is a common issue of inadvertedly setting another program (than nautilus) to handle folders by default. And definetely not a bug or an error at all!

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Here is a good explanation of what most probably has caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

---

### Post by talekksna on 2011-02-20
Bravo, majstore!!!!
Thank You Krytarik.
That is solution.:D

---

