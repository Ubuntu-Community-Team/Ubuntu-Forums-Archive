---
title: "Full screen apps with a mouse gesture? Help with hypotheses please :D[UNITY w/Compiz]"
date: 2012-06-07
forum: Desktop Environments
---

### Post by blackbird34 on 2012-06-07
Hi, wondering if one could explain a way to do this. I can't find an appropriate setting, or a way to configure one, in the CompizConfig Settings Manager, which has been doing a very good job so far. 
In the Wobbly Windows defaults, you can snap windows against the side or the top of your desktop to make them take half the screen or maximise. As one can also double click to maximise a window, what I would like Compiz to do would be : when i drag the window title bar upwards to snap and maximise, for it not to maximise but to fullscreen immediately.

Any idea how i could do that?

---

### Post by stinkeye on 2012-06-07
The resizing of windows when dragged to the edge is controlled by the  **ccsm > grid** plugin
but there is no fullscreen option.

You can use the **ccsm > commands** plugin
with xdotool to set a top edge + Rmouse click to make the focused window fullscreen.

eg: In the **ccsm > extra wm actions** plugin I have fullscreen set to Super+F12.
Then in **ccsm > commands** use the command...
```
xdotool key Super+F12
```
and set the button binding to top edge + mouse1.

Normal drag maximizing still works but to toggle fullscreen just click on the top edge.

May need to install xdotool...
```
sudo apt-get install xdotool
```

---

