---
title: "Compiz fusion can't resize windows and other weirdness"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by eising on 2007-07-08
Hey there. 
I have followed the guides regarding compiz fusion in feisty and am currently experiencing three strange issues:

First of all, I can't resize windows. I can do the other window features, but no resize... Nothing simply happens when I try to drag at the window corners. 

Second issue is the startup of compiz. When I start up gnome, the splash screen keeps hanging until I close it with Alt-F4, and the session startup hangs. If I wait five minutes, everything is started correctly, but it still takes about five minutes to do so. I can force Compiz to launch by running killall compiz && killall compiz.real and then relaunching it with compiz --replace -c emerald &
Still the rest of the apps that I have set up in the session options (pidgin, the update manager etc.)  take about five minutes to launch...

Third issue is with Alt-tab switching of windows, that seem to be really broken. When I have two windows open, I can only switch to the same window, and it consequently skips the other window using alt-tab (win-tab works fine).
When I have more than two windows open, it just doesn't switch to the windows in a natural order, like metacity does.

I hope someone is able to provide me with help with these issues, and I will gladly provide any other data should it be required.

---

### Post by onlinelli on 2007-12-09
probably the "Resize Window" plugin is not activated. Go into CompizConfig Settings Manager and enable the mentioned plugin. AFAIR the plugin is uncategorized.

cheers

---

