---
title: "how to change keyboard to &quot;us&quot; in ubuntu command line"
date: 2009-02-14
forum: General Help
---

### Post by Electricalkhukuma on 2009-02-14
My current settings are of "gb" keyboard & whenever i press key '3', it shows "pound(sign)" instead of showing "#" on the command prompt. How can i solve this problem?? 

I have also tried to configure "xong.conf" but it displayes "PERMISSION DENIED" message, whenever i try to save the settings.

---

### Post by geirha on 2009-02-14
Does it have to be from the command-line? If you go to System -> Preferences -> Keyboard -> Layouts(tab), you can add a us keyboard layout and make it the default.

---

### Post by Electricalkhukuma on 2009-02-14
*Does it have to be from the command-line? If you go to System -> Preferences -> Keyboard -> Layouts(tab), you can add a us keyboard layout and make it the default.*

If have added the us keyboard in this same manner & it is working fine in GUI but the problem is that it is still showing "pound(sign)" instead of "#" in the command prompt.

---

### Post by geirha on 2009-02-15
Try ```
sudo dpkg-reconfigure console-data
```

---

