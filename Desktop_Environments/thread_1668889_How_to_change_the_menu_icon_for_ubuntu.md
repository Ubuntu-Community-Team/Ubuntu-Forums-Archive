---
title: "How to change the menu icon for ubuntu?"
date: 2011-01-16
forum: Desktop Environments
---

### Post by Kyralik on 2011-01-16
I know this has been posted before, but non of the former posts helped me.  What I would like to figure out is how to change the small Ubuntu logo next to the Applications, Places, System widget on the panel.  I'm not sure if this is part of a theme or if it's a system file.  Either way; I would love some help on this, as this will bring me one step closer to: world domination / creating a theme, how different are they really?

---

### Post by Krytarik on 2011-01-17
This is the Readme of the "black-white_2-Style" icon theme, [http://gnome-look.org/content/show.php/black-white+2+Style?content=72619:](http://gnome-look.org/content/show.php/black-white+2+Style?content=72619:)
> ReadMe to black-white 2 

1.Change your main menu icon
2.different folder icons

1.-add a "Main Menu" to your panel
 -run gconf-editor
 -navigate to /app/panel/objects
 -find a object_x with the "object_type=menu-object".
 - tick up "use_custom_icon"
 -type in "custom_icon" start-here1, start-here2, ... , start-here11
 - if you doesn't like any of this icons you can browse here to an image of your choice

2.In this version I add some different icons for your downloads, documents, music,... folder.  
 -To use them you must unpack the tar.gz package.
 -right click on the folder you wants to change and presspreference    
 -click on the folder icon and browse to the unpacked black-white2.tar.gz folder and go on to /  scalable/places (sometimes /scalable/places/256)    
 -choose your folder and press open.

So, to use a custom icon for the main menu, you have to place the image file in an appropriate folder of an existing icon theme and enter its name in gconf-editor like described, without its extension, e.g. .png.

---

### Post by lykeion on 2011-01-17
You can also do this with Ubuntu Tweak if you want an easier way.
* Add PPA and install Ubuntu Tweak:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
You'll find it in Applications > System Tools
Ubuntu Tweak > Desktop > GNOME Settings > Click this button to change the menu logo image

---

