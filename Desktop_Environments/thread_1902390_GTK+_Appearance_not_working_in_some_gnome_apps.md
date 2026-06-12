---
title: "GTK+ Appearance not working in some gnome apps"
date: 2011-12-30
forum: Desktop Environments
---

### Post by kn00buntu on 2011-12-30
Hello,

I recently switched to Kubuntu because of the Unity and Gnome 3 disasters and I really love that Kubuntu tries to make Gnome apps feel native.

However the oxygen-gtk widget style selected in the GTK+ Appearance window doe not get applied to all of the Gnome apps. It works for apps like Pidgin and Gimp but not for Rhythmbox or the Gnome Network Manager. These two still use the horrible Raleigh style. Any ideas why?

Thanks.

---

### Post by samigina on 2011-12-30
In onerig the oxygen-gtk is working just for gtk2 apps. You will need the **gtk3-engines-oxygen**, you can get it from here **ppa:gnumdk/ppa**

```
sudo add-apt-repository ppa:gnumdk/ppa
sudo apt-get update
sudo apt-get install gtk3-engines-oxygen
```

Close your sesion or restart the system.

---

### Post by kn00buntu on 2011-12-30
I have installed the package, restarted the system but the problem was not solved.

---

