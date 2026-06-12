---
title: "D-link DWLG630 with Atheros"
date: 2006-07-12
forum: Desktop Environments
---

### Post by analogdevices on 2006-07-12
I have a D-Link DWL G630 Wireless card with the atheros chipset, and it's acting kind of weird.. first of all, it's putting out blink-signals, which are as follows in a progressing order; the underscores represent blinks, and the dashes are there to keep the formatting



Link|Act
------_
-_
-_
-_
------_
------_
------_
-_
-_
-_

-_----_
-_----_
-_----_

and the it repeats.

---

### Post by tturrisi on 2006-07-12
I have several cards, one of which is a dlink 630G atheros.  Just popped in the card and 1 green light means card is recognized.  While connecting, the lights alternate blinks what looks like 3 times each, back & forth until connected, and when connected they both blink at same time.  So, if you see other than the last as I described then maybee your connection is going in & out.  May try setting the ap to a different channel.

---

### Post by lindyslack on 2006-07-12
I also use a D-Link DWl-G630 and I wrote a little shell script for wlanassistant.

from cammand prompt

nano wlan.sh

Then I entered

#!/bin/sh

sudo wlassistant

ctrl+o to save
ctrl+x to exit

Then I 

chmod a+x wlan.sh

and just run ./wlan.sh enter your password and wlanassistant launches as superuser and finds my wireless network and I click on mine and it connects... Had a hard time before I did this... Always trying to get it connected...

hope this helps!

---

### Post by analogdevices on 2006-07-13
thanks for the assistance guys, but I finally got it after meddling around for about 3 hours

---

### Post by mikecool on 2008-01-14
> **analogdevices said:**
> thanks for the assistance guys, but I finally got it after meddling around for about 3 hours

could you tell us how to work through it? I met the same problem, the adapter works well, but the blinking is boring.

---

