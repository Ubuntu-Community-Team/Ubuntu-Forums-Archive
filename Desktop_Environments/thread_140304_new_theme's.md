---
title: "new theme's"
date: 2006-03-05
forum: Desktop Environments
---

### Post by kc8pdr on 2006-03-05
Where and how do i install new theme's ?

---

### Post by Strangerdave on 2006-03-05
What are you using gnome or KDE?

If you search the site you can easily find the answer to the question on installation.

Try gnome-look.org
and KDE-look.org

for different themes.

-SD-

---

### Post by aysiu on 2006-03-06
KDE themes can be difficult to install. Just a heads-up.
Gnome themes are a lot easier to install.

---

### Post by Princey on 2006-03-06
[QUOTE=aysiu]KDE themes can be difficult to install. Just a heads-up.
Gnome themes are a lot easier to install.[/QUOTE]

Pretty much so. I've been fighting for the past hour trying to install some themes from kdelook.org and haven't gone past error messages when I follow the advice on how to install. Most requires me to compile, after issuing the first command, I get an error message saying no gtk or c compilers are installed when they really are installed on the system.

---

### Post by Xian on 2006-03-06
[QUOTE=kc8pdr]Where and how do i install new theme's ?[/QUOTE]

The gnome-theme-manager has an install mechanism but I never use it (yeah, I know that shocks everyone). I just place (unpack if required) the theme in my /home/<username>/.themes folder and then goto 'Theme Details' in the theme manager to apply the individual portions as desired (controls, window border, etc.), and then save it in the main window using a name of my choosing.

---

### Post by f1dave on 2006-03-06
[QUOTE=aysiu]KDE themes can be difficult to install. Just a heads-up.
Gnome themes are a lot easier to install.[/QUOTE]

It is however getting easier these days. theme-manager themes include all icons, styles, window decorations, etc and are a snap to install. Styles, WinDecs, etc individually are a bit harder- generally you'll need to do 
```

./configure
make
sudo make install
```

Or some such. For window decorations, I recommend dekorator. Get it from KDE-look, its easy to install window decorations using that.

---

### Post by chavo on 2006-03-07
Hi I answered this question yesterday over here [http://www.ubuntuforums.org/showthread.php?t=140271](http://www.ubuntuforums.org/showthread.php?t=140271).

I'll quote it here.  It's a steep by step rundown of installing kde-themes for newbies :)

> KDE or QT styles are actually plugins and they need to be compiled. If you can't find a deb then you need to compile it. 
 Compiling kde-styles is easy, you just need to get a compiler and some basic development files.
 
 sudo apt-get install build-essential
 sudo apt-get build-dep kdebase
 
 Those two commands should get you a working environment.
 Now decompress the archive and cd into the new directory.
 Now run this ->
 
 ./configure --prefix /usr
 make
 sudo make install
 
 The procedure is the same for kwin decorations.


I'll be happy to assist anyone if they have further problems. But it really should be as easy as the stepsa above.

---

### Post by Princey on 2006-03-07
Thanks Chavo...Things look better now.

---

### Post by Princey on 2006-03-08
[QUOTE=chavo]Hi I answered this question yesterday over here [http://www.ubuntuforums.org/showthread.php?t=140271](http://www.ubuntuforums.org/showthread.php?t=140271).

I'll quote it here.  It's a steep by step rundown of installing kde-themes for newbies :)



I'll be happy to assist anyone if they have further problems. But it really should be as easy as the stepsa above.[/QUOTE]


I take it to mean that when they're compiled they're in deb format, right? I found some cool themes in deb format but when I use theme manager to install them it says that it's not a valid theme archive. When I use sudo dpkg -i to install the deb file, things run and and I'm told that the them is set up but I can't seem to find them in system preferences or in theme manager. Any advise?

---

### Post by f1dave on 2006-03-08
[QUOTE=Princey]When I use sudo dpkg -i to install the deb file, things run and and I'm told that the them is set up but I can't seem to find them in system preferences or in theme manager. Any advise?[/QUOTE]

I think here would be a good time to define what kde means by themes, etc.
Window Decorations- The bar at the top of each window with your buttons and caption
Styles- The widget style of your windows- what buttons look like, bars, checkboxes, etc.
Colour Schemes- Pretty self explanatory.
Background- Again, self explanatory.
Font- Ditto.
Icons- The icon theme installed on your system
Screen saver- Self explanatory.
Theme manager themes- Right. These themes are the key here- they are simply a file that contains a combination of the above items. So one theme might contain the following- Plastik window decoration, Phase style, Nuvola icon set... etc.

The debs you are trying to install will likely be styles or window decorations. Some, like baghira, are a little more complex and try to skin your whole system. However the basic setup is still the same. The theme manager only deals with theme manager themes, which are in a .kth format. As far as i understand, for a .kth file to work properly, the components of it have to be already installed. For instance, if you dont have the Klearlook style installed (usually by .deb or .configure/make/make install), then the .kth file will not function properly.

I hope this explains things well, and that someone corrects me if i'm wrong somewhere.

---

### Post by Princey on 2006-03-08
Thanks Dave, I think I better understand now. Guess I was looking for the windows theme experience when I installed. I'll take note of that and not pull the threads off my head

---

