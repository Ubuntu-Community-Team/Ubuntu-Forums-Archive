---
title: "[Solved] Follow Window after Moving to Another Workspace"
date: 2015-04-23
forum: Desktop Environments
---

### Post by kf6sgy on 2015-04-23
I just upgraded to 15.04 and when I use my keyboard shortcuts to move a window to another workspace (Super+1 through Super+4 for workspaces 1 through 4) it no longer switches to that workspace like it did before the upgrade. I went through everything having to do with workspaces and window manager under Settings Manager and have not come up with a solution. Is there a way to change this with the graphical configuration or through one of the text config files? I've tried searching but mostly come up with how to send a window to another workspace. It doesn't appear that the window is active in that workspace if I switch over manually, I'm not sure if that's part of the issue.

---

### Post by grahammechanical on 2015-04-23
Super + 1 to 9 = same as clicking on a Launcher Icon.

I am quoting the overlay that appears when we hold down the super key.  To move focused window to another workspace = shift+ctrl+alt+arrow keys. How we do that without breaking our wrist I do not know. It might help if you can play the piano.

Use the left little finger to hold both the left shift and the left Ctrl keys down, then use the left first finger to press Alt and then with the right hand press an arrow key. Why don't you just leave the window where it is? :)

Regards.

---

### Post by kf6sgy on 2015-04-24
That key combination does nothing on my machine, I changed "Move window to workspace 1" to Super+1, 2 to Super+2, etc. The window will move to the corresponding workspace, but the desktop won't change to that workspace like it once did. There are times when I open a window and would like to move it to another workspace, I prefer to use keyboard shortcuts. I'm hoping the XFCE developers didn't take this away without making it an option.

---

### Post by deadflowr on 2015-04-24
Are you running XFCE?

---

### Post by kf6sgy on 2015-04-25
Sorry, I forgot to mention I'm on Xubuntu, so yes I'm running XFCE

---

### Post by Toz on 2015-04-29
> **kf6sgy said:**
> That key combination does nothing on my machine, I changed "Move window to workspace 1" to Super+1, 2 to Super+2, etc. The window will move to the corresponding workspace, but the desktop won't change to that workspace like it once did. There are times when I open a window and would like to move it to another workspace, I prefer to use keyboard shortcuts. I'm hoping the XFCE developers didn't take this away without making it an option.

The functionality was changed. See: [https://bugzilla.xfce.org/show_bug.cgi?id=11511]("https://bugzilla.xfce.org/show_bug.cgi?id=11511").

---

### Post by kf6sgy on 2015-04-29
I guess that solves that, I rather liked the old way, oh well. Thank you for the link.

---

### Post by wmburke2 on 2015-05-12
FYI, you can still move a window to the next or previous workspace using Ctrl+Alt+End and Ctrl+Alt+Home. The view changes to the new workspace at the same time. See here for more details:
[http://docs.xfce.org/xfce/xfwm4/getting-stated](http://docs.xfce.org/xfce/xfwm4/getting-stated)

---

