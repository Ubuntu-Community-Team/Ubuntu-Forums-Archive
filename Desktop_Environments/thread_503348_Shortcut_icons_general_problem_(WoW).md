---
title: "Shortcut icons general problem (WoW)"
date: 2007-07-17
forum: Desktop Environments
---

### Post by wolfe on 2007-07-17
I'm trying to make a desktop shortcut for WoW but am hitting a snag.

When starting WoW from the command like cedega '/opt/WoW/WoW.exe' , the game loads perfectly.

When I try to make a link on my desktop in KDE, the game starts up with kicker running at the bottom. Clicking the game window will not make kicker go away. Also the mouse cursor shows both the in game cursor and the mouse cursor from KDE. I stress though, these issues are not present calling the program from the command line.

the icon has the following settings:

Command: cedega '/opt/WoW/WoW.exe
Work Path: /opt/WoW

What am I missing here?

---

### Post by RawMustard on 2007-07-18
Change:
Command: cedega '/opt/WoW/WoW.exe

To this perhaps?
Command: cedega '/opt/WoW/WoW.exe'

---

### Post by wolfe on 2007-07-18
oh that was just an error on part while posting to this thread, the command itself does not include the quote marks.  I just used that as a way to seperate the command portion from the rest of my post. Thanks though.

---

