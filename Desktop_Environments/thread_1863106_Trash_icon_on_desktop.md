---
title: "Trash icon on desktop"
date: 2011-10-17
forum: Desktop Environments
---

### Post by NModern on 2011-10-17
How to add trash icon to the desktop on ubuntu 11.10 ?

[http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/)
This way is not working.

---

### Post by NModern on 2011-10-17
??????????77777

---

### Post by mcduck on 2011-10-17
The reason why that method isn't working is that 11.10 uses Gnome 3, which has moved the settings from Gconf to GSettings/dconf.

Easiest way to enable the icons is to install [gnome-tweak-tool]("apt:gnome-tweak-tool"), which gives you options for desktop icons and some other nice features that aren't available in any of the default option dialogs. Like changing your window, GTK3 and icon themes, customiziing the fonts used etc.

Alternatively you can install the [dconf-tools]("apt:dconf-tools") package, and then use dconf-editor in similar way as the guide you linked uses gconf-editor. The options will appear in org/gnome/nautilus/desktop.

...or you can run the following command in a terminal:
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

---

### Post by zaphodbblx on 2011-10-22
> **mcduck said:**
> The reason why that method isn't working is that 11.10 uses Gnome 3, which has moved the settings from Gconf to GSettings/dconf.

Easiest way to enable the icons is to install [gnome-tweak-tool]("apt:gnome-tweak-tool"), which gives you options for desktop icons and some other nice features that aren't available in any of the default option dialogs. Like changing your window, GTK3 and icon themes, customiziing the fonts used etc.

Alternatively you can install the [dconf-tools]("apt:dconf-tools") package, and then use dconf-editor in similar way as the guide you linked uses gconf-editor. The options will appear in org/gnome/nautilus/desktop.

...or you can run the following command in a terminal:
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

 Even though this made me deduct -100 nerd points from my balance this did the trick! THANKS!!

---

### Post by ehering on 2011-11-10
Hi,

i have the same problem as the OP, but for some reason none of the options described here work - I can change the settings, but no effect takes place and the trash icon (as well as the other icons you can make visible) remain invisible, even after relogging or rebooting.

What could be the reason? I would appreciate if someone could help clear up my confusion.

Cheers,

ehering

---

### Post by ehering on 2011-11-11
Well what can I say, it wouldn't work 20 times, but now it does...

Cheers

---

### Post by Frogs Hair on 2011-11-11
Install the Gnome Tweak Tool / Advanced settings and open desk top . Other useful settings are included as well .

---

### Post by ehering on 2011-11-13
> **Frogs Hair said:**
> Install the Gnome Tweak Tool / Advanced settings and open desk top . Other useful settings are included as well .

Thanks for your help, but as I tried to point out in my post, this did not work for me. The icons remained invisible no matter what. Strangely, after some time and numerous relogs/reboots, it started to work all of a sudden and now I have the icons on my desktop.

Thanks nonetheless for your reply,

Cheers

---

### Post by nativehound on 2011-12-24
Thank you, mcduck.

---

### Post by lolpenguin on 2011-12-25
> **ehering said:**
> Thanks for your help, but as I tried to point out in my post, this did not work for me. The icons remained invisible no matter what. Strangely, after some time and numerous relogs/reboots, it started to work all of a sudden and now I have the icons on my desktop.

Thanks nonetheless for your reply,

Cheers

You are not using Ubuntu 11.10 if they did not work.

---

