---
title: "I have questions about gtkrc..."
date: 2014-01-27
forum: Desktop Environments
---

### Post by desconocido on 2014-01-27
Questions about gtkrc - by the way, is there a book about it?

I have just installed Ubuntu 12.04 after using 9.10 and have installed gnome-shell and removed unity.

Following advice in some of the threads on the forum, I tried altering some of the gtkrc settings. I know almost nothing about gtkrc.
I am keen to remove the colour orange (which is my least favourite colour) from as many places as possible.
I also find the tooltips and notifications (white text on a black background) very garish, especially with a pale theme like Radiance.

1) I created a file ~/.gtkrc-2.0 and set (in gtk-color-scheme = ) tooltip_fg_color:#ff0000
Nothing happened. Is that what you would expect?

2) I created a folder called
~/.themes/myRadiance/
and copied the contents of 
/usr/share/themes/Radiance 
into it and made changes to tooltip_fg_color:#111111, selected_bg_color:#6fdb57 and tooltip_bg_color:#c0dbba
I then used Gnome Tweak Tool to set GTK+ theme and Window theme to MyRadiance. (I wasn't allowed to change Shell theme - it said "Could not list shell extensions".)

That affected tooltips and selected text backgrounds in Firefox (except in windows looking at Ubuntu forums) and Thunderbird, but not in gedit, nautilus or gnome panels.
Is there a way of affecting these programs?

3) To see the effect of changes, do I just need to restart programs, logout and logon again or do I need to restart the computer? (I got confused because Firefox menu highlighting changed colour several hours after changing the gtkrc file, without me doing anything except resume from suspended.)

4) There are also other areas of orange I would like to change: icons for folders in gedit, firefox, nautilus and file dialogue boxes; the close button on windows; highlighting on system and application menus.

5) There is a new scroll bar appearance - a very thin scroll bar with a thicker slider that appears when the pointer gets close. This makes it extremely difficult to point at the column division line to change the width of columns, for example when the bookmarks column in nautilus needs a scroll bar. Is there a workaround or is there a value in gtkrc to make the column division line thicker?

6) The gold stars in Thunderbird hardly show up against the white background on my screen. Changes possible?

---

### Post by ajgreeny on 2014-01-27
This site may help you.
[https://developer.gnome.org/gtk3/3.2/GtkSettings.html](https://developer.gnome.org/gtk3/3.2/GtkSettings.html)

---

### Post by vasa1 on 2014-01-27
> **desconocido said:**
> ...
1) I created a file ~/.gtkrc-2.0 and set (in gtk-color-scheme = ) tooltip_fg_color:#ff0000
Nothing happened. Is that what you would expect?
I don't use ~/.gtkrc-2.0 for most theme adjustments and so won't comment. 

> 2) I created a folder called
~/.themes/myRadiance/
and copied the contents of 
/usr/share/themes/Radiance 
into it and made changes to tooltip_fg_color:#111111, selected_bg_color:#6fdb57 and tooltip_bg_color:#c0dbba
I then used Gnome Tweak Tool to set GTK+ theme and Window theme to MyRadiance. (I wasn't allowed to change Shell theme - it said "Could not list shell extensions".)

That affected tooltips and selected text backgrounds in Firefox (except in windows looking at Ubuntu forums) and Thunderbird, but not in gedit, nautilus or gnome panels.
Is there a way of affecting these programs?


Firefox and Thunderbird (and Google Chrome and LibreOffice) are gtk2 programs. To make changes to the appearance of these programs you mostly need to fiddle with ~/.themes/your_theme/gtk-2.0/gtkrc.

To make changed to the appearance of gedit and nautilus, you'll need to go into ~/.themes/your_theme/gtk-3.0. And in there, you'll see gtk.css and gtk-widgets.css, etc. Standards css syntax applies there.

> 3) To see the effect of changes, do I just need to restart programs, logout and logon again or do I need to restart the computer? (I got confused because Firefox menu highlighting changed colour several hours after changing the gtkrc file, without me doing anything except resume from suspended.)

In my experience, changing from one theme (the edited one), to another and back is enough to make changes visible for gtk2 apps. gtk3 apps may need a log out and log in.

> 4) There are also other areas of orange I would like to change: icons for folders in gedit, firefox, nautilus and file dialogue boxes; the close button on windows; highlighting on system and application menus.

Icons are another topic altogether.

> 5) There is a new scroll bar appearance - a very thin scroll bar with a thicker slider that appears when the pointer gets close. This makes it extremely difficult to point at the column division line to change the width of columns, for example when the bookmarks column in nautilus needs a scroll bar. Is there a workaround or is there a value in gtkrc to make the column division line thicker?

Yes, that's called the overlay scrollbar. It's been introduced in 11.04. You can disable it easily. I think that's already been asked and answered: I think if you search the forum for "overlay scrollbar" you'll find the solution.


If you don't mind my saying so, it would be easier if you ask specific questions about specific programs in separate threads.

---

### Post by vasa1 on 2014-01-27
Re. the scrollbars (and some other Unity tweaks)...
Look at [http://irclogs.ubuntu.com/2014/01/25/%23ubuntu-classroom.html#t18:34](http://irclogs.ubuntu.com/2014/01/25/%23ubuntu-classroom.html#t18:34) :
```
philipballew	also, if you do not like the scrollbars the way they are, this site shows how to change them:	18:34
philipballew	gsettings set com.canonical.desktop.interface scrollbar-mode normal	18:34
philipballew	if you want to go back:	18:34
philipballew	gsettings reset com.canonical.desktop.interface scrollbar-mode	18:34

```

---

### Post by Dennis N on 2014-01-28
A couple of points to be aware of:

To modify general appearance themes (like radiance, ambiance), you should change the theme files in **/usr/share/themes**. The reason is when you copy a theme folder to **~/.themes** and make your mods there, your result will not affect "root" applications (requiring root privileges) like Synaptic, Update Manager, etc. giving you an inconsistent appearance. If you download a new theme to try, it needs to be located there too.

Generally, for some colors (like selected background color), you need to fix settings in three theme sub folders:

in folder gtk-2.0: **gtkrc**
in folder gtk-3.0: **gtk.css**, **settings.ini**

Logout and Login is sufficient to see the changes.

Folder icons, action and application icons come from the icon theme found in **/usr/share/icons**. To change those, you need to use a different icon theme. Many available from gnome-look.org

Cursors also have themes. To change the cursor, you change the X11 mouse (cursor) theme. Those are also in **/usr/share/icons**. These can be tricky to universally change in Ubuntu; easier in Xubuntu or Lubuntu. Many cursors are available from gnome-look.org

All themes you might try don't universally work well with all applications. Most applications are set to look good with the default theme in mind.

Experiment and Learn

[907]

---

### Post by desconocido on 2014-01-28
> **vasa1 said:**
> If you don't mind my saying so, it would be easier if you ask specific questions about specific programs in separate threads.

Yes, maybe, although I am very happy with the sort of replies I have received.

---

### Post by desconocido on 2014-01-28
Thanks everyone, this is all very helpful.

---

### Post by vasa1 on 2014-01-28
> **desconocido said:**
> Yes, **maybe**, although I am very happy with the sort of replies I have received.
I'm sorry I didn't make it clear but it's not about you or me. Basically, questions that focus on a single issue and which have a title clearly reflecting that issue will be more helpful to *other* users.

In other words, while asking an omnibus question maybe convenient for the person who asks because "everything" is in one spot, others who just look at the title may not realize that there is something of interest to them or something they could help with.

Of course, how you wish to ask in the future is up to you :)

---

