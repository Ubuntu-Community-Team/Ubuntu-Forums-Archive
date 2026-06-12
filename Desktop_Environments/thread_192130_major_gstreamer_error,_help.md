---
title: "major gstreamer error, help"
date: 2006-06-08
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-08
hey, last night I updated dapper with the update manager. and then I rebooted. Nautilus wouldnt reboot. Had to reinstall some libs (libnotify) and then reinstall nautilus. and now rhythmbox isnt working.

when I play a song, I get a X red icon next to the song item. and I get this message in right click / properties

Missing Element: "audioresample". Please check your GStreamer installation.

I opened synaptic and then searched for audioresample. Found nothing. What should I do? Should I re-install gstreamer? If so, how do I do that?

---

### Post by Hallavej on 2006-06-08
Breezy used gstreamer0.8 and Dapper uses gstreamer0.10. Think you shouldt open Synaptic and search for gstreamer. Then remove all the gstreamer08 packages and install all the gstreamer0.10 packages.

---

### Post by truenemesis on 2006-06-08
okay, well, that didnt work. thanks tho. any other suggestions?

---

### Post by truenemesis on 2006-06-08
come on, i need help here.

---

### Post by Hallavej on 2006-06-08
Sorry, that was my best guess. Did you try simply to reinstall rhythmbox?

---

### Post by truenemesis on 2006-06-08
um..i tried that in synaptic. rhythm is attached to the ubuntu desktop. if i remove the player, i remove ubuntu desktop according to my synaptic manager. any other ideas?

---

### Post by fordfan753 on 2006-06-08
Tried reinstalling all of gstreamer through synaptic?

---

### Post by truenemesis on 2006-06-09
no such luck. reinstalled everything. stil had an issue. Help, people! please.

---

