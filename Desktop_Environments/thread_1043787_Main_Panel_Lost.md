---
title: "Main Panel Lost"
date: 2009-01-18
forum: Desktop Environments
---

### Post by PElizabethM on 2009-01-18
I am rather new to Ubuntu, and mistakenly let my younger cousin use my computer. She did not properly shut down (simply pressed and held the power button), and now my panels are gone. I've looked at other posts, and tried everything they've said to do, and my panels are not reappearing. Can anyone help me out?

---

### Post by albinootje on 2009-01-18
> **PElizabethM said:**
> I am rather new to Ubuntu, and mistakenly let my younger cousin use my computer. She did not properly shut down (simply pressed and held the power button), and now my panels are gone. I've looked at other posts, and tried everything they've said to do, and my panels are not reappearing. Can anyone help me out?

You can open a terminal, and then type exactly this :
```

killall -9 gnome-panel ; gnome-panel

```

Please post any errors or if this still doesn't show a panel.
It is also possible that the panel is there, but minimized, or hiding by the way.

---

### Post by PElizabethM on 2009-01-18
Thank you, that did work. However, now some of my applets are not working, specifically the eyes, the trash can, and the mixer. It is not extremely important, but a little bit of an inconvenience.

---

### Post by albinootje on 2009-01-18
> **PElizabethM said:**
> Thank you, that did work. However, now some of my applets are not working, specifically the eyes, the trash can, and the mixer. It is not extremely important, but a little bit of an inconvenience.

You mean that the applets are gone ? 
Or do they refuse to start with some error ? (If so, what are the errors ?)

If they're just gone, you can add them to the panel again, with the right click, and "add to panel".

---

### Post by PElizabethM on 2009-01-18
It is an error. Specifically, it says 

The panel encountered a problem while loading
"OAFIID:GNOME_GeyesApplet".
Do you want to delete the applet from your configuration?

The exact same thing with the different applet names for all three.

---

### Post by zman58 on 2009-01-18
Perhaps if you just go ahead and delete them from your configuration, then go back into the panel properties and add them back in. Not sure, but it just might work.

---

### Post by adamlau on 2009-01-19
If that does not work, try reinstalling the problem applets.

---

### Post by PElizabethM on 2009-01-19
I did both of those, and am still getting the same error.

---

