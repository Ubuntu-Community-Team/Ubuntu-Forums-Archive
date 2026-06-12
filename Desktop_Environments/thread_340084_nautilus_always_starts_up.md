---
title: "nautilus always starts up"
date: 2007-01-16
forum: Desktop Environments
---

### Post by odysseus.lost on 2007-01-16
Hi,

no matter what I do, on my startup there is always one nautilus window opening. In my .gnome2/session file there is the following:

```

3,id=117f000001000116254708400000050260003
3,RestartStyleHint=2
3,Priority=40
3,Program=nautilus
3,CurrentDirectory=/home/gats
3,CloneCommand=nautilus --sm-config-prefix /nautilus-hmNi8w/ 
3,RestartCommand=nautilus --sm-config-prefix /nautilus-hmNi8w/ --sm-client-id 117f000001000116254708400000050260003 --screen 0 

```

But if I remove that and decrement all the first integers on the subsequent processes results into having a broken desktop in which the background image is not shown, the icons on my desktop are not shown and in general my desktop is unresponsive.

Any clues?

~Thanks.

---

