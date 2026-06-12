---
title: "&quot;Run in terminal&quot; and how to stop it from autoclosing (10.04)"
date: 2011-06-24
forum: Desktop Environments
---

### Post by DrDevice on 2011-06-24
Guten tag, mein freunds!  (German, how multicultural! :P)

Looking for a starting point on how to tweak my 10.04 Gnome a bit.

**_Setup_**:
From the Desktop or Nautilus I double-click on a script or executable. Usually up pops that nifty window with four button choices: Run, Run in Terminal, Display, and Cancel.

I like running things in gnome-terminal to check output; reading the terminal output from a game in Wine helped me figure out what I needed to fix to get it tweaked perfectly.  But the "Run in terminal" button doesn't keep the terminal window open, it autocloses as soon as I exit the program, negating the purpose of running in a terminal.

**_Question_**:
What is the best way to go about changing the behavior to allow  the window to remain open?  I'm thinking something akin to adding a PAUSE command into a batch file in MSDOS, but applied to all opened programs using the button.  Thoughts?

---

### Post by furtypajohn on 2011-06-29
Open a terminal (Accessories -> Terminal) and do the following steps:

Edit -> Profile Preferences -> Title and Command

At the bottom there is a selection labeled "When command exits" and it should be set to "Exit the terminal" by default.

Change this option to "Hold the terminal open."

Hopefully that does what you're looking for.

---

