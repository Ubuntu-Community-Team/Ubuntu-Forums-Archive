---
title: "Terminal text colour scheme -- what does it mean?"
date: 2008-12-04
forum: General Help
---

### Post by PaulFXH on 2008-12-04
I have a folder full of drivers and another full of symlinks to these same drivers.
When I look at the symlinks folder in a terminal, all of the driver links are coloured light blue, except for one which is orange/yellow on a black background.
As it happens the driver whose link has a different colour to all the other links is not performing well (actually not at all).
I believe the colour code may help me identify what the problem is but I can't find any reference to this (other than this brief and incomplete [thread]("http://ubuntuforums.org/showthread.php?t=334555")).
Can anybody help?

---

### Post by scorp123 on 2008-12-04
> **PaulFXH said:**
> When I look at the symlinks folder in a terminal, all of the driver links are coloured light blue, except for one which is orange/yellow on a black background. Sounds like a dead symlink to me ... If you follow the link (e.g. look at the file the link is supposed to point to): is the file really there? If I had to guess I'd say no ... it's a dead symlink you're looking at (the link is pointing to a file that doesn't exist).

---

### Post by PaulFXH on 2008-12-04
Thanks for the reply.
Certainly the symptoms agree that the symlink is dead. However, I formed the link myself to a file that is definitely present -- I unzipped and placed it in the folder pointed to by the link.
However, be that as it may, is there any document that I can refer to that specifically mentions that this colour arrangement (yellow on black background) is indicative of a non-functioning link?

---

### Post by scorp123 on 2008-12-05
> **PaulFXH said:**
> However, I formed the link myself to a file that is definitely present Are you sure you did it right?

As for the colors: According to Google this command spits out what's configured: ```
dircolors --print-database
```

If I do that on my system I get (irrelevant parts are left away):
```
...
...
# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
[COLOR="RoyalBlue"]# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white[/COLOR]
NORMAL 00 # global default, although everything should be something.
FILE 00 # normal file
DIR 01;34 # directory
LINK 01;36 # symbolic link. (If you set this to 'target' instead of a
 # numerical value, the color is as for the file pointed to.)
...
**[COLOR="Red"]ORPHAN 40;31;01[/COLOR]** [COLOR="Red"]# symlink to nonexistent file, or non-stat'able file[/COLOR]
...

``` According to the given explanation above regarding colors the color code for a dead symlink is "40;31;01" which translates into:
[INDENT]40 = black background (as explained above)
31 = red foreground
01 = bold[/INDENT]

As I said ... dead symlink ;)

---

