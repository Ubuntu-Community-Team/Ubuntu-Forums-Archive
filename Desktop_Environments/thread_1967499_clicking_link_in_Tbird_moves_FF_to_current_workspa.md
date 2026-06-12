---
title: "clicking link in Tbird moves FF to current workspace"
date: 2012-04-28
forum: Desktop Environments
---

### Post by timzak on 2012-04-28
With the 12.04 release, I've switched my production machine to Xubuntu.  This is my first time running XFCE fulltime, as such, it's taking awhile to discover the new idiosyncrasies ;)

Just found an undesired behavior and wondering if it's possible to change.  I normally run Thunderbird in workspace 1, and Firefox in workspace 2.  If I click on an email link (Newegg promo), I expect the page to open in a new tab on Firefox on workspace 2.  Instead, Firefox moves from workspace 2 to workspace 1, then the page opens in a new tab.  Is there any way to keep Firefox from moving workspaces in this situation?  

Xubuntu 12.04 rocks!  Well done, Xubuntu team!
Thanks!
Tim

---

### Post by timzak on 2012-04-28
Found a solution.  Here it is for anyone else who comes across this:

Go to the XFCE Settings Editor (Application Menu->Settings->Settings Editor)

Navigate to xfwm4->activate_action and change the value from "bring" to "switch"

---

### Post by Toz on 2012-04-28
Go to Settings Manager->Window Manager Tweaks->Focus tab, and change the "When a window raises itself" option to "Switch to window's workspace".

---

