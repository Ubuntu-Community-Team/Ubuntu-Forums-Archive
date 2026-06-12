---
title: "How do i change the &quot;Bluetooth Manager Applet&quot; icon in &quot;Notification Area&quot;?"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by Repgahroll on 2008-01-12
Hello Guys :D
This is my first thead here in Ubuntu Forums! :D :D

I'm just customizing a little my Gnome, and i'm modifying the Notification Area icons to monochrome ones, but i don't know how to change the Bluetooth Manager icon :(
To change the lcd brightness applet icon, i just made a search for "brightness*svg", and replaced the respective icon... but now i already replaced all the "bluetooth*svg" and "bluetooth*png" images, but the icon still the same! :(... Do anyone have any idea on how to do it?

Thank you very much for trying to understand my bad English!

---

### Post by Repgahroll on 2008-01-12
Take a look at this screenshot of my desktop.

This image of the bluetooth symbol just don't exists on my computer! (at least not in the format of an image).

Can it be in a compressed format as tarball?(like the grub image)

Is there any hope to me?


Sorry my bad english - Thanks

---

### Post by spdf on 2008-01-14
Take a look in /usr/share/gnome-bluetooth/pixmaps

---

### Post by Forlong on 2008-01-14
The icon you are looking for is probably ```
/usr/share/icons/gnome/24x24/stock/io/stock_bluetooth.png
```

---

### Post by Repgahroll on 2008-01-15
> **spdf said:**
> Take a look in /usr/share/gnome-bluetooth/pixmaps

:( There's no such directory...

> **Forlong said:**
> The icon you are looking for is probably ```
/usr/share/icons/gnome/24x24/stock/io/stock_bluetooth.png
```

I had tried it before... didn't work :(

The solution was to add a stock_bluetooth.png image to my theme folder (~./themes/THEMENAME/RESOLUTION/stock_bluetooth.png) i discovered it after downloading the Mac4lin gnome theme :D...

Just don't ask me why even modifying every bluetooth image on the system, the icon still the same :(... 

Now i know how to do what i wanted, but i don't know why what i wanted happened :(


[COLOR="DarkRed"]_**Thank you all VERY MUCH!!! :D :D :D**_[/COLOR]

---

