---
title: "Mouse cursor changes only in active windows"
date: 2015-08-23
forum: Desktop Environments
---

### Post by bisherbas on 2015-08-23
Running Xubuntu 14.04.3 and have been experiencing this problem that has been occurring since 8 years!

[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/157447](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/157447)

I have already tried every single workaround mentioned I could find online. Modifying the /default/index.theme, editing .gtkrc-2.0 file with the cursor name, copying the theme from ~/.icons to /usr/share etc etc etc

None worked so far!

This is the theme I am trying to install: [http://xfce-look.org/content/show.php/PixelFun3?content=168338](http://xfce-look.org/content/show.php/PixelFun3?content=168338)

For example it works fine all right inside the terminal window, chromium window, and even the Notes gadget on desktop but it does NOT work on desktop, file manager, login screen etc. AND IT DOES NOT WORK WHEN THE CURSOR IS ON THE WINDOW TITLE BAR! Even when it works over the content of the window it still does not work when I move the cursor over to the title bar. Strange....

Please help. Thanks!

---

### Post by CantankRus on 2015-08-24
The reason your previous attempts may have failed is the theme's folder name does not match the name in 
the cursor.theme file of your linked theme.  
[ATTACH=CONFIG]264022[/ATTACH]

This should work making sure the downloaded **168338-pixelfun3.tar.gz** archive is in **~/Downloads**

Using terminal, change directory to ~/Downloads...
```
cd ~/Downloads
```

Extract the archive.... 
```
tar -xzvf 168338-pixelfun3.tar.gz
```

Move and rename the pixelfun3 folder to /usr/share/icons/pixelfun
```
sudo mv pixelfun3 /usr/share/icons/pixelfun
```

Run these commands one at a time to install and set your cursor in alternatives....
```
CURSOR=pixelfun

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

Although you don't need to in xfce, it won't hurt to also run this command for other DEs.
```
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
```

Use the xfce mouse and touchpad settings to select your cursor theme.
Log out to complete the change.

---

### Post by bisherbas on 2015-08-24
Thank you so much! This is the most elaborate instructions on installing the mouse cursor I have ever seen.

Good catch on the theme folder name. I wasn't paying attention to it. Theme's maker responded with an alternative solution that works fine too. Here: [http://gnome-look.org/content/show.php?content=168338#c478134](http://gnome-look.org/content/show.php?content=168338#c478134)

But obviously the way you are explaining makes perfect sense to me.

---

### Post by bisherbas on 2015-08-24
> **CantankRus said:**
> The reason your previous attempts may have failed is the theme's folder name does not match the name in 
the cursor.theme file of your linked theme.  
[ATTACH=CONFIG]264022[/ATTACH]

This should work making sure the downloaded **168338-pixelfun3.tar.gz** archive is in **~/Downloads**

Using terminal, change directory to ~/Downloads...
```
cd ~/Downloads
```

Extract the archive.... 
```
tar -xzvf 168338-pixelfun3.tar.gz
```

Move and rename the pixelfun3 folder to /usr/share/icons/pixelfun
```
sudo mv pixelfun3 /usr/share/icons/pixelfun
```

Run these commands one at a time to install and set your cursor in alternatives....
```
CURSOR=pixelfun

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

Although you don't need to in xfce, it won't hurt to also run this command for other DEs.
```
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
```

Use the xfce mouse and touchpad settings to select your cursor theme.
Log out to complete the change.

Do you mind explaining how to change the cursor size too? User interface does not seem to have any influence over the cursor size of the custom theme. Default themes change just fine though.

---

### Post by Dennis N on 2015-08-24
> Do you mind explaining how to change the cursor size too? User interface does not seem to have any influence over the cursor size of the custom theme.
Explained here, but with resizable cursors is not possible to have a uniform size (larger than default) with Xubuntu unless you use 15.04 or later.
[http://ubuntuforums.org/showthread.php?t=2232013&p=13290196#post13290196](http://ubuntuforums.org/showthread.php?t=2232013&p=13290196#post13290196)

Note: Not all cursors support multiple sizes.

---

### Post by CantankRus on 2015-08-25
You can increase cursor size by using a theme made with just the one large pixel size.
Instructions [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2278591&p=13291206#post13291206") including a DMZ-White-Medium(32px) download.
Only difference is in xfce you don't need to run the gsettings command. 
You select the cursor theme in mouse settings as a last step. (edits ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml) 

More custom themes of 1 larger size [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12735911#post12735911").
My fav is DMZ-Black-Medium(32px)

---

