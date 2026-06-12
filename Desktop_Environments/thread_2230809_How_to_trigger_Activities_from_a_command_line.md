---
title: "How to trigger Activities from a command line?"
date: 2014-06-21
forum: Desktop Environments
---

### Post by narcisgarcia on 2014-06-21
I'm developing a web aplication to work at full screen in a touchscreen, and want to put in the web interface a button to go to see Gnome activities.
I want to link that button to PHP exec() function with the proper call.

---

### Post by narcisgarcia on 2014-06-21
I've found xdotool package to execute this:

env DISPLAY=:0 xdotool key Super

---

