---
title: "&quot;System -&gt; Help&quot; Lost"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Ubuntist on 2005-11-10
I don't know how I did it, but I've lost the Help item on the System menu as well as the lifesaver icon on the system bar.  Being I newbie, I'd really like to have the help facility.

I've looked through the System menu and the options in Synaptic, but I can't find anything that would restore System -> Help.  Any suggestions?

---

### Post by Ubuntist on 2005-11-10
Could someone whose help icon is working please right-click on it, select Properties, and tell me what appears in the Command field of the Basic tab.  Then maybe I could figure out which program is missing and go from there.  Thanks....

---

### Post by mrmcctt on 2005-11-10
The system command I get is 'yelp'.  (No quotes.)

I'm not sure how to help you but I hope this helps you somewhat.

---

### Post by Ubuntist on 2005-11-10
Thanks, mrmcctt -- that does help a lot.  I looked for Synaptic and found that yelp was not installed (can't imagine how it got uninstalled), so I installed it.  I still don't have the help icon, but at least I can run yelp from a terminal window.

If anybody can tell me how to get the icon back, I'm still all ears.

---

### Post by mrmcctt on 2005-11-10
For now, what you could do is right click on the panel, click "Add to Panel" and add a "Custom Application Launcher" and set it up to run yelp.

This is kind of a 'band-aid fix' until someone smarter comes up with a way to replace it in the main menu.

Maybe someone with experience with SMEG could let you know if it can be done.

---

### Post by mrmcctt on 2005-11-10
As an after thought, you said you had to re-install yelp?  Another thing you might try is running ```
sudo killall gnome-panel restart
```and see if yelp  (Help) icons return.

---

### Post by Ubuntist on 2005-11-10
That worked!  You're a genius!

---

### Post by mrmcctt on 2005-11-10
Far from a genius but glad I could help.

---

