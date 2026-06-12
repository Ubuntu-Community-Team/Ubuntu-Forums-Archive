---
title: "[SOLVED] Games not running in fullscreen all the time."
date: 2008-06-14
forum: Gaming &amp; Leisure
---

### Post by Uzi304 on 2008-06-14
Well when I try playing games such as Open Arena, Nexuiz, Zero Ballistics, and Savage: The Battle for Newerth, they keep switching between fullscreen to window mode without warning. It's annoying because the top and bottom panel cover up part of the screen when it switches to windowed mode. Any ideas?

---

### Post by doorknob60 on 2008-06-14
You have Compiz (desktop effects) turned on while you play. This reduces performace and causes issues like that. Turn it off before you play any games, or make a script to start the game:
```

#!/bin/sh
# Disables Compiz
metacity --replace &
# Starts OpenArena
openarena
# Reenables Compiz
compiz --replace &
```
 
You can adjust that script to easily work with other games as well. I'd just put it somewhere in your home folder and change your launchers to launch the script. Don't forget to make it executable though (you can acomplish this in the Permissions tab of Properties).

---

### Post by Uzi304 on 2008-06-14
Ah thanks a lot, I just tried and it works!

---

### Post by michaelrg1231 on 2011-10-14
this didnt work for me

---

### Post by Perfect Storm on 2011-10-14
Please check the date of this thread.


Thread closed.

---

