---
title: "Themes Help"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by Fallen2 on 2007-05-09
I just got Ubuntu installed this morning and now I want to install new themes but I read that you need Murrine Engine or something like that.  What do I need to do in order for me to install new themes?

---

### Post by Foxmike on 2007-05-09
You can find some themes at [www.gnome-look.org]("http://www.gnome-look.org"), it is a wonderfull (and quite addictive) web site. 
 
In order to change/install theme, you should already have some installed. You will acces them with the menus: System -> Preferences -> Themes (traducing from french, words migh differ).
 
To install a theme you just downloaded from [www.gnome-look.org]("http://www.gnome-look.org"), just drag'n'drop it into the theme manager, it should work. Now, there is primary 3 themes categories:
- Metacity will change the windows borders and the minimize/maximize/close buttons
- GTK2 will modify colors, the shape of everything inside the windows themselves, as well as the bars you have up and down the screen
- Icons: self descriptive.
 
Now, in order to make some GTK2 themes work, you will have to install the proper engine. If you are not sure which one to install, just install them all then you shouldn't have any problem. To find the GTK engines, go with the menus to: System -> Administration -> Synaptic . Make a search for "GTK+ engine" and install all the packages in wich you see "GTK+ engine" in the name. Note: Synaptic might find you some other packages, just scroll the list, the engines will all be in a bunch.
 
If you just installed a theme, the result is a horrible Windows 95 looking windows, then you don't have the proper engine installed.
 
To make sure that with new themes the theme will follow up when doing administration work (i.e. anything that will pop-up a windows asking you for password), you will have to open a terminal (Applications -> Accessories -> Terminal) and copy/paste the following:
 
```
sudo cp -R ~/.themes/* /usr/share/themes/
```
 
and press enter.  The terminal will ask you for your password, enter it and press enter again.  The command will copy the themes you just installed to a place where they will be available to all users of the computer. 
 
Good lock!:)
 
Regards,
 
-FM

---

### Post by WNDS1701 on 2007-05-10
Hey buddy,


thanks for this very clear and easy HOW-TO. Why don't you guys make official how-to's for some of the "standard questions" that arise often? Wouldn't this cut off many questions?


Have fun!

---

### Post by kpolice on 2007-05-10
No offense but that's why the search on the forum exists.

---

### Post by WNDS1701 on 2007-05-10
This is not offending at all, you are right (and I found this thread this way) but many questions are posted several times and the quality of the answers differs from time to time. I think that such stuff could be answered in how-to's to which you only have to refer with a link then.

Sometimes a guy may type in the wrong search words and does not find the thread. If there are 10 how to's for the major themes, he will find them more easily.

Perhaps this is just a stupid thought of a stupid mind. I hope that it's not but it's on others to judge about that. ;-)

Have fun!

---

