---
title: "missing taskbar"
date: 2008-04-25
forum: Desktop Environments
---

### Post by ressaw on 2008-04-25
Hi, I'm a total noob at using linux and after a successful installation of Ubuntu, I installed VLC packages and to free resources I uninstalled Totem. 

The thing is that suddenly my taskbar (the upper bar and the one from below too) disappeared and I can't make them appear again, even if I restart the system it's still missing. 

In any case, to some extent the computer is usable, the icons that I had on my desktop allow me to access some programs and some of my files, but that's it, does anyone know how can I fix this?


PS> if it involves using the command lines, please explain easily cause I'm very new at using it :P thanks!

---

### Post by gjwolfswinkel on 2008-05-04
same problem here, also after installing stuff. No solution yet.

---

### Post by TheMemphisExperience on 2008-05-04
I was trying to find a way to create new panels, but no joy.

However, you might have some luck if you create a new user account. 

Hit alt+F2 to open a magic run application dialogue. Input users-admin and hit run. You can create a new user to login to with this. Ideally, they will have panels. If so, migrate your files into this new directory or leave them in your other user profile. If you leave them there, you can cripple the second profile so it is only usable as a storage area. 

Alternatively, a clean install after salvaging your data should clear up the problem.

---

### Post by juje on 2008-05-05
hey! same problem here...the thing is that i was pimping up my newly installe hardy heron and had some problems with the screen resolution with the nvidia-settings package, meanwhile i was installing some other packages (i don't quite remember which one, but they had nothing to do with desktop settings nor screen)...to solve this screen resolutions i use the nvidia-settings package...it all went find until i restart my pc...when i found i've lost my taskbars (both of them) and the screen resoution all mixed up...any clue how to restore them?

---

### Post by juje on 2008-05-05
ok...i've found a solution for my little problem...the thing is that i must have done something (or the nvidia installing process did it) and uninstalled the gnome panel...so i installed back again with this command

apt-get install gnome-panel

---

### Post by hariprs on 2008-05-05
Same thing happened for me also after installing and uninstalling some packages. I don't remember exactly what are all those packages. But I remember i uninstalled firefox completely and reinstalled it and installed new beta driver for my nvidia card.

To solve this I created a new login and copied all the files from the old login to the new login and changed the permission. Now everything seems ok.

---

### Post by houldsworth1 on 2010-08-21
Try this if it happens again:

Press Alt+F2, in text fild type 'gnome-terminal' (without quots) and click on 'Run'.

In terminal submit the commands below one by one. Select one line at a time and press 'Enter'.

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by jimbop99 on 2010-08-21
Where'd you pull up this old thread from?

---

### Post by houldsworth1 on 2010-08-22
> **jimbop99 said:**
> Where'd you pull up this old thread from?

Simple answer - this answer was higher on Google search than the one that actually provided a solution.  So I moved it here to help  people in the future.  

I should, however, give credit where due, so here is the original post:

[http://netgator.blogspot.com/2010/06/taskbar-missing-in-ubuntu-1004.html](http://netgator.blogspot.com/2010/06/taskbar-missing-in-ubuntu-1004.html)

---

### Post by JigglyWiggly_ on 2011-12-20
> **houldsworth1 said:**
> Try this if it happens again:

Press Alt+F2, in text fild type 'gnome-terminal' (without quots) and click on 'Run'.

In terminal submit the commands below one by one. Select one line at a time and press 'Enter'.

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
Ressurecting this, but thank you very much.

---

