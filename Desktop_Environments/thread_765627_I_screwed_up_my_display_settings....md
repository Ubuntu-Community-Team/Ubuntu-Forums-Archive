---
title: "I screwed up my display settings..."
date: 2008-04-24
forum: Desktop Environments
---

### Post by dloyer4 on 2008-04-24
Now, when Gnome opens up, all I get are scattered horizontal lines...almost looks like the cable went out on my TV. Is there a way to boot Gnome into some sort of safe-mode so I can reset the display settings back to something I know will work?

Thanks,
Dennis (total Linux/Gnome Newb)

---

### Post by Patsoe on 2008-04-24
Assuming we're talking about Ubuntu Hardy (8.04) here, if you select recovery mode from the GRUB boot menu you will get to a recovery menu with an xfix option.

See [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)
> A new X windows recovery feature is available. If you are unable to boot after attempting changes, you can reboot, choose the restore option in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.

---

### Post by overdrank on 2008-04-24
> **dloyer4 said:**
> Now, when Gnome opens up, all I get are scattered horizontal lines...almost looks like the cable went out on my TV. Is there a way to boot Gnome into some sort of safe-mode so I can reset the display settings back to something I know will work?

Thanks,
Dennis (total Linux/Gnome Newb)

Hi and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by dloyer4 on 2008-04-24
ALL RIGHT!!  Got it working properly again...sorta. The display is still having problems, but they're the same problems it was having when I screwed it up, so it's usable at least :)

Thanks,
Dennis

---

### Post by overdrank on 2008-04-24
> **dloyer4 said:**
> ALL RIGHT!!  Got it working properly again...sorta. The display is still having problems, but they're the same problems it was having when I screwed it up, so it's usable at least :)

Thanks,
Dennis

Ok what version of Ubuntu are you using, Feisty, Gusty? what is the model of the graphics card? This issue you have are vertical lines on the desktop?
Also could you post what fix worked for you as I just learned of the ```
sudo xfix
```

---

