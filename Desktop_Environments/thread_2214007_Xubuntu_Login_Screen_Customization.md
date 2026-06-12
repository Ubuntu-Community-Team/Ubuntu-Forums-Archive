---
title: "Xubuntu Login Screen Customization"
date: 2014-03-29
forum: Desktop Environments
---

### Post by edwardjddavis on 2014-03-29
Hello! I'm running Xubuntu 13.10. I would like to get rid of the top panel on the login screen(see below). How would I go about doing this? Your help would  be grealty appreciated. Thanks


[IMG]http://linux.t-tietz.de/sites/default/files/images/xubuntu-saucy25.png[/IMG]

---

### Post by slickymaster on 2014-03-31
Even though there are several items that you can customize in the LightDM greeter (background image, the theme, logo, icon theme and font, language selector, etc), I don't think that you can remove that top panel entirely.

If you want to customize it, all you have to do is to edit your **_/etc/lightdm/lightdm-gtk-greeter.conf_** file.

---

### Post by Toz on 2014-03-31
Just to add to slickymaster's answer, as of [lightdm-gtk-greeter version 1.6]("http://smdavis.us/2013/06/03/lightdm-gtk-greeter-1-6-0-released/"), you can also theme the greeter. This opens up some interesting possibilities.

Using the parameters in /etc/lightdm/lightdm-gtk-greeter.conf, you can hide the clock and the indicators, and via themeing, you can make the panel fully transparent. The only thing you don't seem to be able to change is the hostname display in the top left corner (though with a little bit of creativity, you can change the text colour to something similar to the background colour rendering it invisible - or almost invisible).

The following screenshot was made with Xubuntu 14.04's lightdm screen (hence the different colouring of the login dialog). It should also work on 13.10. Notice that the panel is not visible (well, mostly).
[[img]http://en.zimagez.com/miniature/lightdm0.png[/img]](http://en.zimagez.com/zimage/lightdm0.php)

---

