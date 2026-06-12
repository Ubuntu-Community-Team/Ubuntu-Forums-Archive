---
title: "Help with installing ubuntu"
date: 2009-03-01
forum: Desktop Environments
---

### Post by chang14 on 2009-03-01
I'm trying to install ubuntu on my acer aspire desktop with a intel Q6600, 4GB memory, and when I boot from CD and press install ubuntu, it stalls at the screen after the loading bar. The last few lines it reads are 
startin powernowd... [ok] 
starting hardware abstraction layer hald [ok] 
starting bluetooth 


and it stops. there's no ok after the bluetooh.  Anyone know what to do?

---

### Post by taurus on 2009-03-01
On my machine, the next thing should start/run is Gnome window manager.  So, looks like there is a problem starting the X server on yours.

What kind of graphic card does it have?  Reboot and when you get to the initial screen, press F4 to use the safe graphic mode option to see if it boots this time.

---

### Post by miegiel on 2009-03-01
Does the same thing happen when you choose the option at the top of the list? I believe it's called "try ubuntu" "start ubuntu from CD" or "run ubuntu from CD", can't really remember :)

When ever I had problems installing the *Desktop CD*, using the *Alternate install CD* to install saved me. Though the installation is less user friendly. For example, I remember it didn't install the desktop and I had to install it by hand after the installation with :```
sudo install ubuntu-desktop
```

---

