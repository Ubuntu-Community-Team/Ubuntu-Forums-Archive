---
title: "Change Panel Theme"
date: 2007-03-19
forum: Desktop Environments
---

### Post by NautTboy on 2007-03-19
I installed a theme that was title Vista something.  Anyway, I like it a lot.  Just one thing, the panel didn't change.  All windows has a darker border except the main panel.  Anyone know which or how i can change the theme so the main panel is darker and vista color like?

---

### Post by floke on 2007-03-19
Right click on the panel.
Select properties.
Have a play.

Alternatively, try using some of the dark gtk themes from gnome-look.org. I have neutronium high at the moment and it turns the panel a very vista-ish black.

[EDIT] To install theme use system/prerferences/theme

---

### Post by sethmahoney on 2007-03-19
Right-click on the panel and click "Properties".  In the background tab you can change all sorts of color settings, or use an image instead of a solid color as the panel background.

EDIT: Heh, you beat me to it.

---

### Post by ardchoille42 on 2007-03-19
> **NautTboy said:**
> I installed a theme that was title Vista something.  Anyway, I like it a lot.  Just one thing, the panel didn't change.  All windows has a darker border except the main panel.  Anyone know which or how i can change the theme so the main panel is darker and vista color like?

What you installed was a Metacity theme. Metacity is the default window manager in gnome and takes care of theming the titlebar and window border, that is all Metacity does. To change the panel, you need to change the GTK2 theme, this is in the Controls tab of the theme manager.

There are several different kinds of themes:

Metacity theme - takes care of theming the window border, titlebar and titlebar icons
GTK2 theme - takes care of theming the panel, widgets (scrollbars, buttons, menus, etc)
Icon theme - takes care of the icons in your apps and on your desktop.

---

### Post by NautTboy on 2007-03-20
Thanks to all, but special thanks to Ardchoil for the break down.  It really helps me understand what is what not just how to do it.

---

### Post by ardchoille42 on 2007-03-20
> **NautTboy said:**
> Thanks to all, but special thanks to Ardchoil for the break down.  It really helps me understand what is what not just how to do it.

you're quite welcome :)

And, if you ever feel like making your own themes, there are some great tutorials [here]("http://live.gnome.org/GnomeArt/Tutorials").

---

### Post by NautTboy on 2007-03-23
All I wanted to do was change the main panel to dark plastic to match the windows.  Most of the theme I downloaded change the whole windows.  Do you know a good theme to change JUST the main panel to Vista-ish dark color?

---

### Post by mgmiller on 2007-03-23
Try "Darker theme 0.3" from gnomelooks.org  It makes the panels a vistaish shiny dark color.  It is a GTK 2.x theme

---

### Post by ComplexNumber on 2007-03-23
> **NautTboy said:**
> All I wanted to do was change the main panel to dark plastic to match the windows.  Most of the theme I downloaded change the whole windows.  Do you know a good theme to change JUST the main panel to Vista-ish dark color?
try [this]("http://gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570"). this is what the panel looks like. it seems to be what you're looking for.

---

### Post by NautTboy on 2007-03-26
Hey thanks again, I thought I downloaded this before but I guess I didn't download the all in one package instead I just downloaded just the SVG.  That Start button does look good, how/where do we download that too?

---

### Post by miatawnt2b on 2007-03-28
I'm sort of in the same boat, but cannot seem to figure out how to edit the title-bar color.  When you say right click on the panel, you mean the title-bar correct?  I don't have a properties option if I do that.
Thanks,
-J

---

### Post by XerXeX on 2007-12-06
Ok, this has taken me the whole night...its 8AM here, Im trying to use the panel from this theme: [http://www.gnome-look.org/content/show.php/Darker+theme?content=32768](http://www.gnome-look.org/content/show.php/Darker+theme?content=32768) to go with the rest of this theme: [http://www.gnome-look.org/content/show.php/Wii-Black?content=45829](http://www.gnome-look.org/content/show.php/Wii-Black?content=45829) !

I have tried just to use the GTK2 theme from the "Darker Theme" bc Im only after the panel but I cannot get it right. I have copied the buttons, renamed them for the Wii.Blacks gtkrc etc etc, but it never turns 100%.  I think the panel from "darker theme" fits perfect into the rest of "wii black" that has almost everything that Im after except the panel!

If someone can help me out Id really appreciate it, thanks!

---

### Post by subs on 2007-12-06
goto Preferences > Appearence 

in the Themes tab click on Customize and then change icon sets... fonts etc to make ur pc look more like vista.....

floke has alredy told u how to change the gnome panel

---

### Post by Mr.Thing on 2007-12-06
Alternative way, if you are familiar with GIMP. Just open your screenshot in GIMP,  Zoom it to 800%. Select only the top side of your window decoration, with 20-40 pixels width. Copy & Paste in new image, give this layer a little bit of transparency if you want your panel to be with a touch of transparency, than resize the image height to the height of your panel and save it as PNG. Than go to panel properties, and set the saved image as the panel background.
I've attached the shot with selection in GIMP.

That is it :) Good luck!

---

### Post by XerXeX on 2007-12-06
Thx Subs and Mr.Thing but thats not what I was after. I dont even need to use Gimp to get the same panel, I can just open the tar.gz and use the panel png files.

If I use the "darker theme" panel and just change the icons it wont be correct either. I need to go into the gtkrc file and combine and re-write some of the codes from both themes to make it work. I have been close to get what Im after but not 100%, hope that clears some!

---

### Post by stylish_way on 2008-01-15
Hi ..... i'm  a novice when it comes to Linux .... I want to change the panel myself but i am not able to do so can anyone provide a step by step guide to help me out ..... Ubuntu ROX

---

