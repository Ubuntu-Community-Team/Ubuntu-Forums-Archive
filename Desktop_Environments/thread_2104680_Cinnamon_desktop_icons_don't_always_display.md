---
title: "Cinnamon desktop icons don't always display"
date: 2013-01-13
forum: Desktop Environments
---

### Post by Rsxhawk on 2013-01-13
I just installed Ubuntu 12.04, uninstalled Unity, and installed cinnamon.  Everything appears to be working normally except for one thing.  In the "desktop" configuration panel inside the cinnamon management tool, they give you the option of what icons you want displayed on the desktop like Computer, Home, Trash, and mounted volumes.

For some reason, these icons do not always appear and going back into the configuration tool to "uncheck" and "re-check" them usually does nothing.  Restarting cinnamon with the alt+f2, r trick doesn't work either.  

Any thoughts?

---

### Post by bkaplan on 2013-01-13
I have experienced the same issues, even with a full Mint install.  I don't know what causes it, but I've found that opening your file manager will typically cause the desktop icons to reload.

Hope this helps.

---

### Post by Rsxhawk on 2013-01-13
> **bkaplan said:**
> I have experienced the same issues, even with a full Mint install.  I don't know what causes it, but I've found that opening your file manager will typically cause the desktop icons to reload.

Hope this helps.


Thanks for your reply.  Even with Mint eh?  I'm running the 32-bit Mint w/Cinnamon on my laptop and its absolutely fine, no issues there.  In fact, any issues I've had thus far with linux in general, seem to be with 64-bit versions of the OS.  Maybe there's something to that.  As for opening the file manager, I have tried this and it has no effect whatsoever, very strange!

I guess its not mission critical that I have those icons on the desktop but it just seems like of all the problems I could possibly have, just using a basic function of this DE like having icons on the desktop wouldn't be too much to ask.  :-(

---

### Post by bkaplan on 2013-01-14
You are spot-on with your 64-bit observation.  I had not thought about that connection, but I am also running 64-bit and have not had this particular issue with other installations running 32-bit.

Post back if you find a solution!

Best regards.

---

### Post by Rsxhawk on 2013-01-18
So the only way I know how to "fix" this (its more of a work-around), is by making sure the boxes in the cinnamon desktop manager are unchecked then reboot the machine.  

Once the machine is rebooted and the desktop is back, go back into cinnamon and check the boxes again.  However this by itself will not bring the icons back.  Once the boxes are checked, close the cinnamon settings and then open the file manager as you so kindly mentioned before.....BOOM the icons show up.  

Very strange.

---

### Post by vynonline on 2013-03-28
I am having the same issue in Ubuntu 12.04 32-bit with cinnamon installed .
To get the desktop icons back working again ' logging out and selecting cinnamon and logging in works.
I believe its caused by the default file manager of UNITY being loaded and not nemo because the create launcher option in the right-click shortcut menu in desktop is also not visible when there are no desktop icons.

---

### Post by vynonline on 2013-03-28
> I believe its caused by the default file manager of UNITY being loaded and not nemo ..

I managed to fix this issue of cinnamon in Ubuntu 12.04 '*precise pangolin*' by removing nautilus window manager. I removed unity too.
```
sudo apt-get remove nautilus
```

In lubuntu which uses LXDE desktop environment default , I believe , but I am not sure , we have to remove OpenBox window manager.

---

