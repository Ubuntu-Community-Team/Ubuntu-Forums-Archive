---
title: "xubuntu 8.10 screen resolution"
date: 2008-12-31
forum: General Help
---

### Post by jon4528 on 2008-12-31
earlier today I installed xubuntu 8.10 on a Dell x200 which should support 1024 x 768 screen resolution. Within the settings screen function the best available is 800 x 600. I have read various threads indicating I should run sudo dpkg -reconfigure -phigh xserver-org but this just made the situation worse. Within the older version of fedora I was running the resolutions could be manually set in the xorg.conf file but this doesn't seem to work in xubuntu 8.10. Is there a way to fix this or should I downgrade to an older version or Fedora/Linpus?

---

### Post by ajmorris on 2008-12-31
> **jon4528 said:**
> earlier today I installed xubuntu 8.10 on a Dell x200 which should support 1024 x 768 screen resolution. Within the settings screen function the best available is 800 x 600. I have read various threads indicating I should run sudo dpkg -reconfigure -phigh xserver-org but this just made the situation worse. Within the older version of fedora I was running the resolutions could be manually set in the xorg.conf file but this doesn't seem to work in xubuntu 8.10. Is there a way to fix this or should I downgrade to an older version or Fedora/Linpus?

hi there,
if sudo dpkg-reconfigure xserver-xorg didnt work, you might have to manually add the modes to /etc/X11/xorg.conf so that you can set that resolution. You say that it did not seem possible in (x)ubuntu. It is actually possible, whilst the ubuntu devs have introduced all these auto-detection methods, you can override them, if it detects your hardware incorrectly. In your /etc/X11/xorg.conf look for your 'screen' section. It should say automatically configured, or something along those lines. Just add a 'modes' SubSection to it, and specify the modes you want. If there is no screen section, you can add it. If you are not particularly proficient with editing xorg.conf, you can always copy the xorg.conf from fedora, on the same machine, it should work in ubuntu, with the exception of any path statements that may exist in fedora, but don't exist in ubuntu. Although, Xorg *should* ignore these statements. If run into any trouble though, with any of what i have said above, just post back here with errors.
Another option, to see if your Xorg is configured with the 1024x768 resolution, is to try to set it manually with xrandr. So try running this command in a CLI:

```
sudo xrandr -s 1024x768
```


AJ

---

