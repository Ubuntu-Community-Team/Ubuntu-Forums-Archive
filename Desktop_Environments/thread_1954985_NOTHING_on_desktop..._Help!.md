---
title: "NOTHING on desktop... Help!"
date: 2012-04-09
forum: Desktop Environments
---

### Post by sgriggly on 2012-04-09
so i just "upgraded" to Natty Narwal... i went into the compiz settings to put them how i like them. after setting it to "cube" settings, i was unable to close out of the settings. thought it was odd, but just did a quick restart. 

now, there's NOTHING on my desktop on load up. no menus, no tool bar, nothing to access. where do i go, how do i get there, and how do i fix this? (for example, where is the compiz settings application within the file system? i can't find it!)

please be very specific, i'm noob and have no landmarks anymore (for example, without a drop-down menu, you would even have to tell me where and how to find the "terminal" application, if you're suggesting i do anything there, b/c i don't know where it is within the file system...)

---

### Post by squenson on 2012-04-09
To access the terminal, you can press Ctrl-Alt-T. From there, you can run any command.

---

### Post by sgriggly on 2012-04-09
ctrl-alt-T doesn't open any terminal for me... 

and i'm gonna need more help than that. (i'll add that if i minimize a window, it doesn't minimize TO anywhere, it just completely disappears; and, i can't move a window by grabbing it with the mouse either).

---

### Post by squenson on 2012-04-09
Other ideas!

You can press Ctrl-Alt-F1 which opens another session, without GUI. Press Ctrl-Alt-F7 to go back to your GUI desktop.

When you boot, do you have automatic login? If not, on the login screen, you can select another desktop, try them and see if you get better results.

Of course, these ideas won't solve your problems but they may allow you to progress a little bit with your investigations. Good luck!

---

### Post by Krytarik on 2012-04-09
Please see this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by sgriggly on 2012-04-09
followed the instructions, run CCSM, and changed all the relevant settings... problem NOT solved :( 

tried both setting it back to Desktop view, and also [http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

neither solved problem...

---

### Post by sgriggly on 2012-04-09
this solved it: 

"
Reset all the configuration for Unity by running this command in a terminal, or a tty1:

unity --reset 

"

---

