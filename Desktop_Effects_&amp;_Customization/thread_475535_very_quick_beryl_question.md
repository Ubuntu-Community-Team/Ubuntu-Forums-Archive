---
title: "very quick beryl question"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by cplspafford on 2007-06-16
let me start off by saying I am sorry  if this question was asked and/or answered.  I have installed beryl and everything seems fine.  I have the beryl manager and it auto starts.  My only problem is that I can open the beryl manger and I can see all of the settings yet none of them work.  I do not get error messages or anything it just acts like it did when I didn't have beryl installed.  Any ideas??

Thank you all for your time.  This forum has made my switching to ubuntu almost painless!!

---

### Post by Soybean on 2007-06-16
My guess is that Beryl isn't actually running; just the beryl-manager. Beryl-manager is a separate program -- it's the little icon that runs in your notification area and lets you easily change settings related to beryl. But it doesn't actually do any fancy 3d stuff itself. 

Now, normally, when beryl-manager starts, it automatically loads beryl. But if your drivers or X server aren't configured correctly, it's set up to switch back to normal metacity -- without any visible error message.

To troubleshoot:
-exit the beryl-manager (I'm not running Beryl on this computer, but I believe you right click the icon and then... "quit" or "exit" or something, at the bottom of the menu)
-open a terminal window
-type beryl-manager in the terminal


This will launch beryl-manager again, but now if anything goes wrong, it'll print error messages in that terminal. You can try to sort it out from there, or copy-paste the errors on the forum here. :) Oh, and if it still seems like nothing's happening, right click on the icon, go to... "select window manager" or "change window manager" or something like that, and pick beryl.

---

