---
title: "Right-click on desktop disables Xfce desktop management"
date: 2008-10-03
forum: Desktop Environments
---

### Post by Inferiority Complex on 2008-10-03
I had a weird problem earlier which I was going to ask about but I've managed to discover a solution so I thought I'd post in case anyone else was having the same problem.  A quick search revealed they were: [http://ubuntuforums.org/showthread.php?t=434608](http://ubuntuforums.org/showthread.php?t=434608)

Whenever I right-clicked the desktop to get a menu, it would cause the screen to blank out leaving only the Xfce panel.

Going to the **Xfce Settings Manager** and clicking **Desktop Preferences** to see what was going on there revealed that **Allow Xfce to manage the desktop** had become unchecked.

I checked the box and later discovered when I right-clicked the desktop that the same thing would happen again and I'd have to re-check the option for **Allow Xfce to manage the desktop**.

The **Behaviour** tab in the **Desktop Preferences** has **Show window list on middle click** checked but **Show desktop menu on right click** was not.  However, this brought up the main Xfce menu on a right-click which was not what I wanted.  I was looking for the menu that said *Create Launcher; Create URL Link; Create Folder; etc.*

My **Desktop Icons** section was set to none.  I changed this setting to **File/Launcher Icons** and somehow, I got my right-click menu back.

This worked and I hope other folks can benefit from this accidentally discovered solution.  If you're not getting your right-click menu, change this setting and see if it works for you too.

---

