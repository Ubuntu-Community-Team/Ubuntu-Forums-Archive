---
title: "Simplifying Ubuntu Startup"
date: 2011-04-15
forum: Desktop Environments
---

### Post by twtgd09 on 2011-04-15
Okay, I've been *mostly* happy with ubuntu after switching over from windows (unfortunately i cant go back to windows, its broken now :/) But the boot time is somewhat concerning and/or frustrating to me. In windows, I could boot my machine in less than thirty seconds. Ubuntu takes a bit longer due to a) the grub bootloader. Does anyone know how to remove the Grub bootloader unless i push a magic button? I'm running ubuntu 10.10. b) ubuntu does not automatically select my user name as the default, even though im the only user other than guest, how can i make it, by default, select me so i just need to type in my password? c) after logging in, it takes a while for my stuff to load. I've tried editing my startup programs, but ive heard that ubuntu uses metacity to open compiz or something like that, which would slow things down. Also, i would like access to the more specific things that load when i turn on ubuntu, kind of like services .msc in windows. Thanks.

---

### Post by Frogs Hair on 2011-04-15
Part of the answer may be to set Ubuntu to login automatically as a selected user name by changing the settings in Administration > Login Screen , but that would reduce security .

I'm confused with the other part , it sounds like you want to use the Windows boot loader and remove Grub even though Windows is broken .

---

### Post by twtgd09 on 2011-04-15
I want to set grub to automatically boot to ubuntu after deleting my broken installs. Then, i want to make the menu hidden until i push a button, hold down shift perhaps, to shave ten seconds off of boot time.

---

### Post by 3177 on 2011-04-15
as was already said login with your password, and if you want, set your user to login automatically. As for grub not coming up unless you push a button:[http://www.ubuntugeek.com/show-and-hide-the-grub-menu-on-ubuntu.html](http://www.ubuntugeek.com/show-and-hide-the-grub-menu-on-ubuntu.html)

---

### Post by marin123 on 2011-04-15
or you can edit grub... set delay time to 1 sec...

```
sudo apt-get install startupmanager
```

---

### Post by twtgd09 on 2011-04-15
i want to be able to boot into windows once i get my repair disc to fix the drivers though. i just dont want to grub menu to show up unless i tell it to, checking out the link now.

---

