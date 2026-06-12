---
title: "removing shadows"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by soulmatic09 on 2007-11-13
hello-

i'm customizing a theme to my liking, but i can't figure out how to solve two small things:

1) i'm trying to remove the drop shadow at the top portion of the window, where the back buttons are. (i'm not sure what this is called. the control?) 

it looks like something out of windows 95, so i'm trying to delete the edge shadow.


2) in firefox, for some reason the file menu text, and drop downs menus need to be changed. i can't figure out where specific font colors are determined. i keep getting white on white text, or black on black text.

any ideas?

---

### Post by jimerickso on 2007-11-13
you could got to system > preferences > advanced desktop settings
select window decorations plugin
move sliders to adjust drop shadow
good luck!

---

### Post by soulmatic09 on 2007-11-13
um, i don't have an advanced desktop settings option.

any other ideas?

---

### Post by FuturePilot on 2007-11-13
It looks to me that Firefox isn't being themed. Try changing themes. System>Preferences>Appearance

---

### Post by jimerickso on 2007-11-13
try the following

sudo apt-get install compizconfig-settings-manager

---

### Post by Rupertronco on 2007-11-13
> **soulmatic09 said:**
> um, i don't have an advanced desktop settings option.

any other ideas?

Download the aforementioned package (compizconfig-settings-manager) and to run it type ```
ccsm
``` in a terminal or in a run box. You'll get a nice little configuration utility that lets you change a plethora of settings in Compiz Fusion.

Scroll down through until you get to the windows decoration (as said above) plug-in and from there you can manipulate or eliminate the drop shadow.

Also, once you've downloaded ccsm you'll find that you can customize your theme to an even greater degree due to its many options.

---

### Post by soulmatic09 on 2007-11-13
> **jimerickso said:**
> try the following

sudo apt-get install compizconfig-settings-manager

Perfect! that did it.

what about the white text? it's not just firefox, open office has the same problem too.

---

### Post by Phung1s on 2007-11-13
I think thats an issue with your theme, I've found some themes have near invisible menu text in applications and no option to udjust color preferences within the appearance menu.  Would be interested to know if anyone knows of another was to fix this

---

### Post by soulmatic09 on 2007-11-13
i figured it was a problem with the theme, but i don't know the name of the menu item variable to change.

i'll attach the code below:

