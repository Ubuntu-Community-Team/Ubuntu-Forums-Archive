---
title: "Multi Workspace - Window swapping"
date: 2007-09-21
forum: Desktop Environments
---

### Post by wakeboarder3780 on 2007-09-21
Greetings all.  I saw one other post about this back in 2006 that didn't receive any replies.  I was wondering if perhaps now this far along there were more options out and perhaps this is now an option buried somewhere I don't know about.

What I want to do:
Anyone familiar with fluxbox will recognize immediately what I want to do.  I want to be able to drag a window from one workspace to the other (both by dragging it to the far left of the screen, which should drop a workspace, or the far right of the screen which should go up a workspace AND I also want to be able to start dragging the window and just hit my bound key string to jump to another workspace, which should bring me to that specified workspace, and then I can let go with the mouse and BOOM, window is on a diff workspace)

This is extremely handy for managing multiple work stations and I have found that I am not even using multiple workstations simply because there is no fast way to warp windows to a specified workspace.

Anyone know of this option?  If not, how can we request it?  It can't be that hard to implement, plus fluxbox has had it "forever", we should get it too :)

---

### Post by vikram on 2007-09-21
Not sure about the mouse but I use key board shortcuts to move windows to different workspaces. The option to bind these actions to keyboard shortcuts is available in KDE not sure about GNOME. Which DE are you using ?

---

### Post by wakeboarder3780 on 2007-09-21
I am using Gnome.  I believe this is what you meant by DE.  Whatever comes default with Ubuntu, I don't run KUbuntu or anything.  Hope this helps.  If not I could probably do some digging and write some scripts to swap the active window to workspace whatever, but I would rather have the action as I described above.  I assumed it would be possible, please everyone give me your feedback.

---

### Post by Wolki on 2007-09-21
> **vikram said:**
> Not sure about the mouse but I use key board shortcuts to move windows to different workspaces. The option to bind these actions to keyboard shortcuts is available in KDE not sure about GNOME. Which DE are you using ?

Gnome has a wide variety of keyboard shortcuts you can set for workspace actions as well, including moving into a direction and moving to a certain workspace. They do not work while dragging, though.

You can have edge-flipping with an add-on called brightside; I don't use it though and don't remember anymore whether it also allows moving windows to workspaces by edge-flipping.

---

### Post by wakeboarder3780 on 2007-09-22
Wolki: yes I believe this would allow me to get the edge flipping response.  However what I used 99% of the time was the fact that I could activate a window via initiating a drag and use my set key values to switch to another workspace and I would be able to move the "dragged window" to that desktop and simply "let go" of the mouse and the window would stay on that desktop.

I can achieve slightly the same action by setting keys to move the active window to a different workspace and then hitting my key seq to bring me to that workspace, but this is double the work.  It may seem I am being picky, but I am just wondering if there is anyway I could combine these actions.

For instance if there was a way to find out if a window is "active_moving: which I will define to be in the process of being dragged (not just simply the active window) then I could probably figure out a way to put these actions in a shell script and watch for a particular key stroke if a windows is active_moving and if it is, then execute the two sequences of moving the window to that workspace and then switching to that workspace.  Any ideas?

If there isn't a way to hack this feature out I believe it should be requested.  In Ubuntu's day and age there should simply be no reason it can't accommodate this feature.  If this is the case, I would like any direction on where to make feature requests for the window manager.  If there is anyone like me from a fluxbox window manager background I'm sure they feel as naked as I do.

Again, thanks for anyone listening to my blathering.

---

### Post by meindian523 on 2007-09-22
Dunno,just my 2c,but this feature is available in compiz-fusion and iirc,in beryl too....

---

### Post by wakeboarder3780 on 2007-09-22
I understand that this feature is offered in other window managers.  I started out using fluxbox with Ubuntu, tried it for about 6 months, but realized Gnome is really the way to go.  It's the window manager that comes packaged with Ubuntu and therefore should be the "best" wm to use for seamless integration with the system.

For these reasons I want to continue using gnome.  My question was simply this:

Question 1: Is this option available?
(50% answered thanks to wolki's suggestion)
(still wondering if you can do the drag-drop via using wm warping keys)

Question 2: Where do I go to request the option if it doesn't exist?
(dependent on the response to question 1)

---

### Post by Wolki on 2007-09-22
> **wakeboarder3780 said:**
> I understand that this feature is offered in other window managers.  I started out using fluxbox with Ubuntu, tried it for about 6 months, but realized Gnome is really the way to go.  It's the window manager that comes packaged with Ubuntu and therefore should be the "best" wm to use for seamless integration with the system.

Note that GNOME is not a window manager. GNOME is a complete software environment that, among other things, contains a window manager; window manager integration with the desktop environment is done in a modular way so that you can have another (compliant) window manager in the default wm's place. (of course, that window manager will need to provide its own theme and keybinding configuration as the default ones only work for GNOME's default wm, but that shouldn't be too much of a problem.

> Question 1: Is this option available?
(50% answered thanks to wolki's suggestion)
(still wondering if you can do the drag-drop via using wm warping keys)


Not that I know of.

> Question 2: Where do I go to request the option if it doesn't exist?
(dependent on the response to question 1)

GNOME Bugzilla, Metacity product.
I assume that [http://bugzilla.gnome.org/show_bug.cgi?id=344059](http://bugzilla.gnome.org/show_bug.cgi?id=344059) would need to be fixed first, though.

---

