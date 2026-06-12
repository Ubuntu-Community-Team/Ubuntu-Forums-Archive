---
title: "column alignment and conky"
date: 2009-04-26
forum: General Help
---

### Post by sefs on 2009-04-26
Hi i am trying to get top cpu users to display in conky

but its misaligned...see attached photo.

the conky code I have looks like this...

```

$stippled_hr
${color lightgrey}Name PID CPU% MEM%
${color #ddaa00}${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey}${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey}${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey}${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color lightgrey}${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
$stippled_hr

```

I am using the tutorial here...
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

his code is the same thing but his is perfectly aligned ... but mine is not ... also see
[http://debaday.debian.net/wp-content/uploads/2007/08/conky.jpg](http://debaday.debian.net/wp-content/uploads/2007/08/conky.jpg)
His too is perfectly aligned

How can i too get mine perfectly aligned.

thanks.

---

### Post by VCoolio on 2009-04-26
Use something like ${goto 100} for the 2nd column, ${goto 150} for the 3rd column and ${alignr} for the last. Use try-and-error for getting the right numbers on the goto. Do that on each line; this would be the first:
${color #ddaa00}${top name 1}${goto 100}${top pid 1}${goto 150}${top cpu 1} ${alignr}${top mem 1}
Not perfect, but better. Check other conkyconfigs to copy their solutions. There is a big thread in the community cafe section.

---

### Post by unutbu on 2009-04-26
ubuntugeek's .conkyrc says

```
font arial
```

Arial is a proportional font, not a fix-width font.
However, if you look at his screenshots, you'll see the font being displayed is of a fixed-width. So whatever font he is using, it is not Arial. His system probably did not have "arial" installed, so it defaulted to a fixed-width font, unwittingly helping him in this case.

If you change "font arial" to
```

font mono
```
then I think you'll see the columns match up better, since mono is a fix-width font.

---

### Post by sefs on 2009-04-26
Ah yes the font was it in truth.  I switch to Monospace and all is well with the world.

---

