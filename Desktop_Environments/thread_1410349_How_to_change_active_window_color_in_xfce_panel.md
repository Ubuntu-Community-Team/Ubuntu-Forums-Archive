---
title: "How to change active window color in xfce panel?"
date: 2010-02-18
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-18
Hi,
i am using one gtk theme - *bsm compact silver dark*. 
Want to change just one thing-the color that indicate active/maximized window in xfce panel. Just to difference active window. 
I have no idea what should i change, but i think that i had to modify gtkrc file (as i did at the end to modify desktop icons).

So, if anyyone knows which part i need to change to have new color for active/maximized window, i will be grateful.

I added here the picture of my panel-chrome is maximized, but you can see no difference on screen. And bellow is my gtkrc:

```
# Author: BSM

# These are the defined colors for the theme, you can change them in GNOME's appearance preferences.
#gtk_color_scheme = "fg_color:#101010101010\nbg_color:#ebebebebebeb\ntext_color:#1a1a1a1a1a1a\n base_color:#ffffffffffff\n selected_fg_color:#000000000000\n selected_bg_color:#60c4af9dd709\n tooltip_fg_color:#000000000000\n tooltip_bg_color:#f5f5f5f5b5b5"
gtk_color_scheme = "fg_color:#101010101010\nbg_color:#ebebebebebeb\ntext_color:#1a1a1a1a1a1a\nbase_color:#ffffffffffff\nselected_fg_color:#000000000000\nselected_bg_color:#A9A9A9\ntooltip_fg_color:#000000000000\ntooltip_bg_color:#f0f0f0"
#########
# ICONS 
#########
#gtk-icon-sizes	= "gtk-button=16,16" # This makes button icons smaller.
gtk-icon-sizes	= "gtk-large-toolbar=16,16:gtk-small-toolbar=16,16:panel-menu=16,16:gtk-button=16,16" # This enables "compact-mode".
gtk-button-images	= 0 # Enables or disables icons on buttons (OS X-like).
#gtk-menu-popup-delay	= 1 # Makes menus pop up faster! Set to 1 instead of 0 to avoid Banshee 1 bug.

##########
# PANELS 
##########
include "panel.rc" # This includes the file that handles panel theming. Gradient panel backgrounds are enabled by default. Please edit panel.rc or comment out this line to remove gradient panels. You can also choose one of the following lines instead, for different-sized panels.:

#include "panel28.rc"	# Use this instead for 28px gradient panels.
#include "panel32.rc"	# Use this instead for 32px gradient panels.
#include "panel40.rc"	# Use this instead for 40px gradient panels.
#include "panel48.rc"	# Use this instead for 48px gradient panels.

# The following lines make panel-menu-applet and gimmie applet's text bold.
style "bold-panel-menu"
{
#font_name = "Bold"
}

widget "*Panel*MenuBar*" style "bold-panel-menu"  
widget "*gimmie*" style "bold-panel-menu"

##########################
# GENERAL THEME SETTINGS 
##########################
style "clearlooks-default"
{
	GtkButton      ::child-displacement-x	= 0 # Pressed button icon displacement.
	GtkButton      ::child-displacement-y	= 0 # Pressed button icon displacement.
	GtkButton      ::default-border		= { 0, 0, 0, 0 }
	GtkCheckButton ::indicator-size		= 12 # Size for check buttons.
	GtkRadioButton ::indicator-size		= 12 # Size for radio buttons.
	GtkPaned       ::handle-size		= 3 # Width of handles.

	GtkRange       ::trough-border		= 0
	GtkRange       ::slider-width		= 12
	GtkRange       ::stepper-size		= 12

	GtkScale       ::slider-length		= 24 # Length of sliders.
	GtkScale       ::trough-side-details	= 1
	GtkScrollbar   ::min-slider-length	= 30 # Min. length of scrollbars.

	GtkMenuBar     ::internal-padding	= 0
	GtkExpander    ::expander-size		= 10
	GtkToolbar     ::internal-padding	= 0 # Toolbar padding.
	GtkTreeView    ::expander-size		= 12
	GtkTreeView    ::vertical-separator	= 0

	GtkMenu        ::horizontal-padding	= 0
	GtkMenu        ::vertical-padding	= 0

	WnckTasklist   ::fade-overlay-rect	= 0

	GtkButton      ::focus-padding		= 0 # This can give you a more compact appearance.
  	GtkScrolledWindow ::scrollbar-spacing	= 1 # This sets the spacing between scrollbars.
	GtkTreeView::odd_row_color		= mix(0.98, shade (0.93,@base_color), @selected_bg_color) # This sets the color for odd row items.

	GtkEntry::honors-transparent-bg-hint	= 1

#	Uncomment one or both of the following for flat/unified menus or toolbars:
#	GtkToolbar     ::shadow-type		= GTK_SHADOW_NONE  # Makes toolbars flat and unified.
#	GtkMenuBar     ::shadow-type		= GTK_SHADOW_NONE  # Makes menus flat and unified.

	xthickness = 1
	ythickness = 1

	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]	  = @selected_bg_color  # Color for selected items.
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.90, @bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (1.35, @selected_bg_color)
	base[SELECTED]    = shade (1.25, @selected_bg_color)  # Color for selected base items.
	base[INSENSITIVE] = @bg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)

	engine "clearlooks" 
	{
		reliefstyle	= 1 # 0 makes buttons/widgets less raised.
		menubarstyle	= 0 # Gradient menubar, use tweak in line 66 for flat menubars.
		toolbarstyle	= 0 # 0 makes bad toolbars flat.
		animation	= TRUE # FALSE disables progressbar animations.
		style		= GUMMY # Could also be set to GLOSSY.
		radius		= 1.0 # Roundness of widgets.
		hint		= "use-hints" # Set a hint to disable backward compatibility fallbacks.
	}
#	bg[NORMAL] = "#FF00FF"
#	bg[PRELIGHT] = "#FF00FF"
#	bg[SELECTED] = "#FF00FF"
#	bg[INSENSITIVE] = "#FF00FF"
#	bg[ACTIVE] = "#FF00FF"

#	base[NORMAL]      = "#FF00FF"
#	base[PRELIGHT]    = "#FF00FF"
#	base[SELECTED]    = "#FF00FF"
#	base[INSENSITIVE] = "#FF00FF"
#	base[ACTIVE]      = "#FF00FF"

}

#################
# THEME MODULES 
#################
style "evolution-hack" = "clearlooks-default" # Hacks for Evolution Mail.
{	
	bg[NORMAL]	= shade (1.04, @bg_color) # Color for evo treeview headers.
	bg[PRELIGHT]	= shade (1.08, @bg_color) # Color for evo treeview header prelight.
	bg[ACTIVE]	= shade (0.90, @bg_color) # Color for unfocused evo selected items.
	bg[SELECTED]	= shade (1.25, @selected_bg_color) # Color for evo selected items.
	fg[ACTIVE]      = @selected_fg_color # Color for evo active text.
	fg[SELECTED]    = @selected_fg_color # Color for evo selected text.
}

style "clearlooks-wide"
{
	xthickness = 2 # Can't change, or clowns will eat you.
	ythickness = 2 # Can't change, or clowns will eat you.
}

style "clearlooks-wider"
{
	xthickness = 3 # Can't change, or clowns will eat you.
	ythickness = 3 # Can't change, or clowns will eat you.
	engine "clearlooks" 
	{
		radius = 1.1 # Firefox > 3.0.6 location bar's bug fix
	}
}

style "clearlooks-button" = "clearlooks-wider"
{
	#xthickness = 1 # Can't change, or clowns will eat you.
	#ythickness = 1 # Can't change, or clowns will eat you.
	bg[NORMAL]	= shade (1.04, @bg_color) # Color for buttons.
	bg[PRELIGHT]	= shade (1.08, @bg_color) # Color for button-prelight.
	bg[ACTIVE]	= shade (0.85, @bg_color) # Color for pressed-buttons.
}

style "clearlooks-notebook-bg"
{
	bg[NORMAL]	= shade (1.04, @bg_color) # Tab background.
	bg[ACTIVE]	= shade (0.94, @bg_color) # Unfocused tab background.
}

style "clearlooks-notebook" = "clearlooks-notebook-bg"
{
	xthickness = 1 # Width of tabs and notebook borders.
	ythickness = 1 # Height of tabs and notebook borders.
}

style "clearlooks-menu" = "clearlooks-wider"
{
	bg[NORMAL] = shade (1.05, @bg_color)  # Color of menu background.
	engine "clearlooks" 
	{
		radius = 1.0 # Roundness of menu items.
	}
}

style "clearlooks-menu-item" = "clearlooks-wider"
{
	fg[PRELIGHT]	= @selected_fg_color  # Color of selected menu item text.
	bg[SELECTED]	= shade (1.25, @selected_bg_color)  # Color of menu items.
	bg[PRELIGHT]	= shade (1.25, @selected_bg_color)  # Color of menu items.
}

style "clearlooks-separator-menu-item"
{
	xthickness = 1
	ythickness = 1

#  Code for pixmap menu separators.
  engine "pixmap"
  {
    image
    {
      function	  = HLINE
      recolorable         = TRUE
      file	  = "Menu-Menubar/menu-line.png"
      border	  = { 1, 1, 1, 1 }
      stretch	  = TRUE
    }
}
}

style "clearlooks-menubar"
{
	xthickness = 1
	ythickness = 1
	engine "clearlooks"
	{
		hint	= "menubar"
	}
}

style "clearlooks-treeview"
{
	bg[SELECTED]	= shade (1.25, @selected_bg_color)  # Color workaround for Banshee 1.0.

	GtkTreeView::odd_row_color = shade(1.03,@tooltip_bg_color)
	GtkTreeView::even_row_color = @tooltip_bg_color

#	GtkTreeView::odd_col_color = shade(0.95,@tooltip_bg_color)
#	GtkTreeView::even_col_color = @tooltip_bg_color

  	engine "clearlooks" 
	{
		hint = "treeview"
		radius = 0.0  # This makes treeview progressbars square.
	}
}

style "clearlooks-treeview-header" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 1
	bg[NORMAL]	= shade (1.04, @bg_color)  # Color for treeview headers.
	bg[PRELIGHT]	= shade (1.08, @bg_color)  # Color for treeview header prelight.
	bg[ACTIVE]	= shade (0.85, @bg_color)  # Color for pressed-treeview.
	engine "clearlooks" {
		hint = "treeview-header"
	}
}

style "clearlooks-frame-title"
{
	fg[NORMAL]	= lighter (@fg_color)
}

style "clearlooks-tooltips" = "clearlooks-wider"
{
	bg[NORMAL]	= @tooltip_bg_color
	fg[NORMAL]	= @tooltip_fg_color
}

style "metacity-frame" = "clearlooks-default"
{
#	bg[SELECTED]	= @selected_bg_color  # Color for metacity borders.
}

style "clearlooks-progressbar"
{
	xthickness = 1
	ythickness = 1
	fg[PRELIGHT]	= @base_color  # Progressbar prelighted text.
	engine "clearlooks"
	{
		radius	= 1.0  # Roundness of progressbars.
		hint	= "progressbar"
	}
}

style "clearlooks-statusbar"
{
	engine "clearlooks"
	{
		hint	= "statusbar"
	}
}

style "clearlooks-comboboxentry"
{
	engine "clearlooks"
	{
		hint	= "comboboxentry"
	}
}

style "clearlooks-spinbutton"
{
	bg[NORMAL]   = shade (1.04, @bg_color) # Color for spinbuttons.
	bg[PRELIGHT]   = shade (1.08, @bg_color) # Color for spinbutton prelight.
	bg[ACTIVE]   = shade (0.85, @bg_color) # Color for pressed-spinbuttons.
	engine "clearlooks"
	{
		hint	= "spinbutton"
	}
}

style "clearlooks-scale" = "clearlooks-button"
{
	bg[NORMAL]	= shade (1.04, @bg_color) # Color for sliders.
	bg[PRELIGHT]	= shade (1.08, @bg_color) # Color for slider prelight.
	bg[ACTIVE]	= shade (0.85, @bg_color) # Color for pressed-sliders.
	engine "clearlooks"
	{
		hint	= "scale"
	}
}

style "clearlooks-hscale" = "clearlooks-scale"
{
	engine "clearlooks"
	{
		hint	= "hscale"
	}
}

style "clearlooks-vscale" = "clearlooks-scale"
{
	engine "clearlooks"
	{
		hint	= "vscale"
	}
}

style "clearlooks-nautilus-location" # Workaround for nautilus' messages.
{
	bg[NORMAL]	= shade (1.25, @selected_bg_color)
}

style "clearlooks-radiocheck" = "clearlooks-default"
{
	text[NORMAL]	= shade (0.8, @selected_bg_color) # Color for checks/radio items.
#	bg[SELECTED]	= lighter (@selected_bg_color) # Color for prelight of check/radio buttons.
}

##############
# SCROLLBARS
##############
style "clearlooks-scrollbar"
{
	bg[NORMAL]	= shade (1.04, @bg_color) # Color for non-colored scrollbars.
	bg[PRELIGHT]	= shade (1.08, @bg_color) # Color for scrollbar prelight? (probably obsolete)
	bg[ACTIVE]	= shade (0.85, @bg_color) # Color for pressed scrollbar buttons.
#	bg[SELECTED]	= @selected_bg_color # You can change the color of colorized scrollbars here.
	engine "clearlooks"
	{
#		colorize_scrollbar	= TRUE # Uncommenting this gives you colorful scrollbars.
		radius	= 1.0  # Roundness of scrollbars.
		hint	= "scrollbar"
		style = GLOSSY
	}
}

style "clearlooks-hscrollbar" = "clearlooks-scrollbar"
{
	engine "clearlooks"
	{
		hint	= "hscrollbar"
	}
}

style "clearlooks-vscrollbar" = "clearlooks-scrollbar"
{
	engine "clearlooks"
	{
		hint	= "vscrollbar"
	}
}

############
# TOOLBARS
############
#Gradient toolbars are enabled for this theme.

style "clearlooks-toolbar" = "clearlooks-default"
{
	bg[NORMAL]   = shade (0.965, @bg_color)  # Darkens gradient toolbars to match with unified metacity theme.
	engine "clearlooks"
	{
		toolbarstyle = 0
	}

}

style "clearlooks-evo-new-button-workaround"
{
	bg[NORMAL]   = shade (0.965, @bg_color)
	engine "clearlooks"
	{
		toolbarstyle = 0
	}
}
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "clearlooks-evo-new-button-workaround"

class "GtkHandleBox" style "clearlooks-toolbar"

#########################################
# Matches
#########################################

# Clearlooks default style is applied to every widget.
class "GtkWidget"    style "clearlooks-default"

# Increase the x/ythickness in some widgets.
class "GtkToolbar"   style "clearlooks-toolbar" 
class "GtkFrame"     style "clearlooks-wide"
class "GtkEntry"     style "clearlooks-wider"
class "MetaFrames"   style "metacity-frame"
class "GtkSeparator" style "clearlooks-wide"
class "GtkWindow"      style "metacity-frame"
class "GtkCalendar"  style "clearlooks-wide"

class "GtkSpinButton"  style "clearlooks-spinbutton"
class "GtkScale"       style "clearlooks-scale"
class "GtkVScale"      style "clearlooks-vscale"
class "GtkHScale"      style "clearlooks-hscale"
class "GtkScrollbar"   style "clearlooks-scrollbar"
class "GtkVScrollbar"  style "clearlooks-vscrollbar"
class "GtkHScrollbar"  style "clearlooks-hscrollbar"

class "GtkRadio*"	style "clearlooks-radiocheck"
class "GtkCheck*"	style "clearlooks-radiocheck"

# General matching following, the order is choosen so that the right styles override each other eg. progressbar needs to be more important then the menu match.

# This is not perfect, it could be done better (That is modify *every* widget in the notebook, and change those back that we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"     style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>"  style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkLayout>"       style "clearlooks-notebook-bg"
widget_class "*.GtkNotebook.*.GtkViewport"	style "clearlooks-notebook"

widget_class "*<GtkButton>"      style "clearlooks-button"
widget_class "*<GtkNotebook>"    style "clearlooks-notebook"
widget_class "*<GtkStatusbar>*"  style "clearlooks-statusbar"

widget_class "*<GtkComboBoxEntry>*" style "clearlooks-comboboxentry"
widget_class "*<GtkCombo>*"         style "clearlooks-comboboxentry"

widget_class "*<GtkMenuBar>*"           style "clearlooks-menubar"
widget_class "*<GtkMenu>*"              style "clearlooks-menu"
widget_class "*<GtkMenuItem>*"          style "clearlooks-menu-item"
widget_class "*<GtkSeparatorMenuItem>*" style "clearlooks-separator-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>" style "clearlooks-frame-title"
widget_class "*.<GtkTreeView>*"        style "clearlooks-treeview"

widget_class "*<GtkProgressBar>"       style "clearlooks-progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" style "clearlooks-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"    style "clearlooks-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"     style "clearlooks-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"    style "clearlooks-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"    style "clearlooks-treeview-header"
widget_class "*.ETree.ECanvas"    style "clearlooks-treeview-header"
widget_class "*GtkCTree*"	style "evolution-hack"
widget_class "*GtkList*"	style "evolution-hack"
widget_class "*GtkCList*"	style "evolution-hack"
widget_class "*.ETree.*"	style "evolution-hack"
widget_class "*EInfoLabel*"	style "evolution-hack"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" style "clearlooks-tooltips"

###################################################
# SPECIAL CASES AND WORKAROUNDS
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "clearlooks-nautilus-location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that the work around assumes that the combobox is _not_ in appears-as-list mode.
# This style does not affect GtkComboBoxEntry, it does have an effect on comboboxes in appears-as-list mode though.
style "clearlooks-text-is-fg-color-workaround"
{
	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>"   style "clearlooks-text-is-fg-color-workaround"

style "clearlooks-menuitem-text-is-fg-color-workaround"
{
	text[NORMAL]        = @fg_color
	text[PRELIGHT]      = @selected_fg_color
	text[SELECTED]      = @selected_fg_color
	text[ACTIVE]        = @fg_color
	text[INSENSITIVE]   = darker (@bg_color)
}
widget "*.gtk-combobox-popup-menu.*"   style "clearlooks-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the base color set.
style "clearlooks-fg-is-text-color-workaround"
{
	fg[NORMAL]      = @text_color
	fg[PRELIGHT]    = @text_color
	fg[ACTIVE]      = @selected_fg_color
	fg[SELECTED]    = @selected_fg_color
	fg[INSENSITIVE] = darker (@bg_color)
}
widget_class "*<GtkListItem>*" style "clearlooks-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree.
# Only match GtkCList and not the parent widgets, because that would also change the headers.
widget_class "*<GtkCList>" style "clearlooks-fg-is-text-color-workaround"
widget_class "*<EelEditableLabel>" style "clearlooks-fg-is-text-color-workaround"

# The answer to the ultimate question of life, the universe, and everything is 42.

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 00

	base[NORMAL] = "#000000"
	base[SELECTED] = "#fdf6f6"
	base[ACTIVE] = "#fdf6f6"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

---

### Post by Hero of Time on 2010-02-18
Check the panel.rc file and look for bg[ACTIVE]. Change that value and the button will change colour.

---

### Post by vickoxy on 2010-02-19
"Hero of Time" - thanks a lot-that is almost perfect.

Still i want to change only font color-i will tweak little bit there, but i am grateful for this tipp because this is alo very good solution!
:popcorn:

---

### Post by vickoxy on 2010-02-19
I think that font colors are not handled in panel.rc-but can not find anything that should point it in gtkrc-i mean, i found colors, but have no idea what to change.

---

### Post by Hero of Time on 2010-02-19
It replaces more than just the panel text colour of the active item, but fg[ACTIVE] is what makes it change.

---

### Post by vickoxy on 2010-02-19
> **Hero of Time said:**
> It replaces more than just the panel text colour of the active item, but fg[ACTIVE] is what makes it change.

Well, i changed 

```
fg[ACTIVE]	= lighter (@selected_bg_color)  # Makes active text colored.
```
to

```
fg[ACTIVE]	= "#5d9cc4" lighter (@selected_bg_color)  # Makes active text colored.
```

but i got all panel colored in grey:

---

### Post by vickoxy on 2010-02-19
Ok-another question-i installed one another theme and want to make the same thing with it, but can´t success.
panel.rc
```
#################### PANEL BACKGROUND #########################xx

