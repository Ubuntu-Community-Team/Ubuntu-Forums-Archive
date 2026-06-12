---
title: "Beryl"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by deuchar1 on 2007-03-26
Okay okay, I know it's rickety and prone to crashes, bugs etc - but I installed Beryl to give it a whirl. 

One problem I'm having that I've not been able find documented elsewhere is a funny glitch where when I run Beryl I lose the titlebars of all windows and have to ALT+F4 close them.

Anyone have any ideas why this might be happening? Everything works fine aside from the titlebars disappearing and it's really annoying!

Cheers,
G

---

### Post by Kobalt on 2007-03-26
Which graphic card do you have ? What method did you use to install Beryl ?
You can try to right-click the Beryl icon in your notification area, set the window decorator to Emerald, click "Reload Window Decorator", and then make sure the window manager is set to Beryl, and then click "Reload Window Manager"...
You can try to install heliodor through Synaptic, install or reinstall emerald & emerald-themes...

---

### Post by deuchar1 on 2007-03-26
I'm running a GeForce MX 5200 and installed through Synaptic. I added the Beryl repositories and grabbed what I needed. I'll give your suggestions a whirl, thanks!

---

### Post by Kobalt on 2007-03-26
Did you install the proper drivers for your graphic card ?

---

### Post by compmodder26 on 2007-03-26
Try running this command:

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

