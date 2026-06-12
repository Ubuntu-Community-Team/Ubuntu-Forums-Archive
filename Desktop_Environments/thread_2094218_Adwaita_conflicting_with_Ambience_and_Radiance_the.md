---
title: "Adwaita conflicting with Ambience and Radiance themes"
date: 2012-12-13
forum: Desktop Environments
---

### Post by rdettogni on 2012-12-13
Hi,

After installing Gnome Shell and Gnome-Environment from the software central in Ubuntu 12.10 my Ambience and Radiance themes got corrupted.

The problem is now the default theme is Adwaita (in the tweak-gnome-tool) is tells me that Adwait is the default and before was Ambiance. And because of this when I select the theme Ambiance some components of Adwaita persists, specialy top bar windows schemes when widows are not selected (are in the second plane).


Does anyone know how to set Ambience as the default theme again or completly remove Adwaita from Ubuntu 12.10. I deleted the folder from the usr/share/theme directory but Adwaita is still the defaukt theme and are causing problems, 

Thanks in advance!

---

### Post by figure002 on 2013-03-01
Thank you rdettogni, for thanks to your question I was able to find the solution. I was having the same problem after trying out Gnome Shell on Ubuntu 12.10. After reading your post, I looked at the contents of the file `~/.gtkrc-2.0`. The contents of this file looked as follows:

```
# -- THEME AUTO-WRITTEN BY gtk-theme-switch2 DO NOT EDIT
include "/usr/share/themes/Adwaita/gtk-2.0/gtkrc"
include "/home/serrano/.gtkrc-2.0.mine"
# -- THEME AUTO-WRITTEN BY gtk-theme-switch2 DO NOT EDIT
```

Which explains the problem. You can see that it loads a theme file for the Adwaita theme. You can simply remove the line that reads ```
include "/usr/share/themes/Adwaita/gtk-2.0/gtkrc"
``` to solve this problem. As an alternative, you can simply use that tool `gtk-theme-switch2` to change the theme back to Ambiance. If you don't already have it installed:

    ```
sudo apt-get install gtk-theme-switch
```

Then execute the tool from the terminal:

```
gtk-theme-switch2
```

Select Ambiance from the dropdown menu and press the Apply button. And all should be fixed (you may need to restart some applications to see the changes).

---

### Post by Frogs Hair on 2013-03-01
Adwaita is the default theme for the Gnome Shell and the ambiance & radiance themes are Ubuntu defaults. The panel in the Gnome Shell has its own theme  works completely different than in Unity and Gnome Classic.   

Log-out and log-in or use Alt + F2  ```
r 
``` to restart the shell after changing the theme. If you want a Gnome Shell theme that looks like ambiance you will have to install one. 12.04 uses Gnome 3.4 themes and 12.10 uses 3.6 themes. 
 
 [http://browse.deviantart.com/art/GNOME-Shell-Ubuntu-Ambiance-210264151](http://browse.deviantart.com/art/GNOME-Shell-Ubuntu-Ambiance-210264151)

More shell themes:[http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=d87c3b54e28be23112506fe39ba85b8d](http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=d87c3b54e28be23112506fe39ba85b8d)

---

### Post by figure002 on 2013-03-01
@Frogs Hair: I think you misunderstood the thread starter's question. The problem is that Ubuntu's own themes get corrupted after installing Gnome Shell (that's when you're using Unity/Gnome Classic).

---

### Post by Frogs Hair on 2013-03-01
> **figure002 said:**
> @Frogs Hair: I think you misunderstood the thread starter's question. The problem is that Ubuntu's own themes get corrupted after installing Gnome Shell (that's when you're using Unity/Gnome Classic).

I did misunderstand . I thought Ambiance /Radiance were not displaying properly in the shell. Try the following and log out and in.  

```
 sudo apt-get install --reinstall light-themes
```

---

