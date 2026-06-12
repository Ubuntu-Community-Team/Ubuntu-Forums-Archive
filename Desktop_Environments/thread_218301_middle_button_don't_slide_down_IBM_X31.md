---
title: "middle button don't slide down IBM X31"
date: 2006-07-18
forum: Desktop Environments
---

### Post by tomash_cz on 2006-07-18
Hello, could please help me how do i configure ubuntu so that i can use middle button in IBM X31 (trackpoint)? In windows when I press the middle button and than press trackpoint down, the window in browser or office slides down. Thank you for all suggestions. Nebie

---

### Post by aiiee on 2006-07-18
I also have an X31 and did the following based on a Google search
and it worked for me.

Add the following lines to /etc/X11/xorg.conf, under the "Configured Mouse" section, if not already there:
Option "Emulate3Buttons"     "true"
Option "EmulateWheel"        "true"
Option "EmulateWheelButton"  "2"
Option "ZAxisMapping"        "4 5"


save the file and restart X, and you now have Trackpoint middle button scrolling :)

---

### Post by ssalman on 2006-07-19
Hi, I was following this thread as I had the same question on my Thinkpad X20... your solution worked, thanks aiiee!!

---

