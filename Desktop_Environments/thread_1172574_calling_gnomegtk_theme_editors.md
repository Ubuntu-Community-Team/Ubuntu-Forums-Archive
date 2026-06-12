---
title: "calling gnome/gtk theme editors"
date: 2009-05-28
forum: Desktop Environments
---

### Post by thomasboleyn on 2009-05-28
Hi there, I'm playing around with themes on Ubuntu Jaunty at the moment, and am wondering what changes I have to make to my current theme 'MurrinaAquaIsh' to get the gnome clock to appear on 2 lines like the screenshot included below. So far the only way I have managed to achieve this is by using windows 7 clone themes, none of which I particularly like. I have also included my current theme's (MurrinaAquaIsh with modded colours) gtkrc file.
Any help would be greatly appreciated, thanks.


[PHP]style "theme-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 24
  
  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#3C3C3C"
  fg[PRELIGHT]      = "#222222"
  fg[ACTIVE]        = "#505050"
  fg[SELECTED]      = "#ffffff"
  fg[INSENSITIVE]   = "#A2A2A2"

  bg[NORMAL]        = "#F0F0F0"
  bg[PRELIGHT]      = "#efefef"
  bg[ACTIVE]        = "#DDD3BE"
  bg[SELECTED]	    = "#DDD3BE"
  bg[INSENSITIVE]   = "#ddd3be"

  base[NORMAL]      = "#F6F6F6"
  base[PRELIGHT]    = "#ddd3be"
  base[ACTIVE]      = "#ddd3be"
  base[SELECTED]    = "#ddd3be"
  base[INSENSITIVE] = "#ddd3be"

  text[NORMAL]      = "#000000"
  text[PRELIGHT]    = "#000000"
  text[ACTIVE]      = "#000000"
  text[SELECTED]    = "#000000"
  text[INSENSITIVE] = "#000000"

  GtkTreeView::odd_row_color = "#F5F5F5"
  GtkTreeView::even_row_color = "#FFFFFF"
  GnomeHRef::link_color		="#8D52DC" 
  GtkIMHtmlr::hyperlink-color	="#8D52DC"

  engine "murrine" 
  {
	 scrollbar_color     = "#ddd3be"
	 contrast 					 = 1.0
	 menubarstyle        = 2 # 0 = flat, 1 = glass, 2 = gradient
	 menubaritemstyle	   = 1 # 0 = menuitem look, 1 = button look
	 listviewheaderstyle = 0 # 0 = flat, 1 = glass
   animation           = TRUE
  }
}


style "theme-wide" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
}

style "theme-entry" = "theme-wider"
{
  bg[SELECTED]	    = "#93c1ff"
}

style "theme-button" = "theme-wider"
{
  bg[NORMAL]        = "#f2f2f2"
  bg[PRELIGHT]      = "#ddd3be"
  bg[ACTIVE]	     = "#D3D3D3"
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]      = "#efefef"
  bg[INSENSITIVE] = "#efefef"
  bg[SELECTED]    = "#ddd3be"
}

style "theme-tasklist" = "theme-default"
{
  xthickness = 5
  ythickness = 3
}

style "theme-menu" = "theme-default"
{
  xthickness = 2
  ythickness = 1
}

style "theme-menu-item" = "theme-default"
{
  ythickness = 3

}

style "theme-menubar" = "theme-default"
{
  #bg[NORMAL] = "#D7D7D7"
}

style "theme-menubar-item"
{
	ythickness = 4
	bg[PRELIGHT] = "#93c1ff"
}

style "theme-tree" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] = "#404040"
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 1
  ythickness = 1
}

style "theme-combo" = "theme-button"
{
}

# widget styles
class "GtkWidget"      style "theme-default"
class "GtkButton"      style "theme-button"
class "GtkScale"       style "theme-button"
class "GtkCombo"       style "theme-button"
class "GtkRange"       style "theme-wide"
class "GtkFrame"       style "theme-wide"
class "GtkMenu"        style "theme-menu"
class "GtkEntry"       style "theme-entry"
class "GtkMenuItem"    style "theme-menu-item"
class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "*MenuBar*"      style "theme-menubar"

widget_class "*MenuItem.*" style "theme-menu-item"
widget_class "*MenuBar.*"  style "theme-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "theme-combo"
widget_class "*.GtkCombo.GtkButton"    style "theme-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "theme-tasklist"
widget "gtk-tooltip*" style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "theme-tree"
widget_class "*.GtkCTree.GtkButton" style "theme-tree"
widget_class "*.GtkList.GtkButton" style "theme-tree"
widget_class "*.GtkCList.GtkButton" style "theme-tree"
widget_class "*.GtkFrame.GtkLabel" style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"[/PHP]

---

### Post by thomasboleyn on 2009-05-31
Bump:popcorn:

---

### Post by days_of_ruin on 2009-05-31
Have you tried using a fatter panel?
Mind posting a link to the theme you used to get it on two lines?

---

### Post by thomasboleyn on 2009-06-01
> **days_of_ruin said:**
> Have you tried using a fatter panel?
Mind posting a link to the theme you used to get it on two lines?

Here is a link to a gtk theme that makes the clock appear on 2 lines: [http://www.gnome-look.org/content/show.php/Windows+Seven+Plastic+Theme?content=101307](http://www.gnome-look.org/content/show.php/Windows+Seven+Plastic+Theme?content=101307). I changed it a bit so that it didn't use a custom image for the background of the panel though.

It also causes the window list to appear on 2 lines, though I don't use that applet, so it isn't an issue for me. I just need to know what line(s) to add/edit in my current theme to achieve this. Comparing the two themes side by side in gedit is a nightmare, particularly as the ones that come with the engines in the repos are neatly put together code-wise, and a lot of themes from gnome-look are really untidy in that respect. Thanks for the reply.

---

### Post by thomasboleyn on 2009-06-02
Just an update on progress - changing the panel height to anything over 47 pixels does cause the clock to change, though I would like it to do so with a 40px panel. Any help would be appreciated:KS

---

### Post by thomasboleyn on 2009-06-03
Bump:KS

---

### Post by thomasboleyn on 2009-06-04
Ok, I've sort of achieved what I wanted by using a custom format in gconf-editor for the panel clock, and inserting a line break inbetween the time and the date. The problem now is that the second line in very close to the bottom of the panel, and it looks a bit..weird. The win7 clone themes must have some specific coding in the gktrc file that allows this line break that looks better than the gconf method, though I just can't for the life of me figure out which part this is. 

Any help would be appreciated!

---

