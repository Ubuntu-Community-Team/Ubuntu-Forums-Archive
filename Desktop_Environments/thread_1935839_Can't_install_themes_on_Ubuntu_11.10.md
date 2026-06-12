---
title: "Can't install themes on Ubuntu 11.10"
date: 2012-03-05
forum: Desktop Environments
---

### Post by LorteMidget on 2012-03-05
Hi there. 

For a couple of days I have been trying to install some themes to my Ubuntu desktop, but I simply can't apply the new themes and icons.

I have been following guides like these:

[http://www.geoffke.be/nieuws/15/](http://www.geoffke.be/nieuws/15/)

[http://www.linoob.com/2011/04/customized-themes-for-ubuntu-11-04/](http://www.linoob.com/2011/04/customized-themes-for-ubuntu-11-04/)

I have tried to apply themes with gtk-Chtheme but nothing happens. 

Which software should I use to apply new themes, and is there another way to do so?

Thank you.

---

### Post by mcduck on 2012-03-05
The program, and the themes, youa re trying to use are outdated.

Ubuntu 11.10 is based on Gnome 3, and thus uses GTK3 instead of the old GTK2. So you'll need to use themes that support GTK3, or preferably both versions (so any app still usign GTK2 would fir correctly with the rest of the theme).

I recommend using [Gnome Tweak Tool]("apt:gnome-tweak-tool") to switch the themes on 11.10. (It appears as "Advanced Settings" in the menu once installed, and is pretty much a semi-official tool for Gnome 3, supported by Gnome developers but not included in the default install)

---

### Post by ewz on 2012-03-05
Looks like you are trying to install old gtk2 themes they don't work very well gtk3 and unity have a look at the link below there is allot of good tutorials on how to install themes in 11.10/12.04. you will need to install Advanced Settings from the Ubuntu Software Center to apply your themes

[http://www.webupd8.org/2012/01/ambiance-and-radiance-colors-theme-pack.html](http://www.webupd8.org/2012/01/ambiance-and-radiance-colors-theme-pack.html)

Hope this helps.

---

### Post by LorteMidget on 2012-03-05
Thanks a lot! that did it :)

---

### Post by ewz on 2012-03-05
Happydays 
This is a really nice theme if you want that Mac look works well on 11.10 
[http://dakiiia.deviantart.com/#/d486q3v](http://dakiiia.deviantart.com/#/d486q3v)

---

