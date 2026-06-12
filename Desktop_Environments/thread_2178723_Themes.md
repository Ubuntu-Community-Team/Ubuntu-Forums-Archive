---
title: "Themes"
date: 2013-10-04
forum: Desktop Environments
---

### Post by jgw on 2013-10-04
I am looking for a theme which can provide the following:
large, visible cursor
actually displays what is one the desktop, including the top line (holds program stuff like file, view, edit, etc. as well as network hookup, etc.

I have run through several themes and strange things happen.  unity choices turn into spaces, network goes black, file, view, edit, etc. goes away until cursor hits them, etc.  I keep thinking there is one that will actually display everything but, for some reason, I have not been able to find it.

The above lists what I really need.  In addition it would be nice if there was a them which gave a larger view for those of us working with screens which are not on a desk but, rather, further away.  I think a magnification option exists but have no idea how to get there/

Thank you................

---

### Post by stinkeye on 2013-10-04
What your looking for isn't provided by a theme.

Change the cursor size.....see [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12473313&viewfull=1#post12473313")


Disable Menu in panel completely(terminal command)
```
echo '[ "$DESKTOP_SESSION" = "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
Log out/in

If you want to enable the global menu again...
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```



For a larger view, change the text scaling factor(terminal command)
```
gsettings set org.gnome.desktop.interface text-scaling-factor [COLOR="#FF8C00"]**x.x**[/COLOR]
```
...where [COLOR="#FF8C00"]**x.x**[/COLOR] is a number between 1.0 and 3.0
eg
```
gsettings set org.gnome.desktop.interface text-scaling-factor [COLOR="#FF8C00"]**1.5**[/COLOR]
```

To reset text-scaling-factor back to default, use(terminal command)...
```
gsettings reset org.gnome.desktop.interface text-scaling-factor
```

---

### Post by jgw on 2013-10-05
Wow!  Thanks for the reply!

I will try this and see what happens.

Thanks again!

---

### Post by grahammechanical on 2013-10-05
There will also be problems if you are choosing themes built with GTK2 toolkit as Gnome (and hence Ubuntu) now requires themes built with the GTK3 toolkit. This is the case ever since Gnome moved from Gnome 2 to Gnome 3.

Regards.

---

