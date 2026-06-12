---
title: "root access to user display"
date: 2008-12-10
forum: General Help
---

### Post by jansch75 on 2008-12-10
I have an udev script (runs with root privileges) which is started after I have plugged my external USB hard drive into the computer. I would like to give the root access to my display to show some zenity windows...

The important lines of the script:

```
#!/bin/bash
export DISPLAY=:0.0
su USERNAME -c '/usr/bin/zenity --info --text "XYZ"'

```

This script runs well on one of my ubuntu computers (both computers have Hardy Heron). The other machine requires that I have to run as normal user  from a terminal 

```
xhost +local:USERNAME

```

before I can start the automatic udev script...

Otherwise I will get the error messages "No protocol specified.".

Why are there this differences betwieen the two computers? How can I automatically allow the access to the display without starting xhost from the terminal before on the second machine? Can I run xhost =local:USERNAME during start up as start up script? If yes, is this a security risk?

REALLY THANKS for any help since I am really stuck here... In spite of a lot of google searches I have not found any solution yet...

---

