---
title: "game toggle kde4"
date: 2008-11-19
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2008-11-19
so, Im trying to create a launch script to toggle compositing in kde4 so I dont have to remember to do it manually.  I found this command to turn compositing off:
kwriteconfig --file kwinrc --group Compositing--key Enabled false &

So, I wrote a script:

#! /bin/bash

kwriteconfig --file kwinrc --group Compositing--key Enabled false &
# turns compositing off
sleep 2 &
#
kwin --replace &
#
sleep 2 &
# obvious pause to allow kwin a few seconds
firefox &&
# application params and location here will hold script until exit
sleep 2 
# pause again
kwriteconfig --file kwinrc --group Compositing--key Enabled true &
#
#kwin --replace &
# turns compositing back on

Right now, Im just using firefox as a placeholder, it will be changed to the game I plan to run once I get it set up properly.

So, my problem is that the script turns compositing off, launches firefox, but then immediately turns compositing back on instead of waiting for firefox to exit.  Can anyone help me figure out what is going wrong here?

---

### Post by Perfect Storm on 2008-11-19
Instead of 

firefox &&

do

firefox 

instead

---

### Post by Naegling23 on 2008-11-19
thanks for the suggestion, but it doesnt seem to change anything...same problem.

---

### Post by Perfect Storm on 2008-11-19
Try check this script and you can rewrite to fit - [http://ubuntuforums.org/showpost.php?p=5770830&postcount=6](http://ubuntuforums.org/showpost.php?p=5770830&postcount=6)

---

