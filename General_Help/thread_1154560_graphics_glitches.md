---
title: "graphics glitches"
date: 2009-05-09
forum: General Help
---

### Post by St Stephen on 2009-05-09
I am getting a lot of distortion of images and videos; is this a symptom of the ati discrepancies or is it something else that (hopefully) can be fixed? The shot attached is the result of just opening an image file, but the bug also occurs when watching videos in my browser.  It only seems to happen on the lower half of the screen - when the video or image is moved above a certain point on the screen the image becomes clear (but the static stays on the bottom half of the screen).
Any help would be awesome
Im running Jaunty 32bit with an ati x1400 mobility

---

### Post by KhurramM on 2009-05-09
run on cli

metacity

also change the default window manager in gconf-editor

to /usr/bin/metacity

I hope the problem would be resolved.

---

### Post by St Stephen on 2009-05-09
> **KhurramM said:**
> run on cli

metacity

also change the default window manager in gconf-editor

to /usr/bin/metacity

I hope the problem would be resolved.

Could you elaborate on this a little more? What do you mean by "run on cli?" Where in the gconf-editor can I change the default window manager?
Thanks

---

### Post by St Stephen on 2009-05-09
ok well i just found the option in gconf-editor, but its already set to /usr/bin/metacity

---

### Post by KhurramM on 2009-05-09
run on the command prompt AKA gnome-terminal

metacity

hope it works. U will have to wait for the changes. It takes time on my PC. Cant say about yours.

---

### Post by St Stephen on 2009-05-09
yeah that seemed to get it, thanks for the help

---

### Post by Tipped OuT on 2009-05-09
Remember not to expect everything to be perfect when it comes to drivers on Linux, especially open source.

---

