---
title: "Key bindings work, but volume control doesn't control the right device"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Jhongy on 2006-07-24
Hello... Another question I'm afraid.

I've got sound up and workig no problem. What's more, the shortcut jkeys on my keyboard for vol up/down and mute were correctly mapped out of the box!

That is, when I press vol up/down or mute, I get a little OSD confirming that I have pressed those keys.

Since, for the mouse-driven volume control, and just about every other program, I have had to set the sound device (they all default to a USB device I have plugged in), I expect that the same thing is happening here.... only, I can't find anywhere to change this... help! :-D

---

### Post by Jhongy on 2006-07-24
bump, anyone?

---

### Post by stoffe on 2006-07-24
Got the same problem. Just got the volume icon in the tray sorted out, but this still doesn't work. I get the OSD for volume up/down and mute, but nothing actually happens.

---

### Post by Jhongy on 2006-07-24
Yesp, that's exact;y the issue. I'm sure most people have more than one sound-capable device in their system.

I found another thread which suggested putting option= lines in my alsa config file, but I tried that and lost sound altogether.

I expect I'm missing something simple here - there must be a way to set which sound device the shortcut vol up/down/mute functions control.

---

### Post by Jhongy on 2006-07-24
I wonder if reply #4 (setting all USB devices to option -2) to [this thread](http://www.ubuntuforums.org/showthread.php?t=130466&highlight=multiple+sound+devices) might do the trick?... Gonna try it out when I get home.

---

### Post by Jhongy on 2006-07-25
Yep, sorted:

Adding
```
options snd-usb-audio index=-2
```
to the end of /etc/modprobe.d/alsa-base seemed to do the trick. 

The first time I rebooted, the OSD didn't work at all for some reason, but I re-edited the file and tried again... works now. Maybe it was a typo I was too tired to see.


Now... the next challenge is to get my MCE remote working.....

---

