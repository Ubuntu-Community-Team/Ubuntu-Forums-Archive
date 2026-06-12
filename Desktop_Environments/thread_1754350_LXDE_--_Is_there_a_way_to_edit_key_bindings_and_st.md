---
title: "LXDE -- Is there a way to edit key bindings and startup applications?"
date: 2011-05-09
forum: Desktop Environments
---

### Post by Entyrion on 2011-05-09
I have (normal) Ubuntu 11.04 installed and I used the Ubuntu Software Center to install LXDE. I'm stuck on 2 problems though, and I'm not sure how to fix them.

1. How do I change key bindings in LXDE? Specifically, I want to use Super+up/down/left/right change between workspaces, not the default Ctrl+Alt+up/down/left/right.

2. I have a script that I have set to auto-run on startup in my standard Unity session; I created a script and added it to the startup programs list there. However, I need to remove that script from LXDE ONLY, so that in the Unity session it will continue to run, and in the LXDE session it will NOT run.

Is anyone aware of a way to do either of these two things? Thanks!

---

### Post by Entyrion on 2011-05-10
I found a solution for #2:

In the LXDE session, run LXTerminal and run ```
lxsession-edit
``` and simply uncheck the script in the list there. When I did this, it did NOT alter the autorun list in the standard Unity session!

---

### Post by Entyrion on 2011-05-10
Found a solution for #1.
([http://stray-notes.blogspot.com/2011/01/lxde-remap-keyboard-shortcuts.html](http://stray-notes.blogspot.com/2011/01/lxde-remap-keyboard-shortcuts.html))

1. Open LXTerminal

2. ```
cp /home/yourname/.config/openbox
```

3. ```
sudo gedit lxde-rc.xml
```

4. Ctrl+f search for "keybind" and scroll down to that section.

5. Change the "C-A" to "W" in the top 4 entries (-Left, -Right, -Up, -Down) respectively.

Done!

---

