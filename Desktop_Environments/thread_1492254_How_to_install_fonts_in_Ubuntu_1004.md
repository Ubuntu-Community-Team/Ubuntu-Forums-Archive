---
title: "How to install fonts in Ubuntu 10:04?"
date: 2010-05-24
forum: Desktop Environments
---

### Post by duncan503 on 2010-05-24
Hi I would like to find out how to install new fonts in ubuntu 10:04 in 9:10 it was easy (in file system create a new folder named .fonts that was it) in 10:04 that another story cannot create a folder in file system, then what?....
 thank u for the help!
 Best regard : D

---

### Post by Skara Brae on 2010-05-24
This is a good question (I wanted to get the "Vera" fonts, as found at [http://ftp.gnome.org/pub/GNOME/sources/ttf-bitstream-vera/1.10/]("http://ftp.gnome.org/pub/GNOME/sources/ttf-bitstream-vera/1.10/"))

Duncan503, this seems to work for 10.04:

> 1. Go to your home folder
2. Enable &#8220;Show Hidden Files&#8221; option from Nautilus View menu
3. Then create new folder with name &#8220;.fonts&#8221; (with dot in front)
4. Now in new folder copy all your true type fonts. If you want to copy your Windows fonts, you can find it in WINDOWS/Fonts folder.
5. Now restart and new fonts will be in use.

-[http://www.detector-pro.com/2009/04/how-to-install-fonts-on-ubuntu-904.html]("http://www.detector-pro.com/2009/04/how-to-install-fonts-on-ubuntu-904.html")

It works! Isn't GNU/Linux (Ubuntu) wonderful? :D

[QUOTE="duncan503"]in 10:04 that another story cannot create a folder in file system[/QUOTE]
Uhh, it worked with me.

---

### Post by Skara Brae on 2010-05-24
Or this? (even easier)

[QUOTE="Dilip Vamanan"]Guys, Its so simple. Download the file. Right click and Open the .TTF with Font Viewer. Install Option is present there.[/QUOTE]

---

### Post by hok00age on 2010-05-25
Don't forget to run
```
fc-cache -f -v
```

Your fonts will be available without restarting.

---

### Post by Barafu Albino Cheetah on 2010-05-25
Go into Synaptic and, in options to any installed font package, look where it writes itself. Place your files there too. It is an universal way to see where fonts/icons/backgrounds/sounds/anything live in a given Linux distribution

---