style "panelbg"
{
  
 xthickness            			= 0
  ythickness            			= 0
bg_pixmap[NORMAL]					= "Panel/panel-bg.png"
bg_pixmap[SELECTED]					= "Panel/panel-bg.png"
bg_pixmap[INSENSITIVE]					= "Panel/panel-bg.png"
bg_pixmap[PRELIGHT]					= "Panel/panel-bg.png"
bg_pixmap[ACTIVE]					= "Panel/panel-bg.png"
}

class "*Panel*" style "panelbg"
widget_class "*notif*" style "panelbg"
widget_class "*Notif*" style "panelbg"
widget_class "*Tray*" style "panelbg"
widget_class "*tray*" style "panelbg"

##################### PANEL BUTTONS ###############################

style "panelbuttons"
{

  fg[NORMAL]        = "#606060" # very dark brown
  fg[PRELIGHT]      = "#c0c0c0" # text on buttons (hover)
  fg[ACTIVE]        = "#909090" # text on unfocused tabs
  bg[NORMAL]        = "#222222" #Panel bg color
  xthickness            			= 2
  ythickness            			= 1

	GtkWidget::focus_padding = 2

	engine "pixmap" {
      
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state			= NORMAL
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
		}
		
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state			= PRELIGHT
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
		}

		image
		{
			function        	= BOX
			recolorable     	= TRUE
			shadow			= OUT
			state			= PRELIGHT
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
			#overlay_file   	= "panelbutton1.png"
			#overlay_border		= { 4, 4, 4, 4 }
			#overlay_stretch	= TRUE
		}
		
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			shadow			= IN
			state			= PRELIGHT
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
			#overlay_file     	= "panelbutton1.png"
			#overlay_border		= { 4, 4, 4, 4 }
			#overlay_stretch	= TRUE
		}
		
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state			= ACTIVE
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
		}  
		image
		{
			function        	= BOX
			recolorable     	= TRUE
			state			= INSENSITIVE
			file            	= "Panel/panelbutton1.png"
			border          	= { 4, 4, 4, 4 }
			stretch         	= TRUE
		}  
