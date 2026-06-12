---
title: "How to install plugin????"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by doctera on 2008-02-21
Hello, i have a bootable ubuntu CD..
When i use ubuntu with network, i can install all plugins that i need..
At home i dont have internet, but i have a plugins on my USB..
How can i install for example cube plugin that i have on my usb (beryl core 0.2.1.tar.gz)
When i go to add remove application, it only gives me the option to install plugins from internet!
Please help.. tnx

---

### Post by northern lights on 2008-02-21
What kind of ubuntu distribution do you have? If you have gutsy, it ships with compiz-fusion, which has the cube you want. You might not have "Advanced Desktop Effects" enabled. Is there such an entry in your "System > Preferences" menu? If not (and you're indeed on gutsy) run```
sudo apt-get install compizconfig-settings-manager
```

---

