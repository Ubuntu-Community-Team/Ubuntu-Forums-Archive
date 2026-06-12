---
title: "No Volume Control"
date: 2005-04-11
forum: Desktop Environments
---

### Post by xjimtx on 2005-04-11
Hello out there
First time usin Ubuntu, liking it so far. Only problem im having is i noticed my volume control was missing from the panel. I tried Apps/Sound & Video/Volume Control but i get this error msg 

Registry is not present or it is corrupted, please update it by running gst-register

Im using built in sound - AC97 audio controller, if that helps any

Appreciate any suggestions
Jim

---

### Post by dcast on 2005-04-11
Just right click on the panel where you want the control, a cascading menu pops up (or down) and select "add to panel". A list should appear and you can scroll through and add your volume control and all kinds of other neat stuff.  :grin:

---

### Post by xjimtx on 2005-04-11
I wish it was that easy, nothing happens when i try the add the applet. The thing is, I do have sound, its just not loud enough and Id like to turn it up

Jim

---

### Post by c_dog on 2005-04-11
Some sound cards allow for multiple hardware mixers that can run at the same me. You may need to increase the base volume on the each of the mixers. Right-click the volume icon>Open Volume Control> File>Change Device and see if there is a mixer for  each ALSA and OSS. Check to see if their setting on each of the channels is at least 90%.

---

### Post by xjimtx on 2005-04-12
Thx c_dog
I ended up fixing the problem while adding some more gstreamer packages

Jim

---