/*    		image
    		{
      		function			= HANDLE
      		recolorable			= TRUE
      		overlay_file			= "Panel/handle-v.png"
      		overlay_stretch	= FALSE
      		orientation			= VERTICAL
    		}
    		image
    		{
      		function			= HANDLE
      		overlay_file			= "Panel/handle-h.png"
      		overlay_stretch 		= FALSE
     		orientation			= HORIZONTAL
   		}
*/
	}

}

widget "*PanelWidget*" style "panelbuttons"
widget "*PanelApplet*" style "panelbuttons"

widget_class "*Panel*GtkToggleButton*" style "panelbuttons"

#widget_class "*Panel*GtkHandleBox" style "panelbuttons"
#widget_class "*Panel*GtkPaned" style "panelbuttons"

widget_class "*Panel*GtkButton" style "panelbuttons"
widget_class "*PanelButton*." style "panelbuttons"

widget_class "*Panel*" style "panelbuttons"
#class "*notif*" style "panelbuttons"
#class "*Notif*" style "panelbuttons"
#class "*Tray*" style "panelbuttons"
#class "*tray*" style "panelbuttons"

```

I added line bg[ACTIVE] with wanted color-but nothing.

Any idea?

Want  to have better marked/different font/background color for active item in panel

---

### Post by vickoxy on 2010-02-19
> **Hero of Time said:**
> It replaces more than just the panel text colour of the active item, but fg[ACTIVE] is what makes it change.

You were right: i should actually make this-
```
fg[ACTIVE]	= "#5d9cc4" # Makes active text colored.
```

So, now is my theme fixed.

Still-if anyone know how to fix the another one-**dyne dark**

i repeat question:
Want to have better marked/different font/background color for active item in panel

panel.rc is in previous post...

SOLVED: changed in new theme fg active color.
Thanks **Hero of Time**

---

