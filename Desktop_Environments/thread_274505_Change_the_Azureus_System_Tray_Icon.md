---
title: "Change the Azureus System Tray Icon"
date: 2006-10-09
forum: Desktop Environments
---

### Post by redDEADresolve on 2006-10-09
Does anyone know how to change the system try icon for Azureus? Its so small and clashes with the overall feel, I want to use a larger better detaiiled blue frog.

thanks

---

### Post by epennings on 2006-10-10
The default tray icon for azureus is located inside Azureus2.jar

```
/org/gudy/azureus2/ui/icons/a16.png
```

If you want to replace it you should open Azureus2.jar as root

```
sudo nautilus 
```

This will open a filebrowser with root privileges. Navigate to your azureus directory and open Azureus2.jar

Replace /org/gudy/azureus2/ui/icons/a16.png with an icon of your choice.

Note : the icon doesnt resize!

---

### Post by redDEADresolve on 2006-10-10
np i'll edit an icon in gimp to 24x24 that should fit nicely into the menu thanks!

---

