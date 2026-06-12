---
title: "Start Amarok maximized?"
date: 2005-12-11
forum: General Help
---

### Post by cstudent on 2005-12-11
I took an old PIII machine and made a jukebox out of it. I'm using Amarok under Gnome to play my music. I have Amarok setup to start at startup under the sessions config. Is there a command line option that will tell Amarok to start maximized? I've looked through the documentation and can't seem to find one. I've also tried a few guesses like -m, -max, -maximized and using --. Anyone know if it can be done and if so how.

---

### Post by jliedeka on 2005-12-12
You could force it to take up the whole screen by adding an entry in your .Xdefaults file.  You need to find out what X thinks Amarok is called but the entry would be something like this:

Amarok*geometry: 1024x768+0+0

Where 1024x768 stands for whatever your resolution is and +0+0 means start at the top left.

To find the name that Xwindows knows Amarok as, run a shell on the same desktop.  Run the command "xprop" then click somewhere in the Amarok window.  Look for WM_NAME(STRING).  Whatever is in quotes is the name that X uses.

---

### Post by cstudent on 2005-12-12
Thanks. I'll give that a look see.

---

