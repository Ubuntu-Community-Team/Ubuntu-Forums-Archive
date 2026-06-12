---
title: "Firefox still opens Nautilus after installing Mate"
date: 2013-02-16
forum: Desktop Environments
---

### Post by Cezy on 2013-02-16
In Ubuntu 12.10, after used Classic Gnome for a while, I installed Mate and I found it really cool. 

Only, using Firefox, when I click on "open directory" in Downloads window, Firefox open Nautilus and not Caja, Mate's Nautilus' replacement.

There is any firefox/mate setting to modify this?

---

### Post by aarons6 on 2013-02-18
check in ~/.local/share/applications/mimeapps.list

i switched my nautilus to dolphin.. i had to change it in there.. it worked great.. but i use chrome.. should work tho for all programs that use mime types.

---

### Post by Frogs Hair on 2013-02-18
You can also change the what application a folder is opened with. Right click the folder and select open with another application and change the default application for opening the folder by selecting it from the list. 

For the application to be an option for Firefox you might want to make sure the Caja file manager is set as default. This would appear under preferred applications, default applications, or a similar heading.

---

