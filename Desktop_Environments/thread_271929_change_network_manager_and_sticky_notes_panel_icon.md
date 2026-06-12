---
title: "change network manager and sticky notes panel icons?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by strabes on 2006-10-05
I have had some success in changing the panel icons for some things like the menu bar, deskbar, trash, etc, but have encountered problems with the network manager and sticky notes panel apps. I cannot find where the icons for these apps are located. Does anyone know where they are so I can change them? I'm going for a OS X look and this is pretty much the last thing for me to do. Thanks for any help

---

### Post by dannyboy79 on 2006-10-05
I can't tell you where they are but can suggest that you do a find for them fromthe terminal.

sudo find / -name nm*.png
or 
sudo find / -name network*.png

or something to that affect, then try the same for sticky*.png

---

