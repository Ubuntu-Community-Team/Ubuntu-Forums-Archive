---
title: "Making xubuntu menu's like gnome"
date: 2007-10-03
forum: Desktop Environments
---

### Post by Phelan on 2007-10-03
I know i'll probably get flamed, beatin' and hated on, but it doesn't seem to be a lot of that in this forum so i'll ask just for the simple fact that XFCE runs so, so, so much faster so me than gnome on my sub-par old-pos hp dv1000 laptop that I can justify running it.

I like gnome a lot, trying to like xfce, but i don't like the menu system.  Trying to get used to the right click menu on the desktop.  Here is my question, I would like to make the menu structure like it is in gnome, Applications > Places > System, setup EXACTLY like gnome.  Is that possible?  Would I be able to maintain the same stock xubuntu right click menu as well?

If that's not possible, can anyone tell me how to rename where it says "applications".  I had seen somebody said they renamed theirs to "start", I dont want "start" but something better than "applications" would be nice.  It'd be nice to be able to change the icon too, if that's possible.

I've looked around for xfce gui tweaks and any other speed/performance tweaks and I cant find anything specific to xfce that I havn't already done to regular ubuntu.

Trying to get myself situated to just use xubuntu only.  I have an error message that comes up that I will make a post about later today when I get up if I can get some sort of answers from you guys on this post and the icon transparency post.

Thanks!!!!! :p:D:-D8)\\:D/:tongue::biggrin:

---

### Post by Steveway on 2007-10-03
There is a plugin for XFCE's Panel that lets you use items from the Gnome-panel.
You can use that to put your Gnome-menu on your XFCE-panel.

---

### Post by Phelan on 2007-10-03
Did a search on here and on google, I can't find it.  Can you give me a link? :D

---

### Post by jim_p on 2007-10-03
I think its.. impossible to do the "Applications - Places - System" (3 different menus) set in xfce unless you add 3 different menus and alter them to your preferences.

I would suggest installing USP (ubuntu system panel) applet but its not the same

---

### Post by Steveway on 2007-10-03
Found it!
It's called the:
xfce4-xfapplet-plugin

---

### Post by Gremlinzzz on 2007-10-03
right click applications you will see a icon window where you can change name and a browse folder where you can change icon. im using this one.




[http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570](http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570)

---

### Post by Gremlinzzz on 2007-10-03
> **Gremlinzzz said:**
> right click applications you will see a icon window where you can change name and a browse folder where you can change icon. im using this one.




[http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570](http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570)

after right clicking applications you have to choose properties

---

### Post by urukrama on 2008-04-01
There is also a plugin for the xfce panel that lets you use the Gnome 'Places' menu. It is called [xfce4-places-plugin]("http://packages.ubuntu.com/gutsy/xfce4-places-plugin") (only available in the Gutsy and Hardy repositories).

You then just have to add to other menus, one to the right, and one to the left. You can edit the menus by right clicking on them and selecting 'Edit menu'. Use a different menu file for both these menus (you can select that in the Menu properties window: Right click on menu > Properties). 

Leave the location line for the image of the System menu blank so it doesn't show an image to the left of it (between Places and System).

I've just been playing with this myself. I've attached a screenshot. The System menu isn't what I'd want it to be yet (as it still has all the applications in it too), but I am too tired now to edit that file further.

---

