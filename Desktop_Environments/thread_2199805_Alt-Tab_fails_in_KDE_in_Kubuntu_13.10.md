---
title: "Alt-Tab fails in KDE in Kubuntu 13.10"
date: 2014-01-15
forum: Desktop Environments
---

### Post by reese2 on 2014-01-15
I SOLVED IT: 

I installed 64 bit Kubuntu 13.10 a few days ago.  Initially Alt+Tab worked OK as a task switcher, but at some point it broke: it would only switch to the desktop, not between tasks, and then sometimes freeze the mouse for about 10 seconds.

First I went to Settings -> System Settings -> Common Appearance and Behavior -> Shortcuts and Gestures.  I couldn't find Alt+Tab or the Task Switcher in here.

After floundering around some, I finally fixed the problem:  

Go to Settings -> System Settings -> Workspace Appearance and Behavior -> Window Behavior -> Task Switcher.

In the Main tab of the Task Switcher:

Whenever you get the following error message: "The shortcut 'Alt+Tab' conflicts with the following key combination:  Shortcut 'Alt+Tab' in Application KWin for action Walk Through Windows  Alternative" then click on Reassign.

Under All Windows:
Click on the Forward button, press the Alt+Tab keys, Reassign if needed.
Click on the Reverse button, press the Alt+Shift+Tab keys, ...

Under Current Application:
Click on the Forward button, press the Alt+` keys, ...
Click on the Reverse button, press the Alt+Shift+` (also known as Alt+~) keys, ...

Do the same in the Alternative tab.

Click Apply.

---

