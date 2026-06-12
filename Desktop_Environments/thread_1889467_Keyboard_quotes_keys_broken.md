---
title: "Keyboard quotes keys broken"
date: 2011-12-01
forum: Desktop Environments
---

### Post by nshiell on 2011-12-01
When I type and I want a quote " or a single quote ' I have to type the key followed by the space bar.

All other fixes for this I have seen relate to older versions of Ubuntu, can anyone talk me through fixing this?

---

### Post by Copper Bezel on 2011-12-01
You're using the wrong keyboard layout - presently "US International (With Dead Keys)". If you need the International layout (including AltGr in place of Right Alt) and are using 11.10, you'll need ibus running; then you can change the Keyboard Layout in, well, Keyboard Layout (to "US International (AltGr Dead Keys)" or whichever suits you.) I'm pretty sure that once I had this set, I didn't need to do anything special to make the settings stick - ibus isn't added to my startup applications or anything.

You can find ibus and Keyboard Layout in the Dash (Unity or Gnome Shell.)

---

### Post by nshiell on 2011-12-01
Copper thanks for your advice, I'm still not sure what I need change to change the keyboard layout, I have a MacBook with English GB keyboard. What is it I need to do

---

### Post by Copper Bezel on 2011-12-01
Okay, you might not even need the ibus daemon, then. Open Keyboard Layout and select the Layouts tab. Click the "+" button. Select "English (UK, Macintosh)". Click Add, then select the old layout (which again I think is US or English "International (With Dead Keys)") and click the "-" button. Should be all done. = )

---

### Post by nshiell on 2011-12-01
Oooo it's finally working!
It's so hard to program without a working quotes key!
Many thanks

---

### Post by Copper Bezel on 2011-12-01
Very cool. = ) Yeah, I've had some issues with this in the past, too, and it's very frustrating until you figure it out. Just mark the thread as Solved, Thread Tools in the upper right. = )

---