```
#gtk-button-images = 0


include "panel/panel-aq.rc"
include "scroll/scrollbar.rc"
#include "progressbar/progressbar.rc"
include "list/list.rc"
include "buttons/buttons.rc"
include "checkradio/checkradio.rc"
include "combobox/combobox.rc"
include "option/optionmenu.rc"
include "tabs/tabs.rc"
include "shadows/text-entry.rc"
include "menu/menu.rc"
include "spin/spinbuttons.rc"
include "range/range.rc"


style "theme-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15
  
  GtkToolbar     ::shadow_type       = none # removes shadows? 

  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 2  # was 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 27
  
  GtkOptionMenu::indicator_size			= { 7, 6 }
  GtkOptionMenu::indicator_spacing		= { 6, 9, 5, 5 }
  
  xthickness = 0
  ythickness = 0

  fg[NORMAL]       	= "#101010"
  fg[ACTIVE]       	= "#353535"  #tab no seleccionado
  fg[PRELIGHT]     	= "#000000"
  fg[SELECTED]     	= "#000000"
  fg[INSENSITIVE]  	= "#9B9B9B"

  bg[NORMAL]       	= "#f5f5f5"
  bg[ACTIVE]            = "#E0E0E0"
  bg[PRELIGHT]     	= "#f0f0f0"
  bg[SELECTED]     	= "#606060"
  bg[INSENSITIVE]  	= "#e0e0e0"

  base[NORMAL]     	= "#ffffff" #fondo gedit
  base[ACTIVE]     	= "#777777" #fondo selección no activa
  base[PRELIGHT]   	= "#000000" 
  base[SELECTED]	= "#202020" #selección
  base[INSENSITIVE]	= "#e0e0e0" #campos deshabilitados

  text[NORMAL]     	= "#101010"
  text[ACTIVE]		= "#ffffff"  #text selección no actual
  text[PRELIGHT]   	= "#353535"
  text[SELECTED]   	= "#ffffff"  #text selección actual
  text[INSENSITIVE]	= "#9B9B9B"

  engine "murrine" 
  {
	 menuitemstyle = 0 # 0 = flat, 1 = glassy, 2 = striped
roundness = 0 # 0 = squared, 1 = old default, more will increase roundness
	 scrollbar_color     = "#e8e8e8"
    contrast          	= 1.0
    glazestyle = 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style
	 menubarstyle = 0 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	 menubaritemstyle = 1 # 0 = menuitem look, 1 = button look
	 listviewheaderstyle = 1 # 0 = flat, 1 = glassy
    animation = TRUE # FALSE = disabled, TRUE = enabled
  }
}


style "theme-wide" = "theme-default"
{
  xthickness = 1
  ythickness = 1
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
}

style "theme-button" = "theme-wider"
{
 bg[NORMAL]   	   = "#e8e8e8"
 bg[ACTIVE]	   = "#d4d4d4"
}

style "theme-range" = "theme-default"
{
  xthickness = 0
  ythickness = 0
  
    bg[NORMAL]   	   = "#f0f0f0"
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]   	   = "#ffffff"
  bg[SELECTED]   	   = "#1A1B1C"
  
}

style "theme-tasklist" = "theme-default"
{
  xthickness = 5
  ythickness = 3
}

style "theme-menu" = "theme-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL]		= "#1A1B1C" #cambia de color el separador
  fg[PRELIGHT] 		= "#ffffff" 
#  fg[NORMAL]   		= "#ffffff" # "#000000" if you want more contrast
  base[NORMAL]        = "#1A1B1C"
}

style "theme-menu-item" = "theme-default"
{
  xthickness = 2  
  ythickness = 0  # was 3

  fg[NORMAL]           = "#ffffff"  
  fg[PRELIGHT]         = "#ffffff" 
  fg[INSENSITIVE]      = "#aaaaaa"

  text[NORMAL]           = "#ffffff"
  text[PRELIGHT]           = "#ffffff" 

  bg[NORMAL]       	= "#1A1B1C"
  base[NORMAL]        = "#ffffff"
  


}

style "theme-menubar"
{
  xthickness = 2
  ythickness = 2
}

style "theme-menubar-item" = "theme-menu-item"
{
  fg[NORMAL]   		= "#101010" # "#000000" if you want more contrast
  fg[PRELIGHT] 		= "#FFFFFF"
  bg[PRELIGHT]           = "#1A1B1C"
  
  text[NORMAL] = "#101010"
}

style "theme-tree" = "theme-default"
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL]   	   = "#e8e8e8"
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] 			= "#101010"
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] 		= "#ffffff"
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 0
  ythickness = 0
  bg[SELECTED]  = "#e5e5e5"
  bg[NORMAL]    = "#cccccc"
  fg[PRELIGHT]  = "#101010"
  base[SELECTED]   = "#ffffff"

}


style "metacity-frame" = "theme-default"
{
  bg[SELECTED]  = "#000000"

  # Focused title text color
  fg[SELECTED]  = "#101010"
}
class "MetaFrames" 	  style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

# widget styles
class "GtkWidget"      style "theme-default"
#class "GtkSpinButton"  style "theme-default"
#class "GtkButton"      style "theme-button"
class "GtkScale"       style "theme-range"
#class "GtkCombo"       style "theme-button"
#class "GtkRange"       style "theme-wide"
class "GtkFrame"       style "theme-wide"
class "GtkMenu"        style "theme-menu"
#class "GtkEntry"       style "theme-wider"
#class "GtkMenuItem"    style "theme-menu-item"
#class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "*MenuBar*"      style "theme-menubar"

#widget_class "*MenuItem.*" style "theme-menu-item"
widget_class "*MenuBar.*"  style "theme-menubar-item"

# combobox stuff
#widget_class "*.GtkComboBox.GtkButton" style "theme-combo"
#widget_class "*.GtkCombo.GtkButton"    style "theme-combo"

# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "theme-tasklist"
widget "gtk-tooltips" 				    style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "theme-tree"
widget_class "*.GtkCTree.GtkButton" 	style "theme-tree"
widget_class "*.GtkList.GtkButton" 	style "theme-tree"
widget_class "*.GtkCList.GtkButton" 	style "theme-tree"
widget_class "*.GtkFrame.GtkLabel" 	style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"
```

---

