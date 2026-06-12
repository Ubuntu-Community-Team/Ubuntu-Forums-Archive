---
title: "Switching back and forth between GUI and Console mode"
date: 2009-12-24
forum: Desktop Environments
---

### Post by rpaskudniak on 2009-12-24
Greetings.

While trying to solve a problem with my non-functioning Gnome desktop, I made heavy use of Ctrl-Alt-F1 to get out of the GUI into console mode. I didn't think of that; it was listed in a solution.  I also discovered, reading an old, decrepit Linux book (_Linux: Complete Command Reference_, published in 1997) that Ctrl-Alt-F*[FONT="Comic Sans MS"]n[/FONT]* will switch me to console session number *[FONT="Comic Sans MS"]n[/FONT]*.

This is all quite interesting and useful if I'm trying to get out of an unresponsive GUI session.  But when I have done what I need in console mode (like removing the reason for the frozen GUI), I'd like to **_resume my GUI where I left off_**.

Not satisfactory solution: Restart the Gnome daemon ([FONT="Courier New"]sudo restart gdm[/FONT]) because it kills my session altogether and puts me back into the login screen.

What command or key combination will accomplish that?

Thanks much!

---

### Post by Mister.Vash on 2009-12-24
Depends on what you had to drop down to the shell to do.  If you didn't kill the gnome session, you should be able to return to it by pressing  Ctrl+Alt+F7

---

### Post by rpaskudniak on 2009-12-24
Thanks mucho!That worked quite well.

Of course, it does open the door for the curious, what the other Ctrl-Alt-F*n* keys will do. For example, while typing this I pressed Ctrl-Alt-F8 and found what looks like the output of some diagnostic that seems to be still running. The last line on the screen reads:
> [FONT="Courier New"]* Starting TiMidity++ ALSA midi emulation[/FONT]
What in tarnation does *that* mean? (And what in tarnation does *tarnation* mean? :P )

Is this documented anywhere?

BTW, timidity is a MIDI to WAVE converter/player.  I have no clue why it is running but that's the subject of another thread in another forum category.

Again, thanks much.

---

