---
title: "Stopping complize"
date: 2006-09-04
forum: Desktop Environments
---

### Post by toasted on 2006-09-04
I know the command now is compliz-start to get it running. That trips compliz-start shell script in //usr/bin

What would I do to stop compliz?
Is another script needed?

Also, once compliz is stopped - bear with me here - XGL is still running I think. Is XGL the window manager now rather than metacity? Is this how it works?

---

### Post by mushr00m on 2006-09-04
I can't remember where I picked up the hackery for my compiz-toggle script but here it is:

```

#!/bin/bash

#next line tests if compiz.real is started; if yes:
if ps -A | grep -e "compiz.real$" > /dev/null; then
#kills cgwd and starts metacity
        killall cgwd
        metacity --replace &

# if not then start compiz junk
else
        cgwd &
        compiz-start --replace gconf &  # changed with last compiz upgrade (0.0.13.44-0ubuntu1), compiz -> compiz-start
        xmodmap -e "keycode 22 = BackSpace Delete"  #I forget what this is mapping... or mapping out.
fi
```

I put this script in my panels and it toggles the starting and stopping of compiz/metacity....

does that help?
mushroom

---

### Post by toasted on 2006-09-04
What I did - 
made a script in usr/bin with your code in it called  compliz-stop. 

Called from a terminal  compliz-stop

It might shut down, but if it does it starts right back up. It does something though! The windows get transparent till you move them and then its normal again


compliz doesnt stay off

---

### Post by OffHand on 2006-09-04
That script is broken since the latest compiz upgrade.

---

