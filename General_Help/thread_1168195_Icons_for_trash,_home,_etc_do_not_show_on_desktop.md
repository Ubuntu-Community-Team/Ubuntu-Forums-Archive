---
title: "Icons for trash, home, etc do not show on desktop"
date: 2009-05-23
forum: General Help
---

### Post by TeachThai on 2009-05-23
When I first installed Xubuntu on my computer the icons for the trash, for the file manager, and the folder for home appeared on the desktop. Now I can't find them there at all.  When I go into any of the applications to try to enable these icons to show on the desktop, it appears to me that they are designated to show on the desktop but they still are not there. Anyone have an idea why this is happening?

---

### Post by john.nicholls on 2009-05-24
To get the icons, go to Xfce Settings Manager, Desktop, Icons, and under Default Icons, tick the ones you want.

---

### Post by TeachThai on 2009-05-25
Thanks for your suggestion John. I tried clicking several of the icons. When I click on one of them and then another, the first one becomes clear again as though I did not click it.  When I click on just one of them and then close out the manager and reboot the icon I set to appear on the desktop does not appear.  I can't help but wonder if some or maybe all my problems are due to my having so little memory. I have the minimum that can be used with Xubuntu (128 Mb).   Thank you though for your suggestion.  Perhaps I need to be grateful that the system is usable at all on this old computer.

Have a good day friend and thanks again for your efforts to help.

---

### Post by Brandon Williams on 2009-05-25
Do you have "File/launcher icons" selected a the Icon type on the Icons tab in the Desktop configuration dialog? The Default Icons only show up if you have that setting selected.

If that doesn't solve the problem, double check to make sure that Thunar is running. Run 'ps -fC Thunar' on the command line. Does the command output anything?

---

### Post by kerry_s on 2009-05-25
is xfdesktop running> press alt+f2, type: xfdesktop

---

