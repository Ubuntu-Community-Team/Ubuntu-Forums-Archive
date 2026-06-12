---
title: "problems with sound"
date: 2005-11-21
forum: Desktop Environments
---

### Post by rjs on 2005-11-21
For some reason my computer is automatically on mute at start up. It doesn't look like it is mute, but then if i toggle the mute it starts working. Anyone got any ideas?

As a follow up, how do i get the volume icon into the system tray? I had it when i was using hoary, but it isn't there now (with breezy).

paz y amor,
-rjs.

---

### Post by Tiede on 2005-11-21
To get the volume icon in the system tray, jist right-click on it, choose Add, scroll down to the Volume icon and you're done!
For the mute thingy,  think you might have saved your session with the Volume muted.
Just unmute, logout remembering to check the save this session box, and log back in :)

---

### Post by rjs on 2005-11-21
I've tried the save session thing. Didn't work.

Right clicking on items in the system tray gives me their menu, clicking on the blue triangle hiding thingo just gives me the panel menu, and clicking on the applet handles gives me move, remove, configure. Configure just lets me automatically hide things. I can't see any add option, unless you are talking about the add to panel option, in which case i can't see the applet that i am looking for. It's just a pic of a speaker which you click to toggle mute, and has a little pop up volume control.

paz y amor,
-rjs.

---

### Post by FLeiXiuS on 2005-11-21
```
sudo alsamixer
```

Then unmute any thing that should be.  Fix the mixers and what not then push ESC.

Now save the settings!

```
sudo alsactl store
```

---

