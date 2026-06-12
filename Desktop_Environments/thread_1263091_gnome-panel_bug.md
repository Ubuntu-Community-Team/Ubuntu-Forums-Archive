---
title: "gnome-panel bug"
date: 2009-09-10
forum: Desktop Environments
---

### Post by ManDay on 2009-09-10
Hello, due to the rather small dimensions of my screen I've set my panel(s) to auto-hide but it is a little buggy when trying to bring it back.

The current situation is that you can only bring it back by hovering over the part which is not hidden - so if you set the auto-hide to completly hide the panel there is no way of bringing it back. It would be better if you could separately configure an area in which the panel gets triggered to come back. furthermore, even as it is right now is quite buggy. the panel does NOT quite come back when you hoover over what'S left of it. instead (and this seems to be somewhat lousy coding to me) it only comes back if you touch tbe border of it. you ask what's the problem with that? well, usually that wouldnt make much of a difference since to hover over the panel itsself you would first have to cross its border, logically thinking. unfortunally

1.) if you mouse your mouse too quickly (which is about the nomral speed) you get to hover over the panel without the "border-trigger" noticing it -> no panel for you

2.) its only the border towards the center of the screen. if, however, the panel is not fully expanded, you can move your mouse in from the side -> no panel for you


its kinda sad that gnome at this point still suffers from thus uncecessary bugs.

---

### Post by mcduck on 2009-09-10
I agree that the unhiding seems to act a bit buggy.

But what comes to inability of unhiding the panel if you hide it completely, that's not going to happen. Since you can't hide it completely, the minimum hidden size is 1 pixel and trying to use lower value will still give you that 1px size..

Triggering the unhide effect from outside of the program's window could be at least a bit problematic, and since the hiding/unhiding used to work absolutely fine some time ago I don't see reason for that kind of change. Fixing the current behavior should be good enough.

Actually I have no problems at all with horizontal panels, but vertical ones seem to have problems detecting when the mouse is over the panel. Only moving the mouse to very bottom of the screen seems to work as it should.

Edit: now that I tried it again, the problems seem to exist only on the right side of the screen, where I'm able to move the mouse cursor completely out from the desktop. If done too quickly it moves over the and out from the desktop without spending enough time over the panel to unhide it. Panels in any other location don't have this problem since the cursor isn't able to move that far out of the screen. Also, disabling Compiz solves the problem and even panels on the right side of the screen unhide without any hiccups..

---

### Post by ManDay on 2009-09-11
I want to prevent my panels from taking up "maximize" space yet dock them to one side of the screen. Unfortunally, as soon as either the x or y pos of a panel goes 0 gnome will reserve the space for the panel and windows will not maximize into it. is there a way of setting it so that the oanel is ony "on top" but doesnt take up space?

---

