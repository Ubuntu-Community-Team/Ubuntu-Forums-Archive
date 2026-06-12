---
title: "How to activate transparent menu bar like this"
date: 2014-07-08
forum: Desktop Environments
---

### Post by danbuz on 2014-07-08
This [=panel%20cairo%20xfce&filters[primary]=images"]bottom bar]("http://media.photobucket.com/user/ic_deadpipol/media/My%20PC/Screenshot-22.png.html?filters[term) look very nice, and I would like to add it to my xfce desctop. Anyone know how could be done?

Thanks in advance!

---

### Post by ajgreeny on 2014-07-08
If you mean the row of icons at the bottom of the screenshot, that is **cairo-dock** which you can find in the repositories and install in the usual way.

---

### Post by Frogs Hair on 2014-07-08
That's a dock application _possibly_ cairo/glx dock , I can't be sure because there are many themes  and ways to customize it.

---

### Post by danbuz on 2014-07-09
Thanks guys, I'll try it!

P.S. Searched all over the web for customization such like this, and nothing found. Is this transparent effect depends on compiz?
[Here is]("http://s480.photobucket.com/user/Arch-newb/media/Screenshot-56.png.html") another example.. :) ?

---

### Post by amanchesterman on 2014-07-09
The example you've given in post #4 looks to me like a standard xfce panel set to transparent. I have something very similar on my own laptop. The settings of my panel (in case you want to try them) are:
On the 'Display' tab: mode horizontal, panel locked, automatically show and hide;
On the 'Appearance' tab: style none (= use system style), alpha 15, enter 100, leave 100.
Suggest you create a bottom panel yourself and experiment with different settings before you try installing cairo or compiz.

---

### Post by Frogs Hair on 2014-07-09
> **danbuz said:**
> Thanks guys, I'll try it!

P.S. Searched all over the web for customization such like this, and nothing found. Is this transparent effect depends on compiz?
[Here is]("http://s480.photobucket.com/user/Arch-newb/media/Screenshot-56.png.html") another example.. :) ?

I am most familiar with the xfce session and application transparency can be set by enabling compositing in window manager tweaks and then adjusting opacity sliders

---

### Post by ajgreeny on 2014-07-09
Did none of you notice that the caption to the screenshot shows:-
> **Linux Mint 9 LXDE + XFCE**

                     
 
                                Linux Mint 9 LXDE modded -XFCE Desktop Environment -Tint2 panel [COLOR=#ff0000]-Cairo Dock[/COLOR] -Conky            

and if I remember correctly, cairo-dock transparency depends upon a compositing window manager, so presumably compiz would allow it, as would xfwm in xfce4, as well as many others.

---

### Post by danbuz on 2014-07-18
And still I'm not able to achieve the same effect.. Someone familiar with this kind of settings?

---

### Post by Frogs Hair on 2014-07-18
Are you asking about the dock or the transparency settings or the dock . The second picture seems to be transparent xfce panel on the bottom filled with launchers . As for the dock in the first picture it could be a pre-made theme or something that user created with the Cairo dock settings.

 I achieved the following with the panel settings and window manager tweaks in the xfce session. I didn't fill the panel on the bottom with launchers because it is time consuming. ;)   Most people learn by experimenting  but Cairo/GLX dock does offerer some themes in its settings. Right click on the dock and take a look around.

---

### Post by Ghune on 2014-07-19
Wao, your theme is fantastic Frogs Hair!

---

### Post by Frogs Hair on 2014-07-19
Most of this still applies in XFCE , but the desktop settings GUI has changed . [http://www.maketecheasier.com/customize-xfce-desktop/](http://www.maketecheasier.com/customize-xfce-desktop/)

---

