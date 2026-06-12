---
title: "Lost icons and right mouse menu on desktop"
date: 2009-11-23
forum: Desktop Environments
---

### Post by william_nbg on 2009-11-23
I've got a strange problem I can't figure out. I've recently upgraded to 9.10, installed awn dock, but removed it, and put gnome bar back. Now I don't have a desktop - no icons, no right mouse click menu. 

I tried removing my .gconf directory 
I looked in gconf-editor - show desktop is checked

if I call nautilus up in my terminal - the icons and menu function correctly.


Thanks in advance for any ideas.;)

---

### Post by william_nbg on 2009-11-23
Update:

If I alt/F2 and run nautilus after rebooting the desktop works fine for the rest of my session.

---

### Post by emigrant on 2009-11-23
login to another account and come back and see

---

### Post by william_nbg on 2009-11-23
Thanks for the reply.

I logged out, and logged in as root (it was the only other user account I had set up) As root, the desktop functioned correctly, but when I logged out as root an error message came up: something about not being able to log into dbus?? When I logged in again into my own user account the nothing has changed the desktop is still broken.

---

### Post by william_nbg on 2009-11-23
OK, I found a work around, but it's not a solution. I was thinking about a fresh install so I can upgrade to ext.4 and I'd also like to change my partitions a bit.

Work around, added a new startup application:

name: Nautilus fix

command: nautilus --no-default-window


Like I said it works, but it's only a work around. I'd like to know where the real culprit lies hidden. :rolleyes:

---

### Post by lavadisco on 2009-11-28
Bump. I'm having this exact same problem!

---

