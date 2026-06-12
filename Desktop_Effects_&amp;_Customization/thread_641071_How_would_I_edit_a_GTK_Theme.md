---
title: "How would I edit a GTK Theme?"
date: 2007-12-15
forum: Desktop Effects &amp; Customization
---

### Post by radlations on 2007-12-15
I'm a complete noob here but I downloaded a GTK 2.XX file from gnome-look.org and I dragged it into the Appearance menu of Gnome.

well It installed this neat theme but there are problems.

All of my text fields are [grey colored]("http://img.photobucket.com/albums/v259/liVilike/Screenshot-1.png"). How can I make them white?

In other words how can I edit the theme itself.?

---

### Post by Brindled on 2007-12-15
in *Appearances* hit the button customize in the bottom-right-middle. once it opens the next menu, hit the tab for *Colors.* if the current theme you're using is able to it should allow you to change some of the system colors. if the theme is not compatible with this feature it will say so. if it does and this doesn't affect what aspect you want, you may be able to change it within the theme's system folder. 

maybe someone with more knowledge on the latter option could give us more info on it. :)

---

### Post by VictorR on 2007-12-15
I know two ways:
1. Gnome Color Chooser - a nice GUI application to change almost every color on the screen. I found it in gnome-look.org, but in the package I see a link
[http://www.punk-***-bitch.org/gnome-color-chooser/](http://www.punk-***-bitch.org/gnome-color-chooser/)

2. GTK2 theme is a text file 
$HOME/.themes/theme_name/gtk-2.0/gtkrc
creating or changing the theme means actually dealing with this file. You can try it yourself, the font color in input fields is 
text[NORMAL]
there are five other states, but it too much to explain.

---

### Post by radlations on 2007-12-17
What color in the GTK2 text file would I need to edit?

How come when I edit stuff in the file, It doesnt save? (Even if I click save)

---

### Post by VictorR on 2007-12-17
From what I can see in your screenshot, you have problems with your browser. Usually browsers manage their colours themselves - check browser options or preferences.

What theme do you want to modify?
If the file is located in
~/.themes/theme-name
it must be available for re-writing , The problem may appear if you are trying to save the file in
/usr/share/themes
 (which was installed from repos, rather than downloaded from art-work web-sites). In this case it is easier to copy the whole theme to your .themes home folder, and modify it here.

---

### Post by radlations on 2007-12-18
It's not just the browser. Its almost everywhere. My conversation box in Pidgin, my entire document in Open Office. I also dont enjoy the fact that it skins my programs. I only wanted it to skin my desktop and its bars. [IMG]http://img.photobucket.com/albums/v259/liVilike/Screenshot-darkness-FileBrowser.png[/IMG]

```
style "clearlooks-default"
{
  GtkMenuItem::selected_shadow_type = out
  GtkWidget::interior_focus = 1
  GtkButton::default_border = { 0, 0, 0, 0 }
  GtkButton::default_outside_border = { 0, 0, 0, 0 }
  GtkRange::trough_border = 0

  GtkWidget::focus_padding = 1

  GtkPaned::handle_size = 6

  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15 #toolbar arrows
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 12
  GtkMenuBar::internal-padding = 0

  GtkTreeView::expander_size = 14
  GtkTreeView::odd_row_color = "#38393b"
  GtkExpander::expander_size = 16

  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#b8b9bb" 
  fg[PRELIGHT]      = "#b8b9bb"
  fg[ACTIVE]        = "#b8b9bb"
  fg[SELECTED]      = "#b8b9bb" 
  fg[INSENSITIVE]   = "#48494b" 

  bg[NORMAL]		= "#28292b" 
  bg[PRELIGHT]		= "#38393b" 
  bg[ACTIVE]		= "#38393b" 
  bg[SELECTED]		= "#0050a1" 
  bg[INSENSITIVE]	= "#28292b" 

  base[NORMAL]		= "#48494b" 
  base[PRELIGHT]	= "#000000" 
  base[ACTIVE]		= "#0050a1" 
  base[SELECTED]	= "#0050a1" 
  base[INSENSITIVE]	= "#48494b" 

  text[NORMAL]		= "#b8b9bb"
  text[PRELIGHT]	= "#b8b9bb"
  text[ACTIVE]		= "#b8b9bb" 
  text[SELECTED]	= "#b8b9bb" 
  text[INSENSITIVE]	= "#48494b" 

  engine "clearlooks" 
  {
    contrast = 1.0
    sunkenmenubar = 1
  }
}


style "clearlooks-progressbar" = "clearlooks-default"
{
  xthickness = 1
  ythickness = 1
}

style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-notebook" = "clearlooks-wide"
{
  bg[NORMAL] = "#38393b"
  bg[ACTIVE] = "#38393b"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 5
  bg[NORMAL]		= "#262626"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
# base[SELECTED] = "#0050a1"
}

style "clearlooks-menu-itembar" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = "#b8b9bb"
}

style "clearlooks-panel" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = "#58595b"
}

style "clearlooks-combo" = "clearlooks-default"
{
  xthickness = 1
  ythickness = 2
}

style "metacity-frame"
{
  # Normal base color
  #bg[NORMAL]  = "#bbbbbb"

  # Unfocused title background color
  #bg[INSENSITIVE]  = { 0.8, 0.8, 0.8 }

  # Unfocused title text color
  #fg[INSENSITIVE]  = { 1.55, 1.55, 1.55 }

  # Focused icon color
  fg[NORMAL]  = "#b8b9bb"

  # Focused title background color
  bg[SELECTED]  = "#0050a1" 

  # Focused title text color
  fg[SELECTED]  = "#28292b"
}

class "GtkWidget" style "clearlooks-default"
class "GtkButton" style "clearlooks-wide"
class "GtkRange" style "clearlooks-wide"
class "GtkFrame" style "clearlooks-wide"
class "GtkStatusbar" style "clearlooks-wide"
class "GtkMenu" style "clearlooks-menu"
class "GtkMenuItem" style "clearlooks-menu-item"
widget_class "*MenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkAccelMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkRadioMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkCheckMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkImageMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkSeparatorMenuItem.*" style "clearlooks-menu-item"
class "GtkEntry" style "clearlooks-wide"
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"
widget_class "BasePWidget.GtkEventBox.GtkTable.GtkFrame" style "clearlooks-panel"
widget "gtk-tooltips" style "clearlooks-tooltips"
class "GtkNotebook" style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton" style "clearlooks-combo"
class "MetaFrames" style "metacity-frame"
```

---

### Post by radlations on 2007-12-18
Problem solved. I changed the colors in the GTK file. Yay im learning how to adapt to Ubuntu!

---

### Post by VictorR on 2007-12-18
Great!

What I would suggest is to change colors from "hard-coded" to customizable, like this:
```

 fg[NORMAL]       	=  @fg_color
  fg[ACTIVE]       	=  @fg_color
  fg[PRELIGHT]     	=  @fg_color
  fg[SELECTED]     	=  @selected_fg_color
  fg[INSENSITIVE]  	=  @selected_fg_color

  bg[NORMAL]       	=  @bg_color
  bg[ACTIVE]        	=  shade (1.025,@bg_color)
  bg[PRELIGHT]     	=  shade (1.10,@bg_color)
  bg[SELECTED]	    	=  @selected_bg_color
  bg[INSENSITIVE]  	=  shade (1.025,@bg_color) 

  base[NORMAL]     	=  @base_color
  base[ACTIVE]     	=  shade (0.65,@base_color) 
  base[PRELIGHT]   	=  @base_color
  base[SELECTED]	=  @selected_bg_color
  base[INSENSITIVE]	=  shade (1.025,@bg_color)

  text[NORMAL]     	=  @text_color
  text[ACTIVE]		=  shade (0.65,@text_color)
  text[PRELIGHT]   	=  @text_color
  text[SELECTED]   	=  @selected_fg_color
  text[INSENSITIVE]	=  shade (1.70,@bg_color)

```

I have taken this from Aurora Midnight theme by ECHM. In the top of the gtkrc file you could put default colors, like:
```

#default color scheme
gtk_color_scheme = "fg_color:#D4D4D4\nbg_color:#333333\nbase_color:#474747\ntext_color:#D4D4D4\nselected_bg_color:#0081DE\nselected_fg_color:#ffffff"

```
With such a definition one can play with colours using options in Color tab of Appearance - Customize.
.

---

### Post by radlations on 2007-12-18
Wow victor you did alot better than I did.

Thanks alot.

---

