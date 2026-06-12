---
title: "trash_icon_visible still doesn't show Trash on desktop"
date: 2008-09-17
forum: Desktop Environments
---

### Post by virtualpt on 2008-09-17
Hi All,

Fairly new to Ubuntu, but loving it. Have got AWN configured & working, only problem is Trash-Can bug in AWN on Hardy, so I thought I'd put Trash-Can on the desktop, so that I can get rid of the top Gnome Panel (the only thing I need it for now is the Trash-Can!).

Have run sudo gconf-editor & navigated to apps/nautilus/desktop , then ticked trash_icon_visible, but no joy! No Trash-Can appears on the desktop. I've tried logging out & back in, & rebooting, but it still doesn't appear. Have searched forums & Googled, but can't find an answer, everything just says to do what I already have :-) Has anyone got any ideas, or can I add the Trash-Can to any other menu, so that I can get to it via AWN rather than have to keep the top Gnome Panel?

Many thanks :-)
Paul

---

### Post by mcduck on 2008-09-18
Don't run the gconf-editor with sudo. If you do that, you are opening the editor as root, which means that you are changing the root user's desktop settings, not your own.

(besides, even if you really wanted to use gconf-editor as root you should use gksudo, not sudo. sudo doesn't work correctly for graphical applications..)

If you are not sure if the comamnd you are running really requires root privileges try running it without sudo first. If the command needs root privileges you'll get a message telling you that.

---

### Post by virtualpt on 2008-09-18
Thanks mcduck, you are a star, it's fixed my problem & a great explanation too :-)

Paul

---

### Post by anotherdisciple on 2008-09-18
mcduck seemed pretty helpful... could you click the thank you button on his post and then mark this thread as "solved" under thread tools? Thanks!

---

