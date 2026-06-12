---
title: "Can't View MPG Files"
date: 2005-12-25
forum: General Help
---

### Post by Unit #134679 on 2005-12-25
I installed the multimedia codecs and tried to view movie files. When Totem runs and plays, it just shows a blue screen

---

### Post by kaamos on 2005-12-25
Try selecting a different video output with this command in terminal
```
gstreamer-properties
```
Also try installing vlc or mplayer. Hope this helps!

---

### Post by Unit #134679 on 2005-12-25
Which video output should I use? I tried using SDL but no cigar

---

### Post by kaamos on 2005-12-25
Try different ones.. I think xv or X11 should work.

---

### Post by Unit #134679 on 2005-12-25
None of them are working

---

### Post by kaamos on 2005-12-25
install mplayer (sudo apt-get install mplayer) and try with that. If it does not work, try selecting different video outputs in mplayers preferences.

You do have only one monitor right?

---

### Post by Unit #134679 on 2005-12-25
It seems to be working now.....I have no idea how. Thanks

---

