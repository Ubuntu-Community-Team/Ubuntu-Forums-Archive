---
title: "Unity 2d Autohide issues with Natty"
date: 2011-05-30
forum: Desktop Environments
---

### Post by farproc on 2011-05-30
I just installed Natty / 11.04 on a desktop PC with an nVidia card thats a few years old.
As a result, when I activated the the  NVidia driver (173), it said that it was "activated but not being used". So Unity would not start.
I had to de-activate the OEM driver and use the Experimental 3D Support for NVidia cards" driver, which is used, but Unity then did not draw correctly.

So I then Installed Unity 2D using the Ubuntu Software Center. So I now have a Unity desktop, BUT, my Unity 2D Launcher is not auto hiding. I found a gconf script that suppose dto toggle the Unity 2D Launcher autohide, but no matter how I toggle it, If I maximize a window it goes under the Launcher and I can't access the left edge of the window.

Any ideas?

---

### Post by farproc on 2011-06-09
No updates. No autohiding.
Is there a gui at least for configuring Unity 2D?

---

### Post by SoftGround on 2011-06-20
I have tried **Unity 2D Desktop Settings** on my old T22 laptop, which would not run standard Unity.
See [http://www.addictivetips.com/ubuntu-linux-tips/tweak-with-unity-2d-settings-enable-compositing-ubuntu-linux/]("http://www.addictivetips.com/ubuntu-linux-tips/tweak-with-unity-2d-settings-enable-compositing-ubuntu-linux/") 

It seemed to work a lot better when Unity 2D Compositing was turned on, the menu moved out of the way of other windows, but this broke Ubuntu Classic and made it come up in the badly broken(No Effects) mode.  So not so good it you want to use both alternatly or for different users.  
Turning Compositing off for Unity 2D restored Classic compositing to its original condition.

Personally I can't make my mind up yet, it probably takes up to much space on my small screen.  I think more configuration is on the way for 3D, so that may be better for 2D soon as well.

---

### Post by SoftGround on 2011-06-22
Just tried Gnome with Cairo and I prefer it.

---

### Post by SoftGround on 2011-06-27
Apparently the next version of Ubuntu (11.10) will not have Ubuntu Classic. So if Unity 2D is not good enough you may need to switch to Xubuntu, it may take a little getting used to!

If you think of trying it on top of stabdard ubuntu, work our how to revert to ubuntu login first, it was a bit of a pig. A backup/restore might have been simpler than trying to uninstall all of xubuntu.

---

