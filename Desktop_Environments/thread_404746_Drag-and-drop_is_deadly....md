---
title: "Drag-and-drop is deadly..."
date: 2007-04-08
forum: Desktop Environments
---

### Post by Keiji on 2007-04-08
Quite often a very annoying bug happens to me, which is if I try to drag something and then the program where I dragged it from changes the source of the drag before I release the mouse button, everything will stop working. Mouse buttons and all keyboard keys will do nothing, and while I can move the mouse, no highlight occurs when I move the cursor over buttons or similar things. The only thing I can do is either restart X with Control+Alt+Backspace, or switch to a terminal, sudo bash, run a script  I wrote for the purpose of determining a process ID and then killing the program which is the source of the drag.

This is quite possibly the most annoying bug I have seen in Linux, and it has caused me to lose a lot of work on many occasions. Does this happen for everyone or is there something wrong with my computer?

---

### Post by krussell on 2007-04-09
Hello :-)
Drag/drop works fine with y ubuntu.
I didn't understand your problem, could you site another example?

---

### Post by Keiji on 2007-04-09
Well, the most common case is in Galeon. If I start dragging the drag handle from the address bar, but then a new page loads while I'm doing that (e.g. from a META REFRESH), then the bug will occur. It also happens in Nautilus if I drag a file from an FTP browser window and then somehow that file disappears (there are quite a few bugs in Nautilus with disappearing files on FTP folders, in my experience).

---

