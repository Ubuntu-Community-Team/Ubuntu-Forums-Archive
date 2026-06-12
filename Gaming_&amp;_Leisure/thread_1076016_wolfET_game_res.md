---
title: "wolf:ET game res"
date: 2009-02-20
forum: Gaming &amp; Leisure
---

### Post by Nemix on 2009-02-20
hey,
my issue is that when i start the game wolfenstein enemy territory it only uses like 75% of my screen the right hand side is just black. i guess it something to do with X server from what ive gathered from other threads and posts ive looked at but with out getting a solution. 

> **chavo said:**
> I just use a separate X session - write a script like this .
```

#!/bin/bash
startx -- :1 -br
et

```

Just name it xet or something, mark it executable and put it in your ~/bin folder. Then hit Ctrl-Alt-F1, log in and run xet. Hit Ctrl-Alt-F7 and Ctrl-Alt-F9 to switch back and forth between et and your desktop. I usually log out of KDE anyway when I'm playing et, just to free up as many resources as possible.

i tried that but didnt seem to work, i know it was for an older verion and im on 8.10. maybe there is something like this that i can do to solve my problem. 

thanks for your time :D

---

### Post by Nemix on 2009-02-21
anyone??

---

### Post by paul.maddox on 2009-02-22
Try this:

```

#!/bin/bash

killall -9 gnome-screensaver;

KEY=$(xauth list | grep localhost | gawk '{print $3}');
xauth add :1.0 MIT-MAGIC-COOKIE-1 $KEY;

sudo xinit et -- :1 -xf86config xorg.conf

```

---

