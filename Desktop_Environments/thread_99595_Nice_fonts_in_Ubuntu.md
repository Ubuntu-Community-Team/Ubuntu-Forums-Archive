---
title: "Nice fonts in Ubuntu?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by mad_pheonix on 2005-12-05
I was suprised not to see a similar thread already in the forums.  I'd really like to know if Gnome / Ubuntu has any options for fonts other than that in the System -> Preferences -> Fonts panel.  It seems to me that you should really be able to set the font colors, especially for things like window titles.  I'd really like to be able to use a nice dark shiny background image for my panels, but if I do that then I can't see the default (black) fonts.  Does Gnome offer this functionality?

Also, for LCD panels what is the best type of Font Rendering?  On my laptop LCD I think subpixel-smoothing is the best, but I still don't think it stands up to *gag* windows ClearType fonts.  Please, linux, say it ain't so!

---

### Post by bb002 on 2005-12-05
gnome currently doesn't support changing the colors of fonts but this doesn't prevent you from doing so. There is some kind of file you have to edit by hand. Changing the default font color happens to be a feature I didn't even use in windows, much.

think the file is called ".gtkrc". Dunno where it is located or what to edit in it. Sorry I'm not more of a help.

---

### Post by SickTwist on 2005-12-06
The font colors are specified in the GTK2 theme. For simplicity, GNOME allows one to switch between themes but does not allow one to edit the specific details of each theme via the GUI. As bb002 said, you'll need to edit a config file for that (~/.gtkrc-2.0 I think but I'm not positive).

Another alternative would be to look for a theme that contains a color scheme that you like. There are *many* themes available on [Gnome-Look.org]("http://www.gnome-look.org/"). GTK2 themes are what you should look at to change the look and color of text and widgets (buttons, check boxes, radio buttons, etc). Metacity themes will change the look of the border that is drawn around every window and the windows' title bars.

---

### Post by dcstar on 2005-12-06
[QUOTE=mad_pheonix]
.......
Also, for LCD panels what is the best type of Font Rendering?  On my laptop LCD I think subpixel-smoothing is the best, but I still don't think it stands up to *gag* windows ClearType fonts.  Please, linux, say it ain't so![/QUOTE]
There are other threads around for "tweaking" the fonts to greatly improve them, do a search and you'll probably find the 5.04 HOWTO somewhere which may well be worth trying.

I originally did this in version 4.10 and the improvement was dramatic on my LCD monitor!

---

### Post by mad_pheonix on 2005-12-06
Great tips, thanks a lot!

---

