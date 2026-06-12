---
title: "Upper and bottom workspace shortcuts not working"
date: 2016-10-05
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2016-10-05
So I've set up 4 workspaces in two rows, like in Unity:

1    2
3    4

 And configured the following shortcuts:

**Upper workspace: **Ctrl+Alt+Up[B]
Bottom workspace: [/B]Ctrl+Alt+Down[B][B]
Move window to **upper workspace**: [/B][/B]Shift+Ctrl+Alt+Up[B]
**[B]Move window to bottom[B] workspace**: [/B][/B][/B]Shift+Ctrl+Alt+Down

Everything worked as expected at first, but after rebooting I can only move horizontally (i.e. left and right) between workspaces, although the Workspace Switcher displays the workspaces as configured (i.e. in two rows). So that workspaces 1 and 3, and 2 and 4, are not connected, and I can move between 2 and 3 as if they were horizontally adjacent.

Am I the only one experiencing this problem? Is there any way of fixing it?

---

### Post by Pablo_San_Martn on 2016-10-05
Found the solution [here]("http://askubuntu.com/questions/168144/multiple-workspace-rows-in-xfce-without-xfce-panel#285409").

Basically add the following line to ~/.profile:
xprop -root -f _NET_DESKTOP_LAYOUT 32cccc -set _NET_DESKTOP_LAYOUT 0,2,2,0

---

### Post by ajgreeny on 2016-10-05
Great, and well done for finding the answer!
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by Pablo_San_Martn on 2016-10-05
Thanks, ajgreeny, done!

---

