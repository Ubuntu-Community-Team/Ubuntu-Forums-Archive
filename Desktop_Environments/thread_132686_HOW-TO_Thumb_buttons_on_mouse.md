---
title: "HOW-TO: Thumb buttons on mouse"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Vetto on 2006-02-18
First how to is [http://ubuntuforums.org/showthread.php?t=3828]("http://ubuntuforums.org/showthread.php?t=3828")
You will need to reference this how to up till step 4.

I the only exception I had to do for my KDE system skipping steps 4-1 and 4-2 and instead create the following file:
```
~/.kde/Autostart/mouse
```
and put the following in it: (I use the Kate text editor)
```
#!/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"
exec imwheel -p -k -b "67"
```

Then from a term, type
 ```
chmod +x ~/.kde/Autostart/mouse
```

restart and you should be all set!  thumb buttons act as forward and back buttons in FireFox \\:D/

---

