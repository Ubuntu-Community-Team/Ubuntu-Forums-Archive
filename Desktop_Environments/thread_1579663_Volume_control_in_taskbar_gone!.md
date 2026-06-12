---
title: "Volume control in taskbar gone!"
date: 2010-09-22
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-09-22
Booted up in Lucid this morning to find all my volume control has vanished!
I cant re-add to the panel, the volume applet isnt there to re-add! If I go to system/preferences/sound I get the error: Waiting for sound system to respond and nothing happens. If I go into command-line and try running gnome-volume-control-applet, I get the error: WARNING **. connection failed, reconnecting.. this goes on without any further result.
Anyone got any ideas? the sound is working.. I just have no volume control other than the one on my speakers.
Steve

---

### Post by mister_p_1998 on 2010-09-22
Sorted it!
my fault! Id been playing around with permissions, 
sudo chmod 644 ~steve/.dmrc fixed it...
Doh!
Steve

---

### Post by linux-hack on 2010-09-22
juste put a resolved to your post :)

---

### Post by mister_p_1998 on 2010-09-23
> **linux-hack said:**
> juste put a resolved to your post :)

How do you do that?

---

### Post by Elfy on 2010-09-23
Thread tools - mark as solved

---

