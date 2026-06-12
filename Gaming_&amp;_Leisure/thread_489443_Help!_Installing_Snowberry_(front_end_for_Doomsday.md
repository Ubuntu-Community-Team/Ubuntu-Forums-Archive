---
title: "Help! Installing Snowberry (front end for Doomsday)"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by weblordpepe on 2007-07-01
Help!
Im trying to figure out how to install Snowberry in Ubuntu 7.04. I want to be able to use the Jdoom resource pack & so on.

Now I've been a good wee noob & RTFMed. [URL="http://dengine.net/dew/index.php?title=Installation#Snowberry_requirements"]http://dengine.net/dew/index.php?title=Installation#Snowberry_requirements
[/URL]
[LIST]
[*]I have python & wxpython (I think)
[*]I've downloaded snowberry from the SVN.
[*]I have edited snowberry.py to have a **#!/usr/bin/python ** line at the top.
[*]I have made it an executible.
[/LIST]

But now I don't understand what the instructions want me to do. I have tried running the snowberry.py file but I get:
```
Traceback (most recent call last):
  File "./snowberry.py", line 26, in <module>
    import language, ui, plugins, sb.profdb
  File "/home/pepe/Downloads/snowberry/ui.py", line 37, in <module>
    import sys, os, wx, string
ImportError: No module named wx

```
Help, save me Doomsday developers aah!  :cry:

---

### Post by asipi on 2007-07-02
check repositories for wxpython package (I don't know if any and no chance to check atm)
if do not find, try this link:
[http://www.wxpython.org/download.php]("http://www.wxpython.org/download.php")

---

### Post by weblordpepe on 2007-07-02
HAH!! 

You were totally right. Well done. Thanks heaps.

---

