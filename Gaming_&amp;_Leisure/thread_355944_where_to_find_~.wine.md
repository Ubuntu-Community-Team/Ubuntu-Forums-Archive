---
title: "where to find ~/.wine"
date: 2007-02-07
forum: Gaming &amp; Leisure
---

### Post by tjtansey on 2007-02-07
Where can you find the ~/.wine directory in the file system other than using the terminal?

---

### Post by Gibbs on 2007-02-07
By default it's a hidden directory in /home/user/.wine

Either: go to "Places > Home" and hit CTRL+H (to show the hidden files and go to it).

Or: In the terminal type ```
cd /home/**user**/.wine/
``` changing user with your username obviously ;)

---

### Post by tjtansey on 2007-02-07
That's the first place I looked, it's not there

---

### Post by meng on 2007-02-07
By the way, ~ is shorthand for /home/user
e.g. /home/tjtansey (if your username is tjtansey)
~/.wine is not created until you run wine for the first time

You can see hidden files/directories (all those beginning with .) in Nautilus if you press ctrl-H which toggles "view hidden files"

Or else you can, from the terminal
ls -la
which will show all hidden files/folders as well as unhidden ones.

---

### Post by Megatog615 on 2007-02-07
If it's not there, run wineprefixcreate.

---

### Post by tjtansey on 2007-02-08
ctrl-h did tthe trick

---

