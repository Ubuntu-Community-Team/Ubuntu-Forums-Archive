---
title: "GNOME/XFCE Keyboard layout options"
date: 2007-04-16
forum: Desktop Environments
---

### Post by ErikChakravarty on 2007-04-16
In GNOME, the keyboard preferences manager has allowed me to choose a third-level character chooser key for my keyboard (UK Apple PowerBook)  which I set to KP_Enter and it also allows me to add the € sign as a third-level for the '2' key.

Now I have switched to XFCE as I am finding GNOME too resource-demanding especially with Beryl running.

The XFCE keyboard preferences dialog doesn't have the same options available, and although my layout is correct (Apple Laptop, gb mac) , I don't see a way of typing the third-level characters - the KP_Enter I set in GNOME doesn't seem to operate under XFCE, so my € isn't working and neither are any other 3rd level chars.

Is there any way to get this working?

---

### Post by afoglia on 2007-04-20
> **ErikChakravarty said:**
> In GNOME, the keyboard preferences manager has allowed me to choose a third-level character chooser key for my keyboard (UK Apple PowerBook)  which I set to KP_Enter and it also allows me to add the &#8364; sign as a third-level for the '2' key.

Now I have switched to XFCE as I am finding GNOME too resource-demanding especially with Beryl running.

The XFCE keyboard preferences dialog doesn't have the same options available, and although my layout is correct (Apple Laptop, gb mac) , I don't see a way of typing the third-level characters - the KP_Enter I set in GNOME doesn't seem to operate under XFCE, so my &#8364; isn't working and neither are any other 3rd level chars.

Is there any way to get this working?

The default third-level character chooser in Ubuntu's X-windows appears to be the right alt-key.  I can't find a nice XFCE program to change the setting, so you'll have to hand-edit your xorg.conf.  Instructions can be found in a [previous post]("http://ubuntuforums.org/showthread.php?p=1716508#post1716508").  But instead of commenting out the XkbOptions you'll want to replace "lv3:ralt_switch" with the appropriate string for the keypad's enter key.  I believe that will be "lv3:enter_switch" (based on [this debian list post]("http://lists.debian.org/debian-x/2006/10/msg00883.html"), but I could be wrong.

---

