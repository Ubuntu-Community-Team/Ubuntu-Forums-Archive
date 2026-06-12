---
title: "need help genome is crashing and crashing"
date: 2005-11-11
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-11
every time i tried to write my password in a prompt to do so genome locks up and theres no way for recover it back

i have rebooted two times and nothing

i really need help

before i installed kopete everything was all right

all i wanted was opening a root terminal and when the systema asked for my password it just frozen.
 and that had happenned two times i dont want to reboot and reboot again

any ideas

thats the first time it happens since i installed brezzy

help

---

### Post by aysiu on 2005-11-11
No ideas. I'd back up and reinstall and leave Kopete out of Gnome.

---

### Post by Ampersand on 2005-11-11
One possibility might be pressing Ctrl, Alt and F1 to get to a terminal desktop, then logging in there and typing
```
sudo dpkg --purge kopete
```
which will remove Kopete and its configuration files. If it was just a compatibility problem, that might solve it.

---

