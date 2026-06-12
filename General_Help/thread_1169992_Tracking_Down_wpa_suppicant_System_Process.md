---
title: "Tracking Down wpa_suppicant System Process"
date: 2009-05-25
forum: General Help
---

### Post by cmcginty on 2009-05-25
Can someone help explain to me how the wpa_supplicant processes is integrated into the Ubuntu startup scripts.

On my system I have a processes running:

```
4510 ?        S      0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log

```

What script controls the initialization of this process?
**How do I modify the command line options for the wpa_supplicant process?**

---

### Post by cmcginty on 2009-05-25
The wpa_supplicant service is started under DBUS, with the file ```
/usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service
```

---

