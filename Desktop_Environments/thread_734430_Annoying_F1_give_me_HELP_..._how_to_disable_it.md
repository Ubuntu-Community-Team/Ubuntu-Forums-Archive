---
title: "Annoying F1 give me HELP ... how to disable it?"
date: 2008-03-24
forum: Desktop Environments
---

### Post by asbesto on 2008-03-24
Hi, 

pressing F1 in almost every application I use under gnome, it open me a F@&#ING D@MN3D help window.

This is *tremendously* annoying me because F1 is just under ESC key, and the mistake give me a damned HELP window every time.

Does anyone know how to DESTROY this UNUSEFUL feature? 8(

---

### Post by Sam Lars on 2008-03-24
System > Preferences > Keyboard Shortcuts

---

### Post by asbesto on 2008-03-25
Ehm... no: there is nothing about F1 in System - Preferences - Keyboard Shortcuts, for this I'm asking here! :confused::(

---

### Post by asbesto on 2008-03-25
Dirty trick to solve this behaviour:

1) create a /usr/local/bin/nothing script:

```

#!/bin/bash
exit 0

```

2) rm /usr/bin/gnome-help

3) ln -s /usr/local/bin/nothing /usr/bin/gnome-help

no more D@MN3D help pressing f1 !!! :)

:guitar::lolflag:

---

### Post by Sam Lars on 2008-03-25
Ok, cool, whatever works. :)

---

### Post by juanitobanana on 2008-07-12
is there a less brutal way to solve this problem?

---

### Post by Sam Lars on 2008-07-12
I've uninstalled the help stuff, so it just pops up an error for me...
You could assign F1 to a different action that maybe you could use.

---

### Post by conorsulli on 2008-07-12
> **asbesto said:**
> Hi, 

pressing F1 in almost every application I use under gnome, it open me a F@&#ING D@MN3D help window.

This is *tremendously* annoying me because F1 is just under ESC key, and the mistake give me a damned HELP window every time.

Does anyone know how to DESTROY this UNUSEFUL feature? 8(

YES. what i did was in compizconfig settings manager I overrode this command by enabling f1 to initiate "shift switcher" now I just enable the shift preview when f1 is pressed which I actually use. It doesnt hog the system like the help command and can be exited quickly by pressing f1 or enter again. of course you can assign it to other desktop effects also. use the grab command and just press f1. e.g 

shiftsitcher plugin -> key bindings tab -> initiate -> grab command , then just press f1.

This is more a workaround but any other way you would probably be making changes you wouldn't be sure about. this way is 100% safe.

hope this helps

---

