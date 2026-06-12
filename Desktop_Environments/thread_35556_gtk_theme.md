---
title: "gtk theme"
date: 2005-05-19
forum: Desktop Environments
---

### Post by brandan on 2005-05-19
does anybody have experience with this?  i've edited another theme enough to get a general look of what i'd want, but there are still a few issues.

for instance, i'm trying to get rid of borders completely, but i've noticed there are still borders on menus and tabs.  i'm also trying to change the color of the menus, but for some reason they remain white.  if anybody would look at this and maybe point me in the right direction i'd appreciate it.

```
include "icons/iconrc"

style "whiteplate-default"
{
  GtkWidget::interior_focus = 1
  GtkButton::default_border = { 0, 0, 0, 0 }
  GtkButton::default_outside_border = { 0, 0, 0, 0 }
  GtkRange::trough_border = 0

  GtkWidget::focus_padding = 0

  GtkPaned::handle_size = 20
  
  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 13
  GtkRadioButton::indicator_size = 13
  GtkMenuBar::internal-padding = 0
  GtkMenuBar::trough_border = 0
  
  GtkButton::child_displacement_x = 0
  GtkButton::child_displacement_y = 1

  PanelMenu::stripe-color = "#e7ebef"

  GtkMenuItem::selected_shadow_type = GTK_SHADOW_IN

  #GtkOptionMenu::indicator_size = { 11, 6 }
  #GtkOptionMenu::indicator_spacing = { 4, 5, 2, 2 }

  xthickness = 0
  ythickness = 0
  
  bg[NORMAL]      = "#e7ebef"
  bg[NORMAL]      = "#e7ebef"
  bg[PRELIGHT]	  = "#e7ebef"
  bg[ACTIVE]	  = "#e7ebef"
  bg[INSENSITIVE] = "#e7ebef"
  bg[SELECTED]    = "#e7ebef"
  
  fg[PRELIGHT]    = "#000000"
  
  base[SELECTED]  = "#e7ebef"
  text[SELECTED]  = "#ffffff"

  engine "industrial" {}
}

style "whiteplate-unrounded" = "whiteplate-default"
{
  engine "industrial" 
    {
      rounded_buttons = FALSE
    }
}

style "whiteplate-wide" = "whiteplate-default"
{
  bg[NORMAL] = "#ffffff"
  xthickness = 0
  ythickness = 0
}

style "whiteplate-tasklist" = "whiteplate-default"
{
  xthickness = 0
  ythickness = 0
}

style "whiteplate-arrows" = "whiteplate-default"
{
  fg[NORMAL] = "#999999"
  bg[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#999999"
  bg[PRELIGHT] = "#ffffff"
  fg[SELECTED] = "#999999"
  bg[SELECTED] = "#ffffff"

xthickness = 0
ythickness = 0

}

style "whiteplate-menu" = "whiteplate-default"
{
  xthickness = 3
  ythickness = 3

  bg[NORMAL] = "#e7ebef"
  bg[PRELIGHT]  = "#e7ebef"
  bg[SELECTED]  = "#e7ebef"
  fg[PRELIGHT]  = "#000000"
  fg[SELECTED]  = "#000000"
}

style "whiteplate-menu-separator" = "whiteplate-default"
{
  xthickness = 0
  ythickness = 0

  bg[NORMAL] = "#e7ebef"
  fg[NORMAL] = "#e7ebef"
  bg[PRELIGHT]  = "#e7ebef"
  bg[SELECTED]  = "#e7ebef"
  fg[PRELIGHT]  = "#e7ebef"
  fg[SELECTED]  = "#e7ebef"
}

style "whiteplate-menubar" = "whiteplate-default"
{
  fg[NORMAL] = "#e7ebef"
  xthickness = 0
  ythickness = 0
}

style "whiteplate-handlebox" = "whiteplate-default"
{
  fg[NORMAL] = "#ffffff"
	xthickness = 0
	ythickness = 0
}

style "whiteplate-paned" = "whiteplate-default"
{
  xthickness = 0
  ythickness = 0
}

style "whiteplate-tree" = "whiteplate-default"
{
  engine "industrial" 
    {
      rounded_buttons = FALSE
    }
  xthickness = 0
  ythickness = 0
}

style "whiteplate-frame-title" = "whiteplate-default"
{
xthickness = 0
ythickness = 0
}

style "whiteplate-panel" = "whiteplate-default"
{
  xthickness = 0
  ythickness = 0
}

style "whiteplate-tooltips" = "whiteplate-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL] = "#e7ebef"
}

style "metacity-frame"
{

	# Normal base color
 	bg[NORMAL]      = "#e7ebef"

	# Unfocused title background color
	bg[INSENSITIVE]	= "#e7ebef"

	# Unfocused title text color
	fg[INSENSITIVE]	= "#000000"

	# Focused icon color
	fg[NORMAL]	= { 0.2, 0.2, 0.2 }

	# Focused title background color
	bg[SELECTED]	= "#e7ebef"
	
	# Focused title text color
	fg[SELECTED]	= "#000000"
}

#class "Gtk*Paned" style "whiteplate-paned"

widget "*.tasklist-button" style "whiteplate-unrounded"
widget_class "*.GtkTreeView.*" style "whiteplate-tree"
widget_class "*.GtkList.*" style "whiteplate-tree"
widget_class "*.GtkCList.*" style "whiteplate-tree"
widget_class "*.ETree.*" style "whiteplate-tree"
widget_class "*.ETable.*" style "whiteplate-tree"

class "GtkNotebook" style "whiteplate-wide"
class "GtkWidget" style "whiteplate-default"
class "GtkButton" style "whiteplate-wide"
class "GtkRange" style "whiteplate-wide"
class "GtkMenu" style "whiteplate-wide"
class "Gtk*Bar" style "whiteplate-menubar"
class "*Tool*" style "whiteplate-menubar"
class "*Handle*" style "whiteplate-menubar"
class "*Bonobo*" style "whiteplate-handlebox"
class "GtkFrame" style "whiteplate-wide"
class "GtkStatusbar" style "whiteplate-wide"
class "GtkMenuItem" style "whiteplate-menu"
widget_class "*.GtkMenuItem.*" style "whiteplate-menu"
widget_class "*.GtkAccelMenuItem.*" style "whiteplate-menu"
widget_class "*.GtkRadioMenuItem.*" style "whiteplate-menu"
widget_class "*.GtkCheckMenuItem.*" style "whiteplate-menu"
widget_class "*.GtkImageMenuItem.*" style "whiteplate-menu"
widget_class "*.GtkSeparatorMenuItem.*" style "whiteplate-menu-separator"
class "GtkEntry" style "whiteplate-wide"
widget_class "*.tooltips.*.GtkToggleButton" style "whiteplate-tasklist"
widget_class "*.GtkFrame.GtkLabel" style "whiteplate-frame-title"
widget_class "*.GtkFrame.GtkCheckButton.GtkLabel" style "whiteplate-frame-title"
class "MetaFrames" style "metacity-frame"
class "GtkVScrollbar" style "whiteplate-arrows"
class "GtkHScrollbar" style "whiteplate-arrows"
widget_class "BasePWidget.GtkEventBox.GtkTable.GtkFrame" style "whiteplate-panel"
widget "gtk-tooltips" style "whiteplate-tooltips"

```

i can't take a screenshot while i've got a menu active (i.e. i've clicked on it), but [here's](http://members.cox.net/glendenning/screenshot.png) a screenshot of the theme how it looks now, so maybe anybody who's interested in helping me can see just what it is i'm going for.  the problem in the menus is that the top and bottom have borders.

also, is it possible to configure the window list panel (at the very bottom) in the same fashion (making the application buttons borderless), or better yet so that the buttons are transparent?

and finally, i've noticed that since i edited the theme that some buttons by default are depressed when windows pop up.  does anybody know what in the gtkrc could be causing that?

thanks for any help.

---

### Post by hamvil on 2007-10-23
The post is very old. However I'm trying to get the same result, namely menu witout borders. Is there a way to achive this?

Bye
Roberto

---

