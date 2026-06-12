---
title: "Application Launcher Question"
date: 2009-02-09
forum: General Help
---

### Post by Waltomatic on 2009-02-09
The xsensors package will not work for my chip set, so I want to make an application launcher that opens a terminal and then runs the command "sensors".

I've tried just putting the "sensors" command into an application in terminal launcher, but that closes the terminal immediately after running the command.

Any help would be appreciated.

---

### Post by SeanTater on 2009-02-09
As for the terminal, are you start the terminal and then typing commands, or are you typing commands into the Alt-f2 dialog? You should probably start the terminal on it's own for this application.

For the missing sensors, most probably are not detected until you run ```
sensors-detect
```

After that, usually you will get several of them. If you don't, it might not be possible to get those sensors. Before you assume that, however, give ```
sudo apt-get install mbmon && sudo mbmon
``` a try.

---

### Post by Osamabingandhi on 2009-02-09
There is a way to get them on the panel with an panel object, who then connects to the sensors. See if there is anything like that to download. Here is one old thread: 

[http://ubuntuforums.org/archive/index.php/t-14730.html](http://ubuntuforums.org/archive/index.php/t-14730.html)

there's also an applet called computertemp.

then you also can install sensors-applet

---

### Post by Waltomatic on 2009-02-09
lm-sensors is working fine. I just want to have some sort of short cut to using it. 

I'm wondering if it is possible to make a short cut that opens a terminal, runs sensors, and displays the output for me to see.

---

### Post by SeanTater on 2009-02-09
For that, you could paste this into a file and run it (I'm sure it could be applied to Gnome's terminal too, but I don't have it at hand, so this requires xterm)

#!/bin/bash
xterm -e "sensors; read -p 'Press Enter to exit ' "

---

### Post by Waltomatic on 2009-02-09
> **SeanTater said:**
> For that, you could paste this into a file and run it (I'm sure it could be applied to Gnome's terminal too, but I don't have it at hand, so this requires xterm)

#!/bin/bash
xterm -e "sensors; read -p 'Press Enter to exit ' "

This is exactly what I needed. Thank You.

---

### Post by Waltomatic on 2009-02-09
> **SeanTater said:**
> For that, you could paste this into a file and run it (I'm sure it could be applied to Gnome's terminal too, but I don't have it at hand, so this requires xterm)

#!/bin/bash
xterm -e "sensors; read -p 'Press Enter to exit ' "

Is there any way that I could configure this to refresh the temperature output by pressing enter?

---

### Post by SeanTater on 2009-02-09
Sure! Use this instead..

```
xterm -e "while true; do sensors; read -p 'Press Enter to refresh, Ctrl-D to quit' || break; done"
```

---

### Post by Waltomatic on 2009-02-09
Thanks so much! 

My CPU cores thank you too.

---

