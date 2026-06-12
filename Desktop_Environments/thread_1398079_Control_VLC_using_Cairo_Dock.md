---
title: "Control VLC using Cairo Dock"
date: 2010-02-04
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-04
Hi all, is there a way to control the vlc media player using cairodock media player control. The default media players available in the list are audacious, banshee, rythmbox etc.

Thanks in advance.

---

### Post by fabounet on 2010-02-04
if you can control VLC remotely, you could make a DBus applet then.

---

### Post by hariks0 on 2010-02-04
There is one more thing I would like to have. The cairo with open gl consumes around 50 % of cpu and hangs frequently especially when I try to configure some items in the dock. The cairo dock without open gl does the same, only that it is a bit late in hanging.

---

### Post by fabounet on 2010-02-05
it depends on the animation level you set up.
the more you have animations/effects, the more it uses CPU (sounds logical).
except that with openGL, the CPU load stays quite low even with a lot of effects, but it depends on your graphic card/drivers.
also some effects are more heavy than others (the "capsule rotation" is, the firework too)
for instance with a GeForce7 I rarely go over 20% CPU even when moving the mouse very fast, but on my Dell Mini9 it's another story ^_^
so just set up the effects according to your PC power.

---

### Post by hariks0 on 2010-02-05
Now there is a bit improvement. I have slider applet detached from the dock and whenever cairo hangs and becomes invisible, I right click the slider applet and select the customised theme and apply it [which is already used]. Then the cairo dock comes again. I used to kill it using system monitor.

Any solution to control vlc using cairo ?

---

### Post by hariks0 on 2010-02-06
Thank you for your reply. But when i tried disabling autohide later, the problem stopped. Cairo-dock is not even appearing in the top 5 processes under cpu/ram usage. If autohide is enabled, the dock hides after some delay and never comes back. I disabled autohide and now only that the dock is there even if some window is maximised.

Also there is no improvement regarding controlling vlc with cairo.

---

### Post by hariks0 on 2010-07-23
Coming back to the original topic, can we control VLC using cairo applet for media player?

---

### Post by fabounet on 2010-07-23
the question is : does VLC has a remote interface (Dbus or whatever) ?

---

### Post by hariks0 on 2010-07-23
Actually my intention is to to control VLC with the music player applet of Cairo dock, which support some other players only. Remote control is still welcome though.

---

