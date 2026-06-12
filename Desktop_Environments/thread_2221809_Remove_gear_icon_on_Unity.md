---
title: "Remove gear icon on Unity"
date: 2014-05-03
forum: Desktop Environments
---

### Post by Richard_Romick on 2014-05-03
I am using Unity 14.04 with Cairo-dock.  Even before I installed Cairo-dock, the shutdown/restart option under the gear icon (upper right on notification bar) would only work half the time.  After installing Cairo-dock, it never works.  This is a known bug between Unity and Cairo-dock.

Since Cairo-dock has it's own shutdown/restart menu, I could just ignore the gear icon on the notification bar.  However, I would greatly appreciate help removing the gear icon if possible.  I have searched for quite a while on google, but I don't think I am searching for the right terms.  Thanks for your time.

---

### Post by Frogs Hair on 2014-05-04
You can try the following though I haven't tried it .

Install the dconf editor if not already 

Open the editor , proceed Apps Indicator Session 

Disable user-show-menu 

Log out and back in

---

### Post by Richard_Romick on 2014-05-18
I did what you suggested, but it didn't take away the gear icon.  I think it took a section out under the gear icon.  Do you have anything else I can try?

---

### Post by Frogs Hair on 2014-05-18
You can login to the Cairo Dock Gnome session which includes it's own wing  panel and indicators, but excludes the Unity top and side panel . Select the icon on the top right of the box where you enter your pass word @ login  to enter the session. Adding more docks is also possible.

---

### Post by Richard_Romick on 2014-05-24
That worked, thank you.  I seem to remember trying that a couple of months ago, but I don't remember why.

---

