---
title: "write into xinitrc file"
date: 2011-06-17
forum: Desktop Environments
---

### Post by sureshms on 2011-06-17
What is the format to write into the xinitrc file? i want the code "xset  -dpms" and "xset s off" to be inserted into the file. How do i do so?


```


#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession


```[FONT=monospace]



[/FONT]Where do i insert the above commands into the file??

---

### Post by Krytarik on 2011-06-17
I would say, simply below the current content:
```
#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

xset -dpms
xset s off
```
Greetings.

---

