---
title: "Display Output of Nautilus Scripts"
date: 2007-02-02
forum: Desktop Environments
---

### Post by sumadartsan on 2007-02-02
I've placed scripts in the .gnome2/nautilus-scripts and they run just fine.  However, I would like there to be a way to be able to see the output of the scripts.  If I could perhaps have a terminal window to pop up so I can watch the results, it would be great.

I've tried to have it load in a terminal window while it runs but to no avail.  I'm uncertain how exactly to do this.

I thought it would work by placing ```
gnome-terminal -x
``` before the command I want output in the script, followed by something like ```
read -n 1
``` to pause the output screen.  However, that does not work for me, even though I've seen it suggested on the forums somewhere.

As a test I tried what the manual page for gnome-terminal says on an arbitrary command:
```
gnome-terminal --command="read -n 1"
```  However, gnome-terminal simply pops up for a split second and closes.
Surely there is something I'm not understanding.

How do I get the script to show it's output?  Perhaps there's an alternative way?

---

### Post by artships on 2007-02-02
xterm   -hold   -e path_to_script

---

