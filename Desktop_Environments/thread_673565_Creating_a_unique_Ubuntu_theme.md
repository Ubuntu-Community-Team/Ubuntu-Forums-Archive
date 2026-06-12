---
title: "Creating a unique Ubuntu theme?"
date: 2008-01-20
forum: Desktop Environments
---

### Post by TristanS on 2008-01-20
Hello again

I am quite experienced with Photoshop / visual design and was really wanting to make my own theme for Ubuntu. (and might release it if you ask nicely :))

The real question is, is the a folder where all the parts of the Ubuntu theme are stored? like the scroll bar backgrounds, buttons etc, so that I can use them / change them in PS and then replace the originals making an awesome new theme?

Or am I just talking *crap* and its much harder than this? 

Thanks, and sorry if this question has been asked already...

---

### Post by banewman on 2008-01-20
Here's a how to -
[http://www.gnome.org/learn/admin-guide/2.2/ch03s05.html](http://www.gnome.org/learn/admin-guide/2.2/ch03s05.html)
:)

---

### Post by imtheguru on 2008-01-20
> is the a folder where all the parts of the Ubuntu theme are stored? like the scroll bar backgrounds, buttons etc, so that I can use them / change them in PS and then replace the originals making an awesome new theme?Not exactly, no.

The fastest and cleanest themes such as Industrial, Clearlooks and such do not use images. They employ GTK+ code to create the various window widgets. So study the themes to observe how they achieve their looks.

Topics of interest are Gnome2, GTK+, Metacity and Gnome Icons.

Official documentation and tutorials can be found on the Gnome developer website.
[http://developer.gnome.org/doc/](http://developer.gnome.org/doc/)
[http://developer.gnome.org/doc/tutorials/](http://developer.gnome.org/doc/tutorials/)

Cheers.

---

### Post by TristanS on 2008-01-20
Ok, I kind of understand. So this is what I have.


> The fastest and cleanest themes such as Industrial, Clearlooks and such do not use images. They employ GTK+ code to create the various window widgets.

I have taken the folder "Glossy" out of the file system and copied it into my .themes folder in my home directory, and would now like just to change the colors of the window title bars, buttons and so forth. Im guessing I have to edit the file "gtkrc" and edit the HEX color values inside of it to achieve this correct?

Thanks,
Tristan

---

### Post by TristanS on 2008-01-21
bump.

I have tried to change one or more hex values, but dont seem to be going anywhere? Anyone got any ideas? Or does the glossy theme run off pixmaps instead of code?

Thanks!
Tristan

---

### Post by mcduck on 2008-01-21
> **TristanS said:**
> bump.

I have tried to change one or more hex values, but dont seem to be going anywhere? Anyone got any ideas? Or does the glossy theme run off pixmaps instead of code?

Thanks!
Tristan

You'll have to save the file and reload the theme in Gnome's theme manager to see any changes.

The Widget Factory is useful tool when doing themes, it shows a window with lots of different buttons and stuff an allows you to change the theme it's using. So it makes it easier to see what you are doing. Just install the 'thewidgetfactory'-package (or run 'sudo apt-get install thewidgetfactory') and then start it by running 'twf'.

By the way, it's also possible to use pixmaps in themes, and also you can mix pixmaps and other theme engines to create more varied themes. The easiest way would be to find a pixmaps based theme and start changing the pictures.

---

