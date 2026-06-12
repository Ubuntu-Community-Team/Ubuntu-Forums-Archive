---
title: "shift+click, mouse wheel not working in wine"
date: 2007-09-21
forum: Desktop Environments
---

### Post by petrescs on 2007-09-21
Hello, I am new to this forum - have searched both here and winehq forums but haven't found too much related with my problem. Not quite sure this is wine related or xorg.conf related, please let me know if a known issue.

The issue is appearing for any recent versions of wine up to current 0.9.45 (have tried on last 5-6 versions), on both ubuntu 6.06 and 7.04. My MS Windows app is developed in Borland Delphi and works almost 100% well under wine. The one problem I noticed so far is that is not responding when Shift+clicking on buttons, as expected (under MS Windoes, this opens specific reports views). Also I cannot scroll in its window with mouse wheel - not sure these two issues have same roots or not; what I can say is that mouse is fully recognized in Ubuntu (scroll wheel works fine "outside" wine) and also keyboard is ok  (shift key works as expected for various other Linux native apps). Except wine, there is no other changes in default install of Ubuntu so I cannot blame certain custom settings.

As far as I found in forums so far, there were mainly two fixes suggested (for gamers not having accessible Shift/Ctrl/Alt + click): some were suggesting changing Movement Key in System/Preferences/Window from Alt to Super, while others suggested changing Window Settings in winecfg (Allow/Disallow the window manager to control the windows). Nothing works in my case.

Any help or pointers to other similar issues is appreciated. Thank you.

---

### Post by petrescs on 2008-02-18
Anybody?This still bugs me now even for wine 0.9.55 and ubuntu 7.10. It does not look like a app issue (as it behaves ok under windows). Was even trying to launch it directly from X instead Gnome (no window manager - have not tried KDE, XFCE) - same result. Looks like Shift key is ignored when is combined with a left click - otherwise Shift behaves correctly. Any advice? Thanks in advance.

---

### Post by Rplus9 on 2008-04-12
I just started having this problem with playing World of Warcraft on Wine.  I use Shift, Ctrl and Alt to get more function from my mouse buttons.  After the last wine patch they stopped working on the left side.  Odly the right shift, alt and ctrl buttons still work with mouse clicks...

no idea.

---

### Post by Rplus9 on 2008-04-12
[http://bugs.winehq.org/show_bug.cgi?id=12392](http://bugs.winehq.org/show_bug.cgi?id=12392)

apparently this is a wine bug  that has been identified

Is there anyone able to explain how to get back to the last "good" version of wine?

---

### Post by NerdyShinobi on 2008-04-20
This happened to me and my wife, too.  I run Openbox as a WM, she runs a straight Hardy Gnome desktop.  I was fine, she could not shift or ctrl-click anything successfuly.  No Dressing Room, no item or quest links.  I installed Openbox on her machine and replaced Metacity with Openbox as WM, and the problem went away.

Metacity seems to be bugged.  Install Openbox, then log out.  Choose ¨Gnome-Openbox¨ as your session, log back in, and try WoW.  Should be able to click away.

---

### Post by pythonholum on 2008-05-05
following these instructions fixed it for me [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

