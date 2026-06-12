---
title: "xwinwrap help"
date: 2007-03-07
forum: Desktop Environments
---

### Post by xboxbman on 2007-03-07
I've trying to get the xwinwrap to give me the matrix animated background.  I've read a number of posts and have followed their instructions exactly everytime, but all  I every get is a descrption of the usage of xwinwrap, implying I'm entering the commands improperly.

[http://ubuntuforums.org/showthread.php?t=146533](http://ubuntuforums.org/showthread.php?t=146533)

[http://ubuntuforums.org/showthread.php?t=319503&highlight=xwinwrap+matrix](http://ubuntuforums.org/showthread.php?t=319503&highlight=xwinwrap+matrix)

[http://ubuntuforums.org/showthread.php?t=150240&highlight=xwinwrap+matrix](http://ubuntuforums.org/showthread.php?t=150240&highlight=xwinwrap+matrix)

these are what I've tried so far.  And none work.  Any ideas?

EDIT:  i've got it accepting my commands now, silly typo, but it does the screensaver on top of everything, so I can touch my windows.

---

### Post by da1nonlymikeo on 2007-03-16
iv been trying too. nothing so far :( i really want this to work.

---

### Post by mcduck on 2007-03-16
Here's the command I use to run xmatrix as background:```
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/xmatrix -window-id WID -delay 50000 -density 60
```.

For GLMatrix, use this one instead: ```
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -no-fog -density 4
```

in short, '-b' runs on background, and 'a' on foreground.

---

