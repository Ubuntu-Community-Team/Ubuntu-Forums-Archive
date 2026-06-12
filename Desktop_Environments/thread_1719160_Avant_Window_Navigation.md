---
title: "Avant Window Navigation"
date: 2011-04-01
forum: Desktop Environments
---

### Post by magodiafano on 2011-04-01
Hello I have a question about AWN.
I don't like the fact that, when the dock is hidden because I am using other windows such as opera, it appears again when, with the mouse's icon, I go across the region where the dock is. 
Is there a way to solve it? I want that, if there is another window open, the dock is always hidden.

And then: what is the difference between "intellihide" and "window dodge" for the behaviour??

---

### Post by fafbox on 2011-04-01
you can try to set awn preferences
or
you can set awn visibility by setting a compiz general command to run the following bash script when you touch that specific desktop edge:

#! /bin/bash
wmctrl -r avant-window-navigator -b add,above &
sleep 4 # set here the amounts of seconds between activating awn-dock and deactivating it
wmctrl -r avant-window-navigator -b remove,above &

Hope this would help you or others...

---

### Post by magodiafano on 2011-04-01
> **fafbox said:**
> you can try to set awn preferences
or
you can set awn visibility by setting a compiz general command to run the following bash script when you touch that specific desktop edge:

#! /bin/bash
wmctrl -r avant-window-navigator -b add,above &
sleep 4 # set here the amounts of seconds between activating awn-dock and deactivating it
wmctrl -r avant-window-navigator -b remove,above &

Hope this would help you or others...

ok I'm gonna try this.
But could you tell me what is the difference between intellihide and windows dodge?

---

### Post by Copper Bezel on 2011-04-01
Intellihide is what Compiz is now (more usefully) calling "Dodge Active Window"; the dock appears if the presently selected window would not be obscured by it. Window Dodge makes the dock disappear if *any* window overlaps it.

I don't understand your initial question, though. Are you saying that you want the dock to stay below other windows at all times?

---

### Post by magodiafano on 2011-04-01
> **Copper Bezel said:**
> Intellihide is what Compiz is now (more usefully) calling "Dodge Active Window"; the dock appears if the presently selected window would not be obscured by it. Window Dodge makes the dock disappear if *any* window overlaps it.

I don't understand your initial question, though. Are you saying that you want the dock to stay below other windows at all times?

I am so sorry because I am italian.
Yes, I want the dock to stay below other window at all times.

But I solved my problem. I have just discovered that the dock appears if the mouse's icon i go down (in the end of the screen).

---

