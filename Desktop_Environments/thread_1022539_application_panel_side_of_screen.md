---
title: "application panel side of screen"
date: 2008-12-26
forum: Desktop Environments
---

### Post by Silvernail on 2008-12-26
I seem to have broken my navigation panel across the top of my screen. At least that is where I would like to to return to.

Now it is at the side of the screen. I have gone into 'Others' and 'panel' and change that so the panel is suppose to be on top. Nothing happens. When I restart, nothing happens, when I reboot, nothing happens?

This has happened before. I sneeze before I can get my hand off of the mouse and the resulting jerk moved the pointer over the panel and it jumps to the side. I have no clue what I did to correct it last time but 3 hours has not provided a solution today.

Is something else controlling this? Do I have evil spirits or ghosts?

---

### Post by Coder543 on 2008-12-26
Right click on the panel
click "allow this panel to be moved"
click-drag it to the top of the screen
let go
done.

---

### Post by Silvernail on 2008-12-27
I do not have  this option, meaning it is not in the right click menu.

---

### Post by damis648 on 2008-12-27
Then just click>drag it to the top of the screen.

---

### Post by Silvernail on 2008-12-27
Interesting....that worked
I had tried that a dozen times before. Nothing would happen. I removed some of the icon on the panel, put the cursor in the clear space, close the fist and swing left, Nothing happened so I assume nothing would happen and let go. 

This time I swung to the top of the page and the panel disappeared from the left side and appeared on top.


Thanks for telling me to do it again.
Dave

---

### Post by ubuntu1sttimer on 2008-12-27
Glad you got your problem solved Silvermail. I found your thread while trying to find information on a similar problem.

Just got a phone call from a fellow that I installed 8.04 for. Is kind of the same problem as above but  a bit extreme. His normal top navigation panel is gone. Not on the side or bottom of the screen. Just not there.

Wonder if anyone has an idea of how to restore a missing navigation panel?  BTW, it is not under the bottom one.

---

### Post by 5BallJuggler on 2008-12-27
> **ubuntu1sttimer said:**
> Glad you got your problem solved Silvermail. I found your thread while trying to find information on a similar problem.

Just got a phone call from a fellow that I installed 8.04 for. Is kind of the same problem as above but  a bit extreme. His normal top navigation panel is gone. Not on the side or bottom of the screen. Just not there.

Wonder if anyone has an idea of how to restore a missing navigation panel?  BTW, it is not under the bottom one.

open "gconf-editor" Alt+F2
under "Apps" you will find a section called "panels"
in this section you will find "toplevels"
in here you should find "top_panel_screen0"
if that's not there, then it has been deleted and you need to remake it.

---

### Post by ubuntu1sttimer on 2008-12-27
Thanks 5BallJuggler. I keep learning with Ubuntu. Someday I may even be ahead of it far enough to help others.

---

### Post by Silent flyer on 2009-01-05
Thanks silvernail and coder543. You solved my problem too (spontaneously-messed up main menu bar after updates).

---

