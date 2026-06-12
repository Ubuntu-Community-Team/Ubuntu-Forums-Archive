---
title: "New to Ubuntu, have some questions"
date: 2009-05-18
forum: General Help
---

### Post by Soul Undead on 2009-05-18
Well, I am new to these forums and new to ubuntu overall, not knowing a single thing to do as an experienced WinXP user. I've only used Ubuntu once before at version 8.10. My Current version is 9.04, and it seems promising so far. What I want to know is:

1. How do I easily install themes?
2. Is Ubuntu as customizable as Windows XP?
3. How are directories... you know... stated?

---

### Post by geirha on 2009-05-18
1. System -> Preferences -> Appearance. Drag and drop an archive (.tar.gz) containing a gtk2/metacity theme (You find lots of them at [http://gnome-look.org](http://gnome-look.org)) into the appearance properties window (on the Themes tab).
2. What type of customizations?
3. stated? I don't understand what you mean. Ubuntu adheres to [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) if that's what you mean.

---

### Post by dhughes on 2009-05-18
> **Soul Undead said:**
> Well, I am new to these forums and new to ubuntu overall, not knowing a single thing to do as an experienced WinXP user. I've only used Ubuntu once before at version 8.10. My Current version is 9.04, and it seems promising so far. What I want to know is:

1. How do I easily install themes?
2. Is Ubuntu as customizable as Windows XP?
3. How are directories... you know... stated?

1. System>Preferences>Appearance>Theme [tab] choose the (Metacity) theme, you can also download themes from such places as gnome-look.org


2. I'd say much, much more

3. This?: [http://kythuatmaytinh.files.wordpress.com/2008/09/linux_file_structure.jpg](http://kythuatmaytinh.files.wordpress.com/2008/09/linux_file_structure.jpg)

---

### Post by Maverick7687 on 2009-05-19
> **geirha said:**
> 1. System -> Preferences -> Appearance. Drag and drop an archive (.tar.gz) containing a gtk2/metacity theme (You find lots of them at [http://gnome-look.org](http://gnome-look.org)) into the appearance properties window (on the Themes tab).
2. What type of customizations?
3. stated? I don't understand what you mean. Ubuntu adheres to [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) if that's what you mean.
I'm just getting started at this as well. I tried this method of installing the Broken Vista theme and it said it is not a valid theme file.

---

### Post by skygazer on 2009-05-19
> **Soul Undead said:**
> 
1. How do I easily install themes?
2. Is Ubuntu as customizable as Windows XP?
3. How are directories... you know... stated?

1.you need to look at the gnome-look tutorial which will help u understand abt metacity,compiz,gtk and all similar jargon used for ubuntu customization. Once u understand, u can figure out how to exactly install and use themes.

2.Ubuntu is far more customizable than XP. I have never come across anything that you cant change, be it your splash screen, themes or music player. Most of your answers will be right here on this forum, for others , u need to spare few minutes of your time and run a web search

3.Not quite sure what you are asking, but  directory navigation is just like windows except that you wont find any C:/ D: drives. You need to goto the /home/USERNAME directory for your data and /rest of the folders for your programs, OS etc

---

### Post by skygazer on 2009-05-19
> **Maverick7687 said:**
> I'm just getting started at this as well. I tried this method of installing the Broken Vista theme and it said it is not a valid theme file.
are you sure its a Metacity/GTK theme and not a GDM theme..?

---

### Post by geirha on 2009-05-19
> **Maverick7687 said:**
> I'm just getting started at this as well. I tried this method of installing the Broken Vista theme and it said it is not a valid theme file.

This one?
[http://gnome-look.org/content/show.php/Broken+Vista+Gtk+Theme?content=101853](http://gnome-look.org/content/show.php/Broken+Vista+Gtk+Theme?content=101853)

I tried it. Clicked the download link and it downloaded the file 101853-Vista.tar.gz to the Desktop. Opened System -> Preferences -> Apperance,  dragged that file over there and got a message that it got installed correctly. I could then select that theme from the list.

---

### Post by Maverick7687 on 2009-05-19
> **geirha said:**
> This one?
[http://gnome-look.org/content/show.php/Broken+Vista+Gtk+Theme?content=101853](http://gnome-look.org/content/show.php/Broken+Vista+Gtk+Theme?content=101853)

I tried it. Clicked the download link and it downloaded the file 101853-Vista.tar.gz to the Desktop. Opened System -> Preferences -> Apperance,  dragged that file over there and got a message that it got installed correctly. I could then select that theme from the list.
That one worked but wasn't the one I was looking at.
[http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049](http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049) 
That is the one I was looking at that wouldn't install. 
The one from your link said it also needed something else to make it look right.

---

### Post by UbuntuNerd on 2009-05-19
try the themes from this [guide](http://my.opera.com/ubuntunerd1/blog/make-ubuntu-look-like-windows-vista)

---

### Post by geirha on 2009-05-19
> **Maverick7687 said:**
> That one worked but wasn't the one I was looking at.
[http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049](http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049) 
That is the one I was looking at that wouldn't install.


That's a GDM theme. GDM is the login screen, so that theme only changes the appearance of the login screen. To install that theme, go to System -> Administration -> Login screen -> [Local] tab, then drag and drop broken_vista.tar.gz over to the list of themes.

> **Maverick7687 said:**
> 
The one from your link said it also needed something else to make it look right.

You mean the part that says you need the ubuntulooks theme?
> For a correct visualization of the theme you MUST have this theme installed to work:
[http://www.gnome-look.org/content/show.php/Ubuntulooks+Engine?content=43255](http://www.gnome-look.org/content/show.php/Ubuntulooks+Engine?content=43255)

The Ubuntulooks theme is installed by default in Ubuntu, so you only need to worry about that if you're not running Ubuntu.

---

### Post by Maverick7687 on 2009-05-20
> **geirha said:**
> That's a GDM theme. GDM is the login screen, so that theme only changes the appearance of the login screen. To install that theme, go to System -> Administration -> Login screen -> [Local] tab, then drag and drop broken_vista.tar.gz over to the list of themes.



You mean the part that says you need the ubuntulooks theme?


The Ubuntulooks theme is installed by default in Ubuntu, so you only need to worry about that if you're not running Ubuntu.
This clears things up nicely. Thanks a lot. Also, yes, the ubuntulooks message is the one I am getting. Strange that it would still show the warning even though it is installed by default.  Just jumping into this OS so I am still very much a newb here.. Thanks

---

### Post by Josh81 on 2009-05-20
Is it as customisable as windows? ITS 500 X MORE CUSTOMISABLE THAN WINDOWS :D



oh and good themes will have readmes saying how to install them, some themes you can just drag and drop into your theme manager, some you have to edit your icons and stuff

---

