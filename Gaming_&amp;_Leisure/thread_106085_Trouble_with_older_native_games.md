---
title: "Trouble with older native games"
date: 2005-12-19
forum: Gaming &amp; Leisure
---

### Post by madjinx on 2005-12-19
im having some trouble with most of my loki native games, when started command returns this error:

root@darkstar:~# rune
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Rune (rune-bin). Is RUNE_DATA_PATH set?
root@darkstar:~#

i think alphacent is one of the few not giving me trouble.

So how do i set RUNE_DATA_PATH?

---

### Post by joshuapurcell on 2005-12-19
Try this:> jeremy@breezy:~$ RUNE_DATA_PATH=/needed/directory/path
jeremy@breezy:~$ echo $RUNE_DATA_PATH
/needed/directory/pathThe echo command is just to show you the system knows what the variable is... not needed to actually set the variable.

---

