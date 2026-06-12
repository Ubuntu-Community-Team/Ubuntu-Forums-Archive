---
title: "multiple terminal short cuts"
date: 2012-09-21
forum: Desktop Environments
---

### Post by confusedstingray on 2012-09-21
I monitor many servers
i would like to have multiple terminal short cuts on my desktop 
that use different icons and different login scripts.
some specs;
ubuntu 12.04 desktop
unity desktop 


i tried to do this, 
 and the first short cut worked,
 them i created a second one and the first one became a clone of the second
tried to change the first one back and the second became a clone of the first one
the short cuts become the same no matter how many i created.

any help would be great.
Thanks in advance,

---

### Post by spier on 2012-09-22
confusedstingray,

same issues resolved through a tricky way::lolflag:

Created some launchers through alacarte, say  
```
gnome-terminal  -e 'bash -c "ssh someone@somewhere"'
```
then, logged to Gnome Classic, just dragged the created launchers from gnome's main menu to the desktop.

Now, back to unity, I get working desktop shortcuts.

Hope it helps!;)

---

### Post by confusedstingray on 2012-09-23
I'll try it and see, thanks!

---

### Post by conradin on 2012-09-23
Im still in Lucid, using gnome2 where there is the nifty application launcher. I put all those sessions up in the panel and it keeps things real neat, and its all 1 click. In Unity, theres no panel! but I think you can still use:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

stuff like ssh, I let it ask me for a password. so i give it a command like:
```
ssh -X -p 793 user@123.123.123.123
```

On the other hand, Ive also made little scripts with things like bash, and Expect, that spawn terminal windows and commands. It wouldn't be too much more difficult to customize their icons. 

Save a file and make it executable:
something like:
```

#!/bin/bash
ssh -X -p 793 user@123.123.123.123
```

you could do tsclient, rdesktop or anything else just as easily.

---

