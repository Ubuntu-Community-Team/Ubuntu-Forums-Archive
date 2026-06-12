---
title: "&quot;Sorry, no mixer elements and/or devices found&quot; in Gnome"
date: 2005-01-04
forum: Desktop Environments
---

### Post by izmaelis on 2005-01-04
In terminal I can run alsamixer and I can edit volumes, but I can't edit volumes in Gnome (Applications -> Multimedia -> Volume Control). I receive "sorry, no mixer elements and/or devices found".
I noticed Gnome system notification sounds. XMMS is playing music (and I here it) too. Whats wrong?

---

### Post by jbh on 2005-01-04
Install gstreamer

sudo apt-get install gstreamer0.8-plugins

---

### Post by Quest-Master on 2005-01-04
Make sure you register it with gstreamer after that as well.

$ gst-register-0.8

---

### Post by izmaelis on 2005-01-05
```
sudo apt-get install gstreamer0.8-alsa
``` 
solved my problem. Thanks for replies.

---

### Post by ~zoey~ on 2005-02-06
I just installed ubuntu and I have no sound.

I get the same message, 'sorry no mixer elements and/or devices found'.

I can't run alsa mixer using the terminal and the volume control will not stay moved from the - setting.

Gstreamer is installed and registered and gives the message 'no pipeline found' when run.

Does anyone have any suggestions?

Thanks, zoey :confused:

---

### Post by ~zoey~ on 2005-02-06
OK, I figured out that ubuntu doesn't recognize my onboard sound, so I installed a sound card.  Now gstreamer will play a test sound or that is, it *looks* like it is playing one but I still can't hear anything.

I can pull up volume control now, and nothing is muted.  So what am I missing?

Thanks,  zoey   :confused:

---

