---
title: "need help with compiz cube"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by spooky655 on 2007-12-04
for some reason i cant get the cube to work. ive had it working in gutsy b4 and feisty. when i first installed the settings manager i checked of the cube and the ctrl+alt switching worked but as soon as i enable another setting (might have been  rotate or skydome or something), the effects stop working. now i cant get the cube to work at all and if i set the apperance effects to none, turn the cube on and swicth back to custom, it goes white fer a minute and then goes back to none. I'd really appreciate it if some1 cud help me. heres a video of it:

[http://www.youtube.com/watch?v=3w6WqSo0rro](http://www.youtube.com/watch?v=3w6WqSo0rro)

---

### Post by smartboyathome on 2007-12-04
Post the output of compiz --replace.

---

### Post by spooky655 on 2007-12-04
(this is without cube ticked off):

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by spooky655 on 2007-12-04
something weird just happened. in synaptic it showed that compiz settings manager wasnt installed,`even thou it was. so i reinstalled it and the cube worked! but the skydome didnt so i disabled and reenable it and now the cube doesnt work anymore... (same thing happened where the effects disabled)

---

### Post by spooky655 on 2007-12-05
bump

---

### Post by spooky655 on 2007-12-05
bump

---

### Post by InsaneSith on 2007-12-06
Try getting XGL to start up and reboot your computer, run compiz --replace. Might not work, but whenever I had issues with certain effects going dead that seemed to work.

---

### Post by spooky655 on 2007-12-06
install xgl and it still doesnt work. but when i enabled the cube after typing "compiz --replace", it came up with a bunch of "A handler is already registered for the path starting with path[0] = "org""s in terminal

---

### Post by spooky655 on 2007-12-08
bump

---

