---
title: "I'd like to change my desktop from Budgie"
date: 2019-03-15
forum: Desktop Environments
---

### Post by Astralogic on 2019-03-15
Hi, I'm currently running the Budgie desktop and would like to try the official desktop environment, I don't know what it's called though :(

Couolkd someone tell me how to install it please?
Thanks

---

### Post by Frogs Hair on 2019-03-15
You can install using the following command , but be aware that Ubuntu and Budgie use different login screens and you may be presented with choice to use GDM during the installation. You can also download Ubuntu and try it from live usb or dvd. A clean installation could be a better choice than two desktops.

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)


 ```
sudo apt install ubuntu-desktop
```

---

### Post by Astralogic on 2019-03-21
> **Frogs Hair said:**
> You can install using the following command , but be aware that Ubuntu and Budgie use different login screens and you may be presented with choice to use GDM during the installation. You can also download Ubuntu and try it from live usb or dvd. A clean installation could be a better choice than two desktops.

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)


 ```
sudo apt install ubuntu-desktop
```

Thanks,I made the switch and everythings wokring fine. How do I uninstall the bidgie desktop? I might as well save some space.

---

### Post by Frogs Hair on 2019-03-21
I have removed Unity, but not budgie and don't have a comprehensive list of commands to safely remove everything. Just removing the budgie-desktop meta package will leave many leftover packages.That's why a clean installation was suggested.

---

