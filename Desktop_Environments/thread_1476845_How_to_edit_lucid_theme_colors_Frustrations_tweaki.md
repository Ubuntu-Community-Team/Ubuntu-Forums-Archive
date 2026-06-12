---
title: "How to edit lucid theme colors? Frustrations tweaking Radiance theme."
date: 2010-05-08
forum: Desktop Environments
---

### Post by kolinab on 2010-05-08
Hi,

I actually rather like the Radiance theme included with Lucid, including the window button position on the left. There are a few changes I would like to make so it suits me better (scroll bar shape, progress bar color, window title bar color, etc.) 

I like elements of the Clearlooks classic theme - especially the clear blue color when highlighting selected items AND the little blue stripe I get on my 'active' Firefox tabs. Unfortunately I can't seem to have the best of both worlds. When I click to 'customize' the Radiance theme in the appearance dialog, strange and unpredictable things happen: 

I try to keep 'window border' set to Radiance, and change the control set to 'Clearlooks.' Sometimes the buttons revert to the right side of the windows, and generally I feel like I don't have the level of control I want to in this dialog to change colors etc. how I would like them. Unfortunately, I don't understand how themes work. I've read around on gnome-look.org, and even tried to download a few extra themes to see if I like them. I get confused. I don't understand 'theme engines' like metacity, etc. 

What is the difference between metacity and GTK 2.X? What theme engine does lucid use?

Is there a GUI theme editor program I can use someplace to have a greater level of control on my themes?

I've been down this road before and I usually end up with some theme compromise I'm not really happy with. Hopefully someone can point me in the right direction so I can have a little better control of my themes.

Thanks for reading,

K

---

### Post by wyliecoyoteuk on 2010-05-08
If you use gconf-editor, the settings are under metacity->general. Double click on button_layout and enter the following
:minimize,maximize,spacer,close

(the spacer is optional)

---

### Post by kolinab on 2010-05-08
Thanks for the reply. I'm actually happy with the buttons on the left as is the default in Radiance. 

What I'm after is information on how to change colors for other options (progess bars, etc.) It seems that there are many many things controlled by changing the control set, and I wish I had control over those 'micro' settings. . . or knew how to edit them. I know there are people out there doing this stuff, but I just don't know how to get 'under the hood' of my themes to start diddling.

[edit] I did find this thread [http://ubuntuforums.org/showthread.php?t=377397&highlight=edit+theme](http://ubuntuforums.org/showthread.php?t=377397&highlight=edit+theme) explaining some of what I'm asking about. It's outdated apparently so I'll update this thread with whatever good resources I find on the topic as things go.

[edit II] I have found a couple of links that are somewhat promising . . . one is for the gnome-color-chooser utility: [http://gnomecc.sourceforge.net/](http://gnomecc.sourceforge.net/) Another is for the 'murrine configurator' [http://gnome-look.org/content/show.php/?content=53951](http://gnome-look.org/content/show.php/?content=53951).

I know there must be some good guides out there for learning this kind of thing and I'll post links to them if I find them.

K

---

### Post by kolinab on 2010-05-08
I love these threads when I get into a dialog with myself. I have found some answers. I haven't acually LEARNED anything yet but found some of the threads and links from the many times this question has been asked before. It seems that there is as yet no simple, easy way to do what I want. However, I am including here a list of the links I will be reading . . . for the next guy who comes along.

Gnome Color Chooser: [http://gnomecc.sourceforge.net/](http://gnomecc.sourceforge.net/)

How to Edit GTK themes: [http://iwan.tumblr.com/post/505979526/how-to-edit-gtk-themes-efficiently](http://iwan.tumblr.com/post/505979526/how-to-edit-gtk-themes-efficiently)

How to change GTK theme colors: [http://forum.xfce.org/index.php?topic=5326.0](http://forum.xfce.org/index.php?topic=5326.0)

Building Themes (old thread): [http://ubuntuforums.org/showthread.php?t=432286](http://ubuntuforums.org/showthread.php?t=432286)

How to change progress bar: [http://ubuntuforums.org/showthread.php?t=1267681](http://ubuntuforums.org/showthread.php?t=1267681)

How to modify GTK theme: [http://ubuntuforums.org/showthread.php?t=1410877](http://ubuntuforums.org/showthread.php?t=1410877)

Gnome Art Useful links: [http://live.gnome.org/GnomeArt/Tutorials/UsefulLinks](http://live.gnome.org/GnomeArt/Tutorials/UsefulLinks)

GTK Theming tutorial: [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

GTK theme creation guide (old): [http://www.orford.org/gtk/](http://www.orford.org/gtk/)

That's where I'm going to start reading . . . So, best of luck if you embark upon the same adventure.

K

---

### Post by usnica on 2010-08-21
Did you ever figure this out?  I found out to change the fill color, border, and roundness of the progress bar, edit the gtkrc file for the Radience theme (or you can copy the GTK-2.0 folder into a new theme name).  Look for this section:

  style "progressbar"

These lines affect the following:
  border_colors       	= { "#E0D6BA", "#E0D6BA" }    >>change outline of progressbar
  roundness		= 0    >>change roundness of progressbar (0=square)
  bg[SELECTED] 	= "#E0D6BA"    >>change color of progressbar

The values above make the progressbar the color of the menubar and squared.  Select a different theme and then go back to the Radience theme and you should see the changes.  I hope this helps.

---

