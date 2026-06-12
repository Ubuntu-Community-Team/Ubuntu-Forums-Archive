---
title: "network icon disappeared"
date: 2010-01-08
forum: Desktop Environments
---

### Post by Black Bart on 2010-01-08
Ubuntu 9.10/Gnome 2.28.1/Clean install

At first boot there is a network icon on top right corner. 
But after update packages installed and machine had rebooted the network icon have disappeared. Instead of network icon there is uknown icon you would see in first attached pic. This icon is not clicable nothing to do with it.

I'm able to remove it and add network icon again (2nd attachment). But after reboot the unknown icon shows up again.

What's happen with Ubuntu 9.10? How to fix my panel fix my network icon? Why so many bugs pours out from Ubuntu 9.10? Why Amarok stopped on next file after playing first? Why DVD icon haven't disappered after I'd unmount DVD so I need manual switch it off? Where's ordinary rules in Gufw?

But don't suggest me downgrade to 9.04. I know I can do this. 
But still there's a "stable" release announcement of 9.10 I'd like know how to fix network icon, please.

---

### Post by kuurozaki on 2010-01-08
Do you have Network Manager (nm-applet) entry on your Startup Applications? ('System > Preferences > Startup Application')

---

### Post by Black Bart on 2010-01-08
> **kuurozaki said:**
> Do you have Network Manager (nm-applet) entry on your Startup Applications? ('System > Preferences > Startup Application')

Yes, I do.
```
nm-applet --sm-disable
```

---

### Post by zloy_smiertniy on 2010-10-10
This happened to me too, and I have no idea what to do, I cant choose it to appear on any menu bar and also the little icon that allowed me to swith between langauges in the keyboard disappeared. Im sorry if it is a silly question but I havent been able to put it back, it seems as it had hidden or something. Can someone help me?

---

### Post by Dyegov on 2010-10-10
You could always try to reset the panel to default:

```
rm -r ~/.gconf/apps/panel
```

---

