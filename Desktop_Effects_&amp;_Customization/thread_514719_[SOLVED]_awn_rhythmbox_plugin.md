---
title: "[SOLVED] awn rhythmbox plugin"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by bash4fun on 2007-08-01
hey guys
does anyone of you know how
to get the rhythmbox plugin for awn working?
i downoloaded the files and copied them into the plugin
directory of rhythmbox in my home folder

howerver, when trying to activate it in rhythmbox
i get an error message stating that rhythmbox is not
able to activate the plugin

do i have to complete any other tasks than just
copying the files into the plugin folder :confused:

please help me
thx in advice

---

### Post by bash4fun on 2007-08-07
i finally got it working...

---

### Post by omriasta on 2007-08-10
do you care to share how you got it working?

---

### Post by bash4fun on 2007-08-11
so here's the solution how i got that thing working:

1) firstly i downloaded all necessary files from [http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/]("http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/")

2) then i created a folder named "plugins" in "/home/user/.gnome2/rhythmbox/"

3) as you had to download the files one by one you will have to ensure that there again exists a folder named "artdisplay-awn", in which you copy all the .py and .pyo files.

4) copy this "artdisplay-awn" folder into the "plugins" directory we created before and also copy the "artdisplay-awn.rb-plugin" file into this directory

5) finally start "rhythmbox" and enable the awn-plugins in the plugins menu

6) as for me the "awn-menus" plugin doesn't work, i left it out. but if you want to try it make it working you can also copy the downloadable files into the plugins directory.

hope this guide helps you guys.
greetings

---

### Post by guitarboy1016 on 2007-09-12
Wow!  This finally works.  Thanks for coming back and telling us how you did it!

Ben <><

---

