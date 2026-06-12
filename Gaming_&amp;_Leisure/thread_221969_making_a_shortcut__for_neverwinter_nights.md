---
title: "making a shortcut  for neverwinter nights"
date: 2006-07-24
forum: Gaming &amp; Leisure
---

### Post by hobieone on 2006-07-24
anyone know how to create a short cut for neverwinter nights  with ala carte or am i just stuck running it from directly in the folder?

---

### Post by Perfect Storm on 2006-07-24
Make a script for it.

```
cd /where/you/want/the/script
nano RunNWN.sh
```

fill in:

```
#!/bin/bash

cd /to/nwn/folder
./nwn
```

Then make an entrty with alacarte to point to the script instead of the nwn.
Command: sh /to/the/script/RunNWN.sh

---

### Post by hobieone on 2006-07-24
thanks

---

### Post by rhenrick on 2007-12-23
I have AWN (Avant Window Navigator) and noticed that it interferes with NWN. There is a flickering black rectangle at times on the bottom of the screen. To fix this, i created a script ... well added on to the suggested script ... that closes AWN and then launches the game.

SCRIPT:
#!bin/bash

killall avant-window-navigator awn-applet-acti

cd to/nwn/folder
./nwn

You do have to launch AWN after you are done playing, but it's better than shutting it down, THEN launching the game. 

Anyway ... Thank you for the suggested script "Artificial Intelligence".

---

### Post by Perfect Storm on 2007-12-23
You could add launching the AVN after exiting nwn to the script.

---

### Post by joku_muko on 2007-12-23
Whats the difference of .sh and executable text file?

---

### Post by rhenrick on 2007-12-24
> **Artificial Intelligence said:**
> You could add launching the AVN after exiting nwn to the script.

Really? How would i do that?

---

