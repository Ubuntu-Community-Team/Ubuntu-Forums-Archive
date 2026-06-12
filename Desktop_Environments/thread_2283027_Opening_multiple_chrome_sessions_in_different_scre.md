---
title: "Opening multiple chrome sessions in different screen locations"
date: 2015-06-18
forum: Desktop Environments
---

### Post by William_Parks_Walk on 2015-06-18
I am running Ubuntu Desktop 14.04. I have installed Chrome. I have created a desktop shortcut with the command line: /usr/bin/google-chrome-stable --window-position=0,525 which works perfectly. When I create a second shortcut on the desktop with a command line: /usr/bin/google-chrome-stable --window-position=325,525 it just opens a chrome window on top of the first chrome window. If I start the second chrome shortcut first and open the first shortcut it opens on top of the second one. It seems that there is a chrome session that retains the attributes of the existing chrome window. How can I create multiple(6) chrome windows that can be individually positioned on the screen either by seperate shortcuts or a command line that will open several at the same time?

---

### Post by Frogs Hair on 2015-06-18
If you don't have to view all instances of Chrome at the same time it's possible to increase the number of workspaces with the compiz config settings manager and switch between work spaces. There are some window placement tools in the CCSM as well. I have six instances of Firefox running in the screen shot by selecting open in a new wind after moving to the next work space. When selecting the active or lighted workspace the window resumes full size.

---

### Post by William_Parks_Walk on 2015-06-19
I need them in the same window. I would use autoit to get this done if it were windows.

---

