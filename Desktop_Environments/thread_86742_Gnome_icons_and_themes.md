---
title: "Gnome icons and themes"
date: 2005-11-06
forum: Desktop Environments
---

### Post by dpm on 2005-11-06
Hi everybody. 

I am posting several questions on this thread, in the hope that someone can bring some light onto this subject, because at the moment I am quite confused about this.

I am trying to change some of the gnome icons that are global to gnome applications (e.g. the "Home" and "Reload" icons, used for example by nautilus and epiphany), but I just don't know how to start...

I have tried using the System->Preferences->Theme graphical tool, but that does not allow me to actually see or change the individual icons.

Then, I saw that there are some system-wide directories that contain the globally available themes and icons:

/usr/share/themes
/usr/share/icons
/usr/share/pixmaps

as well as some user-specific directories for the user-created themes:

~/.themes
~/.icons

(are there any more?)

I created my own very simple theme (using the Theme application) by combining the Clearlooks "Control", the Human "Window Border", and the Gnome "Icons". After that, my ~/.themes folder contained my newly-created theme (I called it Modified Human for the lack of a better name), but my ~/.icons folder remained empty. 

Now I do not know what to do in order to change the particular icons I'm interested in, because I do not know where they reside, for a start!. Yes, I know there is a /usr/share/icons/gnome folder for my currently selected icon theme, but I cannot find the "Back", "Forward" and "Reload" icons in there, for example. In fact, I am only guessing that that is the right directory, I don't even know.

Now, to add to the confusion, I have seen that epiphany, for example, has got a folder with icons that are, as I'm guessing, independent of the icon theme! (see /usr/share/epiphany-browser/art) Is that right?

My questions, then are the following:

1.- Why are there two directories for icons (i.e /usr/share/icons and /usr/share/pixmaps) and what's the purpose of each one of them?

2.- What is (roughly) the difference between GTK themes and Metacity themes? Are both Metacity and GTK themes stored in the /usr/share/themes directory, or are there different directories for each type of theme?

3.- What are "stock" icons?

4.- Finally, how can I change individual icons in the GNOME icon theme?

Thanks for your help.

---

### Post by kperkins on 2005-11-06
stock icons are the ones you're looking for, I believe.  They are named like stock_reload, or navigation_reload (depend on the theme, I think.)
Try putting your new icons in the stock folder of the theme you are using, and naming them using the convention I mentioned.  Tere's a tutorial somewhere on the gnome-art site that explains how to make icon sets.
[http://live.gnome.org/GnomeArt_2fTutorials_2fIconThemes](http://live.gnome.org/GnomeArt_2fTutorials_2fIconThemes)
> As of GTK2.4, stock icons (the icons used in toolbar buttons, menu items, and other widgets) can be defined in the icon theme.
Doesn't really explain the naming convention, but it looks fairly simple.
YMMV

Oh, yeah--/usr/share/pixmaps is basically for application icons like you see in the panel, or menu (and some thing specific to some gnome apps), and /usr/share/icons is for theme icons (which can also have app icons in it)

---

### Post by Xian on 2005-11-06
[QUOTE=desp]1.- Why are there two directories for icons (i.e /usr/share/icons and /usr/share/pixmaps) and what's the purpose of each one of them?[/quote]
~/pixmaps are generally used for menu icons.
~/share/icons are generally used for theme icons.

[QUOTE=desp]2.- What is (roughly) the difference between GTK themes and Metacity themes?[/quote]
I'd just google for info on this. It's a design thing. 

[QUOTE=desp]3.- What are "stock" icons?[/quote]
More akin to "not categorized".

[QUOTE=desp]4.- Finally, how can I change individual icons in the GNOME icon theme?.[/QUOTE]

Two methods:

1. Find the theme you are using by name in the Gnome Theme manager.
Goto /user/share/icons and open that theme directory.
Replace the applicable instance by size of the icon you want to change.

2. Right-click on the icon (if a non-menu image) and change from menu.

---

### Post by dpm on 2005-11-07
kperkins, Xian: thanks for your help. Now I understand a bit better how themes work.

I've still got some questions, though:

1.- The "original" or "base" stock icons, are GTK icons, aren't they? Where are they located (I found some in /usr/share/doc/libgtk2.0-doc/gtk, but this somehow seems like a strange location to me)? 

2.- After googling for an explanation of GTK and Metacity themes, I still cannot quite understand the differences between them, and whether they both reside in a common directory or not. Does anyone know anything about this?

3.- By the way, does anyone know whether there's an application to create icon themes? (I just want to spare myself the effort of typing everything on the .theme file).

Thanks again.

---

### Post by 23meg on 2005-11-07
Metacity themes affect your window decorations such as title bars, corners, borders. GTK themes affect the appearance of GTK widgets, which means pretty much everything else you see in Gnome.

---

### Post by dpm on 2005-11-07
Ok, now I've got a better picture of the whole theme thing. In case someone is interested, I've found out a bit more:

in ubuntu, what resides in /usr/share/themes are _methathemes_ (X-GNOME-Metathemes). These specify combinations of a gtk theme (also called engine), a metacity theme, and an icon theme (I understand them as containers or theme supersets). 

I believe the gtk engine resides in /usr/share/themes/<theme-name>/gtk-2.0, although I think there is also some code involved, for which I haven't found out the location yet.

The metacity theme resides in /usr/share/themes/<theme-name>/metacity-1, and it is basically an XML file defining things like window borders, title bars, and so on, as it has been pointed out before in this thread. The gnome website has got some documentation on the format of this file.

Finally, the icon theme resides in /usr/share/icons, and it may or it may not replace the original gtk stock icons (which I'm still not sure where they are).

These are all system-wide themes; the user-specific counterparts reside in ~/.themes (for methathemes) and in ~/.icons (for icon themes).

What is confusing at first (at least for me it was), is the fact that gtk engines, metacity themes and gnome methathemes can all have the same name. E.g. the Clearlooks methateme contains the Clearlooks gtk engine, the Clearlooks metacity theme, and the gnome icon theme; the Human methatheme contains the Clearlooks gtk engine, the Human metacity engine, and the gnome icon theme.

That's what I found out today. Now I'm happy with what I understand about this whole thing, although one question remains::

1.- I still haven't found out where the gtk stock icons live. I know they can be replaced by the stock icons specified by the icon theme, but I'd like to know where do the original gtk icons come from. As I said before (post #4), I found quite a lot of those in /usr/share/doc/libgtk2.0-doc/gtk, but I'm not so sure they come from there. Does anyone know?

All what I've written here is based on what I've been reading on the net, the current and other threads, and what I've seen on my system. Please feel free to correct me if anything I wrote was wrong or inaccurate. I appreciate any comment on this; I'm a Linux newbie that first started with Hoary, and every time I learn something new about this world (be it Linux/GNU/GNOME/Debian or Ubuntu...) it feels like a great achievement to me :) !

---

