---
title: "Changing the Gnome &quot;Start&quot; menu color"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by King_Critter on 2007-09-03
I'm looking for a way to change the color (background and text) of the Gnome start menu. As you can see from the below screenshot, the glaring white menu doesn't look so hot against a dark background. After some Googling, I did find out about the gtkrc-2.0 file. That looks like it might do what I want -- only problem is, I have no idea how to use it. So a cheat sheet or the like for that would be one way of solving my problem.

Screenshot:
[[IMG]http://img374.imageshack.us/img374/4756/gkrellshoot090307173549ss5.th.jpg[/IMG]](http://img374.imageshack.us/my.php?image=gkrellshoot090307173549ss5.jpg)

---

### Post by jsully1 on 2007-09-03
I may be able to give you a start in the right direction... here is my desktop:
[[img]http://mr2.phpwerx.net/Photos/Sully/Random/Screenshots/thumb/sullyslaptop.jpg[/img]](http://mr2.phpwerx.net/Photos/Sully/Random/Screenshots/full/sullyslaptop.jpg.html)

You'll see that my gnome panel font is white, but everything else is the normal black. To do this you'll want to create a file (unless it's there already) in your home directory called .gtkrc-2.0
by doing (and forgive me if you already know, but others may not)
sudo nano .gtkrc-2.0

In that file I have the following:
gtk-menu-popup-delay = 0
include "/home/sully/.gnome2/panel-fontrc"

The first line sets how long you need to hover over a menu before Gnome opens it. I like it snappy and fast, so I have it set to 0. 
The second (and important line) here tells gnome that I want to use a custom color for my gnome panel font.

Save this file, and then to this:
sudo nano .gnome2/panel-fontrc

The contents of this file should be:
style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

#FFFFFF is white - you can use Gimp or other various apps to find other custom colors and their corresponding hex codes. Save and quit - log out, log in - and you're done. Maybe the other font colors for the actual app menu are be customizable through this file?

---

### Post by King_Critter on 2007-09-03
Well, that gives me a few leads, but I still don't now how to do what I'm looking for. Thanks anyways, though. I'll keep experimenting, but in the meantime -- anyone else?

---

### Post by iamhugeinjapan on 2007-09-03
The easiest solution for you may be to just use a GTK theme that has dark menus. There are a lot of dark themes on Gnome Look.

[http://www.gnome-look.org/index.php?xcontentmode=100](http://www.gnome-look.org/index.php?xcontentmode=100)

---

### Post by King_Critter on 2007-09-03
Hmm, didn't think of that. But really, all I want is to change the menu color, nothing else. Is there a crash course in making your own GTK theme around here somwhere?

---

### Post by King_Critter on 2007-09-04
Well, this has sunk to the bottom of the deepest pit imaginable... AKA page two. So, as much as I abhor them, this is a bump. Because seriously, all I want is a crash course in GTK theming. Does no one know of any?

---

### Post by autocrosser on 2007-09-04
I'm at work right now--so can't post my info, but I'll look up the stuff this evening (I'm on the same time as you--so about 4/6 hrs from now)---there is a fair amount of reading to do, but you can get what you want with some "playing around":)

---

### Post by jhernandez1270 on 2007-09-04
gtk theming will take more time then just finding a theme in gnome-look.org, download it, go into system>preference>themes
and ad your new theme...it takes like 2 minutes

here's what my start looks like

---

### Post by King_Critter on 2007-09-04
> gtk theming will take more time then just finding a theme in gnome-look.org, download it, go into system>preference>themes and ad your new theme...it takes like 2 minutes

Yeah, I know. But all the themes I looked at changed stuff besides the start menu. And besides, I want to have minuet control over what it looks like. Isn't the ability to modify what you want one of the main tenants of Linux? 

> 
I'm at work right now--so can't post my info, but I'll look up the stuff this evening (I'm on the same time as you--so about 4/6 hrs from now)---there is a fair amount of reading to do, but you can get what you want with some "playing around" :D

Awesome! Thanks, man. :P

---

### Post by autocrosser on 2007-09-04
OK--Let's start with "heavy" reading--The current GTK info guide is:
[http://library.gnome.org/devel/gtk/unstable/index.html](http://library.gnome.org/devel/gtk/unstable/index.html)

A older guide that explains what to do with all that info:
[http://www.gtk.org/~otaylor/gtk/2.0/theme-engines.html]("http://www.gtk.org/%7Eotaylor/gtk/2.0/theme-engines.html")

And more:
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

And still more:
[http://library.gnome.org/devel/gtk/unstable/GtkSettings.html](http://library.gnome.org/devel/gtk/unstable/GtkSettings.html)



So what I'd do is download a theme you like & take it apart to see what the elements look like. I'd start by looking at one called Xfce-4.0_EH--It turns the menu blue/gray & looks like a good experimental subject. (I've included a .tar of it)---as long as you don't post it as your own (unless it is Very-Very modded), you can tear it apart to your heart's content......And to check the new theme you have---go no further than Synaptic--look for gtk-chtheme.

---

