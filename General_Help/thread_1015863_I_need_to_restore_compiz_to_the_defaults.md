---
title: "I need to restore compiz to the defaults"
date: 2008-12-19
forum: General Help
---

### Post by hafey on 2008-12-19
Hi, i've installed compiz manager on my laptop and it worked fine. but while i was checking the features I made something which made everything wrong. When i restart my system everything looks fine, until i select any of the menus or right-click my desktop. i need to return my compiz to its defaults or disable it. Please help

---

### Post by eternalnewbee on 2008-12-19
> **hafey said:**
> Hi, i've installed compiz manager on my laptop and it worked fine. but while i was checking the features I made something which made everything wrong. When i restart my system everything looks fine, until i select any of the menus or right-click my desktop. i need to return my compiz to its defaults or disable it. Please help
If you press **ALT-F2** and enter ```
metacity --replace
``` compiz will be disabled.
Then you can try to undo the changes you made.
After that, when you've restored your settings, and if you want to run compiz again, Press **ALT-F2** and enter ```
compiz --replace
```

---

### Post by howefield on 2008-12-19
Or you could open up CompizConfig Settings Manager from the System > Preferences menu.

Then click on the preferences button and then on Reset to defaults button.

When you are done getting back to where you want to be with compiz, you can in the same place as reset to defaults, export your settings to a file from which you can use to reapply your settings in the event of messing up again.

---

### Post by hafey on 2008-12-19
thank you guys, replace did not work with me, so i've removed it from my system.

---

