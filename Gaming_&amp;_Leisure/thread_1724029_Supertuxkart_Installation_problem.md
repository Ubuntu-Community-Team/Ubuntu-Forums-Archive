---
title: "Supertuxkart Installation problem"
date: 2011-04-07
forum: Gaming &amp; Leisure
---

### Post by zephyr20 on 2011-04-07
Hi guys, I am a newbie at this Ubuntu thing, I installed it because windows sucked on my laptoP BUT LNUX IS AWESOME! Except I cant install software that did not come preinstalled.  
Whenever I try to install supertuxkart .deb amd64 it says wrong architecture, so I tried i386 .deb fle and I got the error message "dependncy is not satifiable: Freeglut 3.  So I try to install freeglut 3 i386 and I get another error message, this one saying dependency is not satisfiable:freeglut3 = (2.6.0-0ubuntu2)
what a  doing wrong?
Thanks for reading.

---

### Post by DangerOnTheRanger on 2011-04-07
There is an easy way to install SuperTuxKart 0.7 in Lucid:

[LIST]
[*]Open up **System > Administration >Software sources**
[*]Click on the **Other software** tab
[*]Click **Add...**
[*]In the **APT line **text box, enter the following:
[/LIST]
```

deb http://ppa.launchpad.net/stk/dev/ubuntu lucid main

```
[LIST]
[*]Click **Close**
[*]Open the Ubuntu Software Center
[*]Under the **Get Software **tree, select **SuperTuxKart Dev**
[*]Select **supertuxkart**
[*]Select **More Info**
[*]Click **Install**
[/LIST]
There you go!

If you're running Maverick, just do:

```

sudo apt-get install supertuxkart

```(Note that this works for Lucid, if you want STK 0.6. But STK 0.7 has a bunch of new karts and features, and looks much better)

instead. The reason for this is that STK 0.7 was released to late to be included in Lucid, but early enough for inclusion in Maverick.

---

### Post by zephyr20 on 2011-04-08
Thanks for the quick reply, I was just bout out the door so my english was pretty rubbish :) I type in the 
"sudo apt-get supertuxkart" and i get the message E: Invalid Operation supertuxkart" 
By the way I am running Maverick, cheers

---

### Post by samigina on 2011-04-08
sudo apt-get **install **supertuxkart

Have you tried the Software Center?

---

