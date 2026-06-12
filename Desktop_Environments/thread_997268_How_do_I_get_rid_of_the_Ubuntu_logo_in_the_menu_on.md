---
title: "How do I get rid of the Ubuntu logo in the menu on the gnome panel?"
date: 2008-11-29
forum: Desktop Environments
---

### Post by speaker219 on 2008-11-29
How do I get rid of this?
[IMG]http://sp219.b3ta.org/hlog.png[/IMG]

---

### Post by muadnu on 2008-11-29
What you can do is change the icon. Maybe the easiest way is to install Ubuntu Tweak (go to [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)).

Then go to Applications->System Tools->Ubuntu Tweak. Then go to Desktop->Gnome, and you can change the icon there. If you really want to get rid of the icon, I guess you can try using an empty image file or a very small transparent one.

---

### Post by Cammy on 2008-11-29
We're all assuming he wants to keep the menu. ;)

---

### Post by speaker219 on 2008-11-29
Thanks a lot.
Wish it was possible to remove the logo entirely, but this will suit me just fine until I figure out a way to do that ;-)
Much appreciated.

---

### Post by OrangeCrate on 2008-11-29
I haven't used Ubuntu tweak, and I haven't tried to just delete the logo, but I have changed it, using the following instructions.

Play around with these instructions to see if you can just delete it. (I'm on Xfce right now, and the procedure is different, so I can't check whether it works or not.)

First, find a .png logo (24x24 pixels) you want to change it to, and put it in your Home folder labeled:

start-here.png

Then open your terminal, and type the following command:

gconf-editor 

When you execute this command, a "Configuration Editor" window will open. Then, go down the list on the left and do the following:

apps > panel > objects > object_0

Your start menu icon will probably be object_0, but it may be another object. Look at them all.

If you want to change the logo, do this:

In the right pane, check the box for Use_Custom_Icon. Then, go up and right click:

custom_icon > Edit Key 

In the value box type:

/home/USERNAME/start-here.png 

Once you have entered this into the box, click OK.

If you followed all steps correctly, then you should see your new icon on your Main Menu.

---

