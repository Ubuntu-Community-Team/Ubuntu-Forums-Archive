---
title: "Conky and compiz, how to remove shadows?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by pat23_2007 on 2009-03-31
Hi

I have conky running as a transparent window, but it has shadows under it and it looks bad. How do i get compiz or what ever draws shadows to not do it to the conky window?

---

### Post by James_Lochhead on 2009-03-31
You need the Compizconfig settings manager. In it there should be an entry for Window decoration. Under window decoration there is a box for shadows. You can disable shadows for specific types of windows if you know how (I don't for conky). I don't draw shadows under the gnome panels using:

any& !(type=dock)

You can also just make decrease the shadow size and transparency for everything, or turn shadows off.

---

### Post by pat23_2007 on 2009-03-31
ok you have lost me. sorry

---

### Post by Lunx on 2009-04-01
Have you got the settings manager for Compiz installed? If not you can open Synaptic and search for compizconfig-settings-manager, or install it from the command line using

```
sudo apt-get install compizconfig-settings-manager
```

Once it's installed you can access it from the **System --> Preferences** menu and use it to change the shadows via **Effects --> Windows Decorations **. The settings you want to change are the radius and opacity ones, just turn then down. This will get rid of the shadow effect but it will be for all windows. I'm only a newbie myself, so haven't got up to speed on how you change it for individual windows (but like James said, I'm sure there's a way it can be configured just for conky)

---

### Post by pat23_2007 on 2009-04-01
> **Lunx said:**
> Have you got the settings manager for Compiz installed? If not you can open Synaptic and search for compizconfig-settings-manager, or install it from the command line using

```
sudo apt-get install compizconfig-settings-manager
```

Once it's installed you can access it from the **System --> Preferences** menu and use it to change the shadows via **Effects --> Windows Decorations **. The settings you want to change are the radius and opacity ones, just turn then down. This will get rid of the shadow effect but it will be for all windows. I'm only a newbie myself, so haven't got up to speed on how you change it for individual windows (but like James said, I'm sure there's a way it can be configured just for conky)

Thanks, I actually figured it out on my own already. I just added this in windows decorations, in the window shadow line: (any) & !(class=Conky) that worked prefectly

---

### Post by Lunx on 2009-04-01
> **pat23_2007 said:**
> Thanks, I actually figured it out on my own already. I just added this in windows decorations, in the window shadow line: (any) & !(class=Conky) that worked prefectly

Cool, now I've learned something new also :D

*goes off to play with Compiz*

---

