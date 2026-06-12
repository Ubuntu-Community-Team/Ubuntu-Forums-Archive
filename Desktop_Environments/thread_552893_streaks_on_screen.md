---
title: "streaks on screen"
date: 2007-09-17
forum: Desktop Environments
---

### Post by uknowho008 on 2007-09-17
i just installed ubuntu on a cheap compaq computer i got. it has built in everything, p3. im not too sure about anything else, but i have streaks running all the way down the screen. it doesnt do this with xp, im guessing its somwhat of an unsupported video card problem. but im not sure, is there a setting i can change or is it just a driver problem? thanks guys.

---

### Post by ddrichardson on 2007-09-17
Either backup your /etc/X11/xorg.conf and enter the correct horizontal and vertical refresh rates for your screen, or use```

sudo dpkg-reconfigure xserver-xorg
```from the terminal, after killing X - by entering```

sudo /etc/init.d/gdm stop
``` from a second console CTRL-ALT-F2

---

### Post by uknowho008 on 2007-09-17
thanks for the help. i couldnt find the refresh rate in the conf file. but i changed the resolution like i should have before posting this. but now everythings big, i kinda liked the resolution it was before. oh well...

---

### Post by ddrichardson on 2007-09-17
You wont find a refresh rate as you would in windows - you need to enter the horizontal and vertical components seperately and Xorg calculates the correct rates.

You would need to get this information from either a manual or from the manufacturer.

---

