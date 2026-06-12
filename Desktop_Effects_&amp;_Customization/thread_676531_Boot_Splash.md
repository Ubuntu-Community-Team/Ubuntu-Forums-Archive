---
title: "Boot Splash"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by Janxeh on 2008-01-23
Hey Guys and Girls,

I am using Kubuntu 7.10
Does someone know where the boot splash information file is?

I changed my boot splash screen got bored of that one and changed it again, but it did not change. No matter which one i select from sys settings>splash it shows the same boot splash screen.
Grrrr 

Thanks

---

### Post by mssever on 2008-01-24
> **Janxeh said:**
> Hey Guys and Girls,

I am using Kubuntu 7.10
Does someone know where the boot splash information file is?

I changed my boot splash screen got bored of that one and changed it again, but it did not change. No matter which one i select from sys settings>splash it shows the same boot splash screen.
Grrrr 

Thanks

Look at /boot/grub/menu.lst. After making any changes, be sure to run ```
sudo update-grub
```

---

