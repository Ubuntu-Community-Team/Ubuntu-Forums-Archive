---
title: "Upgrade to Jaunty - GNS and shutdown"
date: 2009-04-24
forum: General Help
---

### Post by toast69 on 2009-04-24
I have just up graded to Jaunty and one or to things get me - 
first - I use GNS3, it will not load saved projects, does anyone know why?
second - root terminal does not load.
third - How can you turn off the time delay for logging off/Shutting down etc. When i press the button i want it to turn off not wait a minute or things like that (i know its a small thing, but these are sending me looking for another linux os)
Thanks

---

### Post by Thura on 2009-04-24
For root terminal , try this command ...
```
gksu gnome-terminal
```
or you can just type this in normal terminal ...
```
sudo -s
```

If those doesn't work, saying "you are not in sudoers " or sth like that ...
post the output (errors) further ....

---

