---
title: "Lost Window Control Buttons In Firefox/Ubuntu"
date: 2009-02-21
forum: General Help
---

### Post by chiques on 2009-02-21
Hello Everyone,
I had Ubuntu run it's recommended updates last night and this morning after a reboot I noticed the Firefox windows is missing the "Minimize", "Resize" and "Close" buttons. I also noticed Firefox dominates the whole screen and no longer allows me to select different task bar items or launch anything from the Ubuntu menu. The only way to get to anything is to close Firefox. 

[[IMG]http://img3.imageshack.us/img3/9794/firefoxproblem.th.jpg[/IMG]](http://img3.imageshack.us/my.php?image=firefoxproblem.jpg)

I have tried "F11" and that did not work. Is there any way to reset or "remove" the last update that messed this up?

Please feel free to ask for configuration files.

---

### Post by chiques on 2009-02-21
I've made some progress with this. Choosing F11 makes the whole window dominate the screen but it also brings the buttons back. Choosing the "Unmaxmize" selection will bring Firefox back to the standard operation. If I choose the "Unmaximize" button again, I loose my Applications toolbar and my window control buttons.

[[IMG]http://img4.imageshack.us/img4/9344/firefoxworking.th.jpg[/IMG]](http://img4.imageshack.us/my.php?image=firefoxworking.jpg)

This appears to be some sort of GUI bug but I have no way of diagnosing it.

---

### Post by perpetualcacophany on 2009-02-21
This happens a lot.

To fix:

Get CCSM:

```
sudo apt-get install compizconfig-settings-manager
```

Open it up through System -> Preferences -> CompizConfig Settings Manager

Scroll down to the Utilities section and select Workarounds.

Uncheck "Legacy Fullscreen Support"

That should fix your problem.

---

