---
title: "x server wont stop please help!!!"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Akya on 2005-12-13
im trying to install my graphics drive and i need to stop my x server but i installed enlightenment and i dont know the command for it now, could some one help me does anyone know what to do?

---

### Post by RAOF on 2005-12-13
If you're installing the graphics drivers through synaptic, you shouldn't have to stop your X server.  If you aren't installing through synaptic, I hightly recommend you do ;)

However, if you really want to, the command "sudo /etc/init.d/gdm stop" should kill the X server & drop you back to a console.  Unless you're using a weird login manager.  Then it might be /etc/init.d/kdm stop, if you're using the KDE login manager.

---

### Post by Akya on 2005-12-13
im using the enlightenment login manager, what should i do? how do i figure out how to stop it1 and 2 how can i use synaptic?

---

### Post by RAOF on 2005-12-13
The enlightemnent login manager is probably something like "edm".  Anyway, whatever script it is will be located in /etc/init.d.  Have a look there, and there's probably something *dm.  sudo /etc/init.d/<whatever it is>dm stop should kill X.

As for synaptic: What is your graphics card?  If it's an nvidia card, you want to install the "nvidia-glx" package.  If it's an ATI card, you want to install the "fglrx" package.  You can find synaptic under System->Administration->Package Manager (Synaptic)

---

### Post by Akya on 2005-12-14
ya that works i guess but i still get lag on the higher quality screensavers and i have a nvidia gf 6800 with a pentium4 2.6 ht and 1 gb of ram so they shouldnt be lagging

---

### Post by RAOF on 2005-12-14
Well, to install the nvidia drivers you install the nvidia-glx package, and then run "sudo nvidia-glx-config enable" at a console.

---

