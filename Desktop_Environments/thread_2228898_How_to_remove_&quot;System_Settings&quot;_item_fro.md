---
title: "How to remove &quot;System Settings&quot; item from Shutdown Menu"
date: 2014-06-10
forum: Desktop Environments
---

### Post by Koray_AGAYA on 2014-06-10
How to remove this system settings button? Ubuntu Version is 14.04 Please help me 

[ATTACH=CONFIG]253873[/ATTACH]

---

### Post by Frogs Hair on 2014-06-10
Hello ,

If it is possible to remove there would be an entry in the deconf-editor . if not installed use the following command or install from the software center and open the application from dash.```
sudo apt-get install dconf-editor
```

Edit:I was informed by a Ubuntu member there is no option to remove from the above application.

---

### Post by Koray_AGAYA on 2014-06-11
I installed dconf-editor and searched but I didn't found. Where is "System Settings" item  Can you help me please ?

---

### Post by mc4man on 2014-06-11
As mentioned there is no setting to suppress System Settings in the session indicator so there is nothing for you in dconf in this regard.
Your only possible viable option is to get the indicator-session source & remove the menu item from being created ( & prevent the compile from testing for the item) & rebuild the package

---

### Post by Koray_AGAYA on 2014-06-23
How Can I do, Do you have Tutorials ?

---

