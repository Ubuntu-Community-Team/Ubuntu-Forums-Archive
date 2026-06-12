---
title: "Lost default top right icons"
date: 2010-12-04
forum: Desktop Environments
---

### Post by h34e0f on 2010-12-04
accidentally removed - the default one with messages, chat, sound etc on. How do I get it back? Can't find it in the 'add to bar' list

:(

---

### Post by Swagman on 2010-12-04
rebuild top panel

Open a terminal (Ctrl + Alt + T) copy & paste, line by line (enter after each line)

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by h34e0f on 2010-12-04
Fantastic, thanks!

---

### Post by h34e0f on 2010-12-04
Oh, sorry to be a pain but I'm now missing my network icon :P

---

### Post by Swagman on 2010-12-04
Those commands I gave you set the top panel back to default.. Perhaps you need to reboot ?

---

### Post by h34e0f on 2010-12-04
DOH. Yes works - thanks a lot. I think I should learn to think before I post!

---

