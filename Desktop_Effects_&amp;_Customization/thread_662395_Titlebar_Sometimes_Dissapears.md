---
title: "Titlebar Sometimes Dissapears"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by vahnx on 2008-01-08
I'm pretty sure it's called the title bar, the one with minimize, maximize, and close. Well sometimes it seems to dissapear, not often, but sometimes. Then I have to ctrl+alt+backspace and log back in. Anyone know of a fix? I'm using compiz. Here's a screenshot:

[IMG]http://img160.imageshack.us/img160/5379/helpyz0.png[/IMG]

---

### Post by nwpuliuhs on 2008-01-08
I have the same problem,and another one,
I echo the following command to /etc/profile
# Tray evolution automaticly
if [ "$(ps -A | grep evolution$ )" = "" ]; then
        alltray evolution&
fi 
# Run stardict automaticly
if [ "$(ps -A | grep stardict)" = "" ]; then
        stardict&
fi
Hoping they can start automaticly,Mostly they work well,but sometimes
they will be missed, even if the "titlbar" starts successfully.
Waiting for Solutions.

---

### Post by vahnx on 2008-01-13
This is still happening, here is another screenshot, if anyone knows of a fix, do tell ;)
PS Imageshack crashes in Ubuntu and Opera o.O WTF Photobucket is also crashing... looks like I should post somewhere else for that..
[img]http://www.uploadhouse.com/fileuploads/1063/1063130f81f72addd64bbe3efefefa71ec4f80b.png[/img]

---

### Post by Gigamo on 2008-01-13
That is most likely Compiz crashing... Have you tried running "compiz --replace" again after that happens?

---

### Post by breaking on 2008-01-13
"compiz --replace" did the trick for me. 

Thanks :-)

---

