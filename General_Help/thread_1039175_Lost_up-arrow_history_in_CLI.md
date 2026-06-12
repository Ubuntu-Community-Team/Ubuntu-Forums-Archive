---
title: "Lost up-arrow history in CLI"
date: 2009-01-14
forum: General Help
---

### Post by jakev383 on 2009-01-14
Here's an odd one for you... Running 8.04 LTS on both my laptop and my desktop.
Laptop works great. My desktop, when I open a gnome-terminal and type some commands, when I close the window and then open again later I cannot hit the up-arrow key to get the history of the commands I used earlier.
This functions normally on my laptop though.
Anyone have any ideas as to why this would have stopped working on my desktop or how to fix it?  It's honestly been broken for a while and I'm just now getting around to asking the question because it finally got annoying enough ;)
Thanks in advance!

---

### Post by adam.ec on 2009-01-14
If you don't close the window can you still get the command historyusing the arrow keys?

---

### Post by jakev383 on 2009-01-14
> **adam.ec said:**
> If you don't close the window can you still get the command historyusing the arrow keys?

Yep.  But I can close the window on my laptop and open it again later and still get the up-arrow history.  The desktop seems to lose the history whenever I close the window.

---

### Post by adam.ec on 2009-02-27
Sorry jakev, I've been working away, I resume the search for a solution if you are still having a problem.

---

### Post by stchman on 2009-02-27
If you are using BASH the history is stored in ~/.bash_history file.

Make sure it did not get set to read only or you inadvertently changed ownership.

---

