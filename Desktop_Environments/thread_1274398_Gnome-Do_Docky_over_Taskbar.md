---
title: "Gnome-Do Docky over Taskbar"
date: 2009-09-24
forum: Desktop Environments
---

### Post by Thomas Kenobi on 2009-09-24
For starters, hello from a new Ubuntu user, former windows acolyte :P

Now to my issue:
I'm using the Docky theme of Gnome-Do, set on auto hide, and what I'm trying to do is to have the docky pop-up over the existing bottom taskbar. However the problem is, that the docky may pop-up behind the taskbar instead, depending on which has focus.
To clarify:

Sometimes (if I click the taskbar first) this happens:
[[IMG]http://img33.imageshack.us/img33/3233/screenshot1rt.th.jpg[/IMG]]("http://img33.imageshack.us/i/screenshot1rt.jpg/")

Whereas I would like this:
[[IMG]http://img80.imageshack.us/img80/8823/screenshottf.th.jpg[/IMG]]("http://img80.imageshack.us/i/screenshottf.jpg/")


Is there any way to force the bottom taskbar to always stay behind the docky? Or possibly to force the docky to always stay on top, although that might present its own set of problems.

---

### Post by Fzang on 2009-09-24
First of, why would you have that taskbar? Move it to the top, or don't use Gnome-do, you're defeating the purpose of the app.

Now, go ccsm, window rules, and set gnome-panel to "always below". I'm not sure if these are the actual steps, I'm on Windows atm so I can't check.

---

### Post by Thomas Kenobi on 2009-09-24
Works like a charm, thanks!

Now about why I'm using it this way. I have too many icons to put in just the top taskbar, so I need both. I have removed the application buttons from the bottom taskbar (I use the docky for that) and I'm using it for some other functions instead (system resource monitoring, etc...). The part directly underneath the docky is essentially empty, but I'm keeping it for aesthetic purposes.

---

### Post by chriskin on 2009-10-16
since i find the same problem, what must i write in compiz and where? there is no always below option as fas as i have seen :S

---

### Post by Pawka on 2009-11-01
By setting "always bellow" to panel not only Do, but also other windows will overlap over panel. I don't like this so I better suggest set "Above" only to to "Gnome-Do". 


@chriskin: Just open CompizConfig Settings Manager, find and enable (if it is not) "Window Rules" plugin and into field "Above" type "class=Do". You can also grab application by pressing "+" button and then "Grab".

---

### Post by chriskin on 2009-11-01
> **Pawka said:**
> By setting "always bellow" to panel not only Do, but also other windows will overlap over panel. I don't like this so I better suggest set "Above" only to to "Gnome-Do". 


@chriskin: Just open CompizConfig Settings Manager, find and enable (if it is not) "Window Rules" plugin and into field "Above" type "class=Do". You can also grab application by pressing "+" button and then "Grab".

i have already found this
thanks anyway though :)

---

### Post by ben2talk on 2011-07-07
I messed around a while, restarted compiz and fiddled some more - then I restarted docky and it was fine.

I added it to my 'refresher' script:

#!/bin/bash
#
# Script to refresh apps
killall docky
killall conky
sleep 0.25
conky -d -c /home/ben/Admin/CONKY/short.conky
sleep 0.25 docky

I made a launcher in my 'admin' folder and dragged a copy to my panel - so hopefull if I ever see this again one click will fix it...

---

