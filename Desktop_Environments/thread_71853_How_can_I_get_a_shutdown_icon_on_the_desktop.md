---
title: "How can I get a shutdown icon on the desktop"
date: 2005-10-04
forum: Desktop Environments
---

### Post by Ibuntu_52 on 2005-10-04
I'm looking for a way to get some kind of icon on the desktop that will shut the computer down.

I've tried dragging the icon of the panel it doesn't work.

---

### Post by Ampersand on 2005-10-04
Try creating a new launcher (in the menu you get from right clicking on the desktop) with the command 'sudo shutdown -P now' , and the run in terminal option checked.

Run 'man shutdown' in a terminal to check the manual page for the exact options you want.

---

### Post by RikoW on 2005-10-05
You can also easily add a logout button to the panel.
Do a right-click on the panel background -> Add to panel
scroll down, select Logout and hit add.

However, that gives you the usual Logout Window which lets you select whether you want to logout, shutdown, hibernate or restart.

Cheers,

               Riko

---

