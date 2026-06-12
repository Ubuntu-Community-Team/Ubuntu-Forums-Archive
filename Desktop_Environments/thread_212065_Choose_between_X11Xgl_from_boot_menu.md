---
title: "Choose between X11/Xgl from boot menu"
date: 2006-07-09
forum: Desktop Environments
---

### Post by playmesumch00ns on 2006-07-09
I love using Xgl/Compiz, but when I'm doing OpenGL development I'd like to run plain old X11/metacity to get the best out of my gfx card.

So is there a way I can choose which configuration I want from the boot menu?

If, for instance I could get grub to run a script just after linux had loaded, but before X had initialized, then I could do something like:
```

#if Xgl/compiz was chosen, copy in custom xorg.conf with Xgl extensions
cp /etc/X11/xorg.conf-Xgl /etc/X11/xorg.conf-custom

---

# otherwise copy 'normal' xorg.conf
cp /etc/X11/xorg.conf-X11 /etc/X11/xorg.conf-custom


```

---

### Post by Dubbayoo on 2006-07-09
depending on the guide you followed you should have an option to login to gnome using xgl or not.

---

### Post by Anduu on 2006-07-09
If you use an ATI card this guide works great  [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by jimmygoon on 2006-07-09
> **Dubbayoo said:**
> depending on the guide you followed you should have an option to login to gnome using xgl or not.

But the problem is... is that the server is already running. AFAIK you're just choosing whether or not to (start Xair?) and/or Compiz

---

### Post by firetux on 2006-07-09
Do some reading about bash scripting!

Here's a simple script to turn compiz/xgl off when its running and turn it on if metacity is running.

```
#!/bin/bash
if ps -A | grep -e " compiz.real$" > /dev/null; then
	killall gnome-window-decorator
	metacity --replace &
else
	gnome-window-decorator &
	compiz --replace gconf &
fi
```

Just copy-paste that into a textfile(no extention), make it executable, and add a custom launcher to your panel or desktop which refers to this file.
This way you can toggle quick&dirty from compiz to metacity and the other way around. You don't even need to log out and in again.

---

