---
title: "Bluetooth on KDE"
date: 2011-06-13
forum: Desktop Environments
---

### Post by Lars Noodén on 2011-06-13
I had bluetooth working in KDE on Natty.  After a re-install of the OS, the icon disappeared from the panel.  How can bluetooth be restored manually?

---

### Post by Lars Noodén on 2011-06-13
Adding the package Bluedevil appears to have given the bluetooth icon in the system tray.  It says it still can't find the bluetooth adapter.

Edit: If I add a USB Bluetooth adapter, KDE can find and use it to attach external devices.  It is the built-in adapter which it has ceased to find and use.

Edit2: I can scan from the USB Bluetooth adapter and find the built-in device.  
```

$ hcitool scan
Scanning ...
        x:x:x:x:x:x       Apple Bluetooth Device

```

Why can't KDE find it and use it like before?

---

### Post by Lars Noodén on 2011-06-21
KDE is still telling me that there are no bluetooth adapters to be found even though it is able to use the bluetooth mouse at the same time.

---

