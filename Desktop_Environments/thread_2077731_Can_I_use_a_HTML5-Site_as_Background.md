---
title: "Can I use a HTML5-Site as Background?"
date: 2012-10-29
forum: Desktop Environments
---

### Post by B3ryJu on 2012-10-29
I just would like to ask if there is a possibility to use a HTML5 File as a Wallpaper, because I have  [this]("https://dl.dropbox.com/u/36727644/projects/nexus/index.html") (not made by me) and I would love to use it as a Wallpaper. 
I user Ubuntu 12.10 with Unity, x64.

---

### Post by Warprunner on 2012-10-29
I can see why!!!! That is awesome!

---

### Post by B3ryJu on 2012-10-29
I just wanted to highlight again that this was not made by me! It was made by @SamusAranX

---

### Post by grahammechanical on 2012-10-29
This is an experiment that you must do for yourself.

Background images on 12.10 are stored in /usr/share/backgrounds/

The script that runs the background image is found at /usr/share/gnome-background-properties/

There you will find three scripts in xml format that can be edited by Gedit if it is launched using

```
gksudo gedit
```

This is what you find in the script called ubuntu-wallpapers.xml

> <wallpapers>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#2c001e</pcolor>
    <scolor>#2c001e</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
</wallpapers>

I guess that you would need to edit the file name line to point to the HTML document that you wish to load.

Be careful. Gedit makes backup copies that become hidden files but are still read by the system and that can cause confusion to the system. You need to stop Gedit from making backup copies.

Another way to try this is to open dconf Editor. It may be in the Dash if you have it installed. Open up the menu tree by clicking com, then canonical, then unity-greeter. At the top you will see the path to the background image file which you can edit.

Regards.

---

### Post by B3ryJu on 2012-10-29
/usr/share/gnome-background-properties
is the path

Edit: Does not work, for whatever reason.

---

