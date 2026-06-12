---
title: "Auto expand workspace count"
date: 2014-01-22
forum: Desktop Environments
---

### Post by Darksonn on 2014-01-22
I currently have 5x5 workspaces, and this is fine most of the times, but sometimes I need more, is it possible to have the workspace grid increase if you have windows in the outer workspaces and the middle one be the default?

---

### Post by tgalati4 on 2014-01-22
What desktop environment are you running?  I don't know of any way to automatically expand the number of workspaces.  You could write a script that runs in the background and counts the number of applications running on each workspace and when that number exceeds a threshold then increment the number of workspaces one-by-one.

Making the middle one the default would require some case logic.  In your expansion script, you could have a case statement that if you are using a 3x3 matrix, then make number 5 the default.  If 4x4 then make 7 the default, if 5x5 then make number 13 the default.

Of course, your script would need to deal with shrinking the workspaces as well, otherwise they would quickly grow and become unmanageable.

You can experiment with other window managers such as [xmonad]("http://manpages.ubuntu.com/manpages/precise/man1/xmonad.1.html").

---

