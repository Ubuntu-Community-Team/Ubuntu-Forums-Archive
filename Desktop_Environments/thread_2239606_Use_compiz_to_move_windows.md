---
title: "Use compiz to move windows?"
date: 2014-08-14
forum: Desktop Environments
---

### Post by feffer on 2014-08-14
I like to use a couple of shortcuts to move windows around the desktop. Using compiz-settings-manager > window grid, there are settings to do this. For example to move the terminal window to the upper right corner of the desktop, hit: Ctl-Alt-KP9 (where KP9 is the keypad 9 on my keyboard). So, OK, this works, but it changes the size of the window in the process...which I don't want. Moving to the top or bottom edge maximizes the window horizontally; centering it makes it full screen. Bad for me! So I go to the Corners/Edges tap and change all the actions to "none," log out, back in again, but nothing changes! I go to the Resize Actions tab and try checking/unchecking the resize box...still no fix!

I'm confused! I've had this working in 12.04, but can't get it to work in the new install...14.04. What am I missing? Thx.

---

### Post by feffer on 2014-08-14
OK, now I remember how to do it. Install compiz-plugins. Then a new window management one called "Put" appears. Go to "Grid" and disable all the keybindings that move windows there (otherwize, they will conflict with settings you'll make in "Put"). Then go to "Put" and enter your key shortcuts. Now log out and back in. Now the windows move around nicely w/o getting resized! Hope this helps others...as well as helping me remember!

---

