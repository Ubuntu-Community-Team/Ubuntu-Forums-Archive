---
title: "Is there  a solution?"
date: 2009-10-03
forum: Gaming &amp; Leisure
---

### Post by Daylon on 2009-10-03
I need a working Auto mouse clicker than will click every 2 seconds in the same spot, is this possible to have in Linux? I have tried to wine most programs and they didn't work too good for me. Anyone have any ideas?

---

### Post by Shibblet on 2009-10-03
> **Daylon said:**
> I need a working Auto mouse clicker than will click every 2 seconds in the same spot, is this possible to have in Linux? I have tried to wine most programs and they didn't work too good for me. Anyone have any ideas?

I'll help with what I can...

I don't know exactly how to do this, but I think you need a macro program of some kind.

---

### Post by ermeyers on 2009-10-03
> **Daylon said:**
> I need a working Auto mouse clicker than will click every 2 seconds in the same spot, is this possible to have in Linux? I have tried to wine most programs and they didn't work too good for me. Anyone have any ideas?
```

apt-get install xdotool

```annoying_enough_mouse.sh
```

#!/bin/sh -x
##

while true
do
   xdotool getmouselocation
   xdotool mousemove 100 100 #x y pos
   xdotool click 1 #button 1
   sleep 5
done

```

---

### Post by hal10000 on 2009-10-03
I found three tools in the repositories that you might take a look at:
1.) mousetweaks
2.) mouseemu
3. xdotool

i don't know anything about these tools, but they are used to simulate mouse buttons.

[EDIT] sorry, i didn't look to your last posting.

---

