---
title: "Kill windows auto-expansion"
date: 2011-09-03
forum: Desktop Environments
---

### Post by orangep on 2011-09-03
Both Gnome and KDE now have window auto-expansion, which is extremely annoying and inconvenient. Whenever I shove a window against the edge of the screen, the window jumps to full screen and blocks all other windows.
I shrink it back down, and that moves it back to where it was before I moved it. So I reposition it again, and it jumps to full screen again... and again, and again...

I cannot find any setting to disable that "feature".
I want to permanently disable such behavior.
Any ideas?

---

### Post by stinkeye on 2011-09-03
There is a setting in dconf-editor which controls the appearance of the Dash, Launcher and also the Window Management behaviour.
dconf-editor is contained in the package **dconf-tools**.
This is using 11.04 Unity.

---

### Post by orangep on 2011-09-03
Okay, I'll go check that out. Thanks.

---

### Post by xadder on 2011-11-09
has anyone solved this in Unity (11.10)? I haven't tried installing dconf-tools, but I assume that something in ccsm should control this now?

I agree with the poster - very annoying. The default should be that windows stay as they are unless told otherwise.

---

### Post by Copper Bezel on 2011-11-09
Turn off the Grid plugin.

---

### Post by xadder on 2011-11-09
Thanks! Seems to work. 

A problem with ccsm is that there is no help system there, and the mouse overviews essentially contain no information, so it was hard to know what "Grid plugin" meant. I could RTFM, but that is a lot to read.

---

### Post by Copper Bezel on 2011-11-09
Yeah, sorry. CCSM makes me think of someone's garage; an organized mess that makes sense only to whoever put it together in the first place. Since I've spent a lot of time dinking with settings in there, I've just become used to it. I'm glad you found it, though. = )

---

