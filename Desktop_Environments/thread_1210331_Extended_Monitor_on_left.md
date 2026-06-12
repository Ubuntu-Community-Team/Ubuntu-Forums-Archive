---
title: "Extended Monitor on left"
date: 2009-07-11
forum: Desktop Environments
---

### Post by Otterbuntu on 2009-07-11
Ok this is embarrassing. I am trying to extend the desktop to an additional monitor that is placed to the left of my primary. It seems to only want to treat that monitor as if it is to the right (I have to move the cursor to the right to get to the screen to the left), not the left. When I swap the monitor placement in the Display options, it just swaps my primary monitor to the one on the left.   you get the idea.

---

### Post by naklinaam on 2009-07-11
The GUI would depend on the driver you are using (I have nvida and it has an option to position the screen to left, right, above or below another screen.

from the command line, execute ```
sudo gedit /etc/X11/xorg.con
``` you can replace the gedit with any editor of your choice.

look for a section called **"ServerLayout"** and look for 
**"Screen      1  "Screen1" RightOf "Screen0""** change the RightOf to LeftOf

below is the extract from my xorg.conf file

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" **LeftOf** "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

---

