---
title: "disable window resize when moving"
date: 2014-11-24
forum: Desktop Environments
---

### Post by hamza_alloush on 2014-11-24
let me describe my problem

1 - Move window to left of screen(half)

2 - point cursor to drag window

3 - click to drag and remove from left of screen

4 - window minimizes/collapses...


i want the window to remain the same size as half the screen, without minimizing

how can i do this?

i'm using Ubuntu 14, stock unity

---

### Post by deadflowr on 2014-11-25
Number 4 seems odd.
Normally when you pull the window from the edge it reverts back to the original pre-grid size, and not minimizes.

But you might look in compiz settings via compizconfig-settings-manager(needs to be installed).
In here go to The section Window Management, then the sub section grid.
In Grid go to  resize actions, there should be a toggle for snap windows back to original size.
Uncheck that.
You might also look at any other settings in there for whatever might be causes said odd problem, if that is what it is...

---

### Post by hamza_alloush on 2014-11-28
looks like it is a bug in Ubuntu, i reproduced it in virtualbox with new installation of Ubuntu 14.04 LTS

how it happens:

1 - open firefox

2 - open any website

3 - maximise window(using ctrl+meta+UP)

4 - close firefox

5 - open firefox 

6 - move firefox to a grid half the screen(using ctrl+meta+LEFT)

7 - move cursor to drag window

8 - click to drag

9 - window collapses(not retaining pre-grid size)...

happens in Chromium too

i even made a video: [http://www.youtube.com/watch?v=AseMphcH9mw&feature=youtu.be](http://www.youtube.com/watch?v=AseMphcH9mw&feature=youtu.be)

---

### Post by hamza_alloush on 2014-11-28
> **deadflowr said:**
> Number 4 seems odd.
Normally when you pull the window from the edge it reverts back to the original pre-grid size, and not minimizes.

But you might look in compiz settings via compizconfig-settings-manager(needs to be installed).
In here go to The section Window Management, then the sub section grid.
In Grid go to  resize actions, there should be a toggle for snap windows back to original size.
Uncheck that.
You might also look at any other settings in there for whatever might be causes said odd problem, if that is what it is...

that toggle does not solve it, looks like there is a variable uninitialized somewhere when you snap it to a grid on the left/right and then attempt to drag it.

---

### Post by CantankRus on 2014-11-28
I see the same when I use shortcut keys to tile the window.
If I drag the window to the side with the mouse to initiate tiling then drag from the maximized vertical state I don't get the tiny window.

If you prefer using shortcut keys one fix would be to add a shortcut that uses this wmctrl command...
```
[COLOR="#008000"]wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,450,260,860,531[/COLOR]
```
The first wmctrl command removes any maximized states then the 2nd wmctrl command sets the size and position of the window.
See [**_[COLOR="#B22222"]THIS POST[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1942500&p=11776457#post11776457") for an explanation of the size and position values and adjust for your screen size.

You need to install wmctrl...
```
sudo apt-get install wmctrl
```

Use the ccsm Commands plugin to set a shortcut key to run the [COLOR="#008000"]wmctrl command[/COLOR]
In the attached pic example I used the shortcut ctrl+alt+KP5
When setting it will ask to disable conflicting shortcuts. Choose to disable.

---

