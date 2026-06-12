---
title: "Can't select Gnome Shell theme"
date: 2012-03-18
forum: Desktop Environments
---

### Post by d3ngar on 2012-03-18
Hi,

I think there are various gnome-shell themes available and I also installed my own ([Boomerang by ghogaru]("http://ghogaru.deviantart.com/art/Boomerang-189180645")).

Sadly I can't seem to be able to select them in the gnome-tweak-tool.

There is a little exclamation mark next to the Shell Theme selector. I attach a screenshot,

Thanks for your assistance.

Chris

---

### Post by Frogs Hair on 2012-03-18
Only the Cursor Themes - Window Themes are available in Unity . The shell themes are for the Gnome shell.

If you are using the shell make sure you have installed in the correct location or try to logout and back in .

---

### Post by cortman on 2012-03-18
Also be sure you enabled the User Themes extension, under the Shell Extensions tab in Gnome-tweak.

---

### Post by TheForkOfJustice on 2012-03-19
Went here to install gnome-tweak-tool:

[http://www.noobslab.com/2012/01/malys-revolt2-theme-for-ubuntu_15.html](http://www.noobslab.com/2012/01/malys-revolt2-theme-for-ubuntu_15.html)

Followed instructions.  Got this error when I typed make:

> 
Making all in extensions
make[1]: Entering directory `/home/mackinal/gnome-shell-extensions/extensions'
Making all in user-theme
make[2]: Entering directory `/home/mackinal/gnome-shell-extensions/extensions/user-theme'
Makefile:441: *** missing separator.  Stop.
make[2]: Leaving directory `/home/mackinal/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mackinal/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1


What's the problem and how do I fix?

There is no 'shell extensions' category in my tweak tool without it.

---

### Post by cortman on 2012-03-20
> **TheForkOfJustice said:**
> Went here to install gnome-tweak-tool:

[http://www.noobslab.com/2012/01/malys-revolt2-theme-for-ubuntu_15.html](http://www.noobslab.com/2012/01/malys-revolt2-theme-for-ubuntu_15.html)

Followed instructions.  Got this error when I typed make:



What's the problem and how do I fix?

There is no 'shell extensions' category in my tweak tool without it.

Hi,

I'd recommend starting your own thread for your problem. But follow instructions [here]("http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html") to install shell extensions. Webupd8 is a reliable site.

---

### Post by d3ngar on 2012-03-25
> **cortman said:**
> Also be sure you enabled the User Themes extension, under the Shell Extensions tab in Gnome-tweak.
Yes, thank you. That solved something. Sadly I still can't select the theme I installed. Wondering if I have it in the right folder?

---

### Post by Frogs Hair on 2012-03-25
There are two places themes or icons can be installed. One is the .themes and .icons folders in home/hidden folders . You will have to create these folders in 11,10. Open the file browser and press Crtl + h and create the folders and place your downloaded extracted folders there. The . prior to the name will hide them.

The second place is file system > usr/share/themes or icons. These folders already exist in the file system. Open the file browser from the terminal using```
gksudo nautilus
``` This will give you permission to add items to the file system.

Check all folders after extraction to make sure there are no packages inside that need extracting . 

If you would like to install themes with a PPA so you don't have to update them by hand and move the files there are some below. Look them up to see if you like them. 
```
sudo add-apt-repository ppa:webupd8team/themes
``` 
```
sudo apt-get update
``` 

_Enter these on at a time_ 
```
sudo apt-get install elegant-brit-gtk-theme
sudo apt-get install evolve-gtk-theme
sudo apt-get install gnomishdark-theme
sudo apt-get install zukitwo-colors-theme

```

---

