---
title: "scipts don't run"
date: 2005-07-08
forum: Desktop Environments
---

### Post by jodar on 2005-07-08
Few problems....

I've been progressing thru the excellent guide at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)


the problems I've run are:

-neither "echo -n mem > /sys/power/stat"
 nor "sudo echo -n mem > /sys/power/stat"

will run due to permissions issues?!?!?

also, when I put .sh scripts in my ~/.kde/Autostart/ directory they just open in KATE editor when it starts (same thing if I double click them).....

---

### Post by manicka on 2005-07-09
You need to make the scripts in your autostart folder executable. It's been a while since I've used KDE but basically you right click on the file, choose 'properties', click on the permissions tab and tick the checkboxes to make the file executable. 

Working from memory but the process is something like that

---

