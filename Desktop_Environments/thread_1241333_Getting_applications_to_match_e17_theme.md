---
title: "Getting applications to match e17 theme?"
date: 2009-08-15
forum: Desktop Environments
---

### Post by surfreak on 2009-08-15
So I've downloaded and installed the super-slick e17 over my base Xubuntu install, and just recently got the "Grunge" theme. Only thing is, when I start applications like banshee, transmission, etc., they open in the "standard grey windows" (screenshots attached). I'd like to get them to be more cohesive with the rest of the theme. 

I've found a pretty cool theme/skin for Firefox that fits well with the "Grunge" theme ("Old Factory Black"), but I'm at a loss for what to do for my other apps. Suggestions?

---

### Post by VCoolio on 2009-08-16
In ubuntu I need to run gnome-settings-daemon to have the same theme settings as in gnome. I guess you'll need to find the xfce-equivalent for this (is there something like xfce/xfce4-settings-daemon?. In gnome you could also make a .gtkrc file in your home folder where you specify (icon-)theme. It looks like this:

gtk-theme-name="Clearlooks"
gtk-icon-theme-name="gnome-human"
gtk-font-name="Sans 10"
gtk-toolbar-style=2
include "/home/username/.gtkrc-2.0.mine" # in this file you can have specific theme settings

Don't know how this works with xubuntu but you'll get the idea.

---

### Post by gjoellee on 2009-08-16
That is not possible beause E17 does not use GTK. You can however try to find a GTK theme that matches or looks good with the E17 theme you're using.

An easy way to manage icons and gtk themes in E17 is to use lxappearance. Install it with this command:
```
sudo apt-get install lxappearance
```

then run 

```
lxappearance
```
in either the terminal or in a run dialog which you can open by hitting Alt + F2.

To theme sudo applications (like Synaptic) you might have to run ```
sudo lxappearance
```

You can install more gtk themes and icons by downloading them and extracting them to ./themes and ./icons (located as a hidden file in your home folder). You can show hidden files by pressing Ctrl + H, or Alt + . if you use Dolphin.

The themes you install to ./themes, the icons you install to ./icons and the fonts you install to ./fonts may not work appear for sudo applications. There is a quick howto fix on the following link: [http://kshoster.net/?q=tutorials/ubuntu/themegnomeroot](http://kshoster.net/?q=tutorials/ubuntu/themegnomeroot)

---

