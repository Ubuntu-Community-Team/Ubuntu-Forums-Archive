---
title: "Desktop help"
date: 2005-03-05
forum: Desktop Environments
---

### Post by fizzicsguy on 2005-03-05
Ok, as a new ubuntu/gnome user I almost feel odd asking this.  After an update via synaptic of my installation the top and bottom bars on my desktop have vanished.  Nothing remains except the Home folder. My desktop is naked!  I did nothing other than a "smart upgrade". I don't even know where to start other than reinstall again. Any ideas?

---

### Post by kassetra on 2005-03-05
[QUOTE=fizzicsguy]Ok, as a new ubuntu/gnome user I almost feel odd asking this. After an update via synaptic of my installation the top and bottom bars on my desktop have vanished. Nothing remains except the Home folder. My desktop is naked! I did nothing other than a "smart upgrade". I don't even know where to start other than reinstall again. Any ideas?[/QUOTE]

Try this:
 1. start a terminal (right click on desktop, "open terminal") and type
[left] ```
gnome-panel
``` [/left]
    2. When they come up, go to Computer->Desktop Preferences->Sessions, Current Session tab
 
3. Scroll down through the list and make sure that you see a restart icon in the style column next to "gnome-panel" in the list (look at metacity's icon to compare if you're not sure) 
 
 4. Stop the panels running from the terminal by pressing CTRL+c in the terminal window
 
 5. Restart your gnome session (CTRL+ALT+Backspace)
 
 That should fix the problem.  *Should*

---

### Post by fizzicsguy on 2005-03-07
Thanks for the reply.

```
gnome-panel
```


Gave command not found.  I reinstalled and everything seems to work fine.

---

