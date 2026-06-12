---
title: "How to change Greybird desktop icon font? Xfce4.10"
date: 2013-01-03
forum: Desktop Environments
---

### Post by IDexius on 2013-01-03
Just upgraded to 12.10 and quickly noticed that the icon font is awful against anything that isn't pitch-black. As can be seen from the image it's near impossible to read, how do I change it(without changing away from greybird)?

[http://i.imgur.com/5VQ3b.jpg](http://i.imgur.com/5VQ3b.jpg)

---

### Post by slickymaster on 2013-01-04
You should try to edit the gtkrc-2.0 file into the themes directory.
Go to the terminal and type: 
```
sudo leafpad /usr/share/themes/Greybird/gtk-2.0/gtkrc
```
Find the section (**style "xfdesktop-icon-view"**) and change **font_name parameter**

---

