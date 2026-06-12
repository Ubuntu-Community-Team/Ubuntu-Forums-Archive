---
title: "help with gtk-2.0 gtkrc file"
date: 2010-01-06
forum: Desktop Environments
---

### Post by Strongman332 on 2010-01-06
Basically I want to change the color of pop-up menus context menus ect.

but I don't know how.

can any one help me with this?

edit: I would also like to change the panel colors. i know you can do this inside of panel options but it doesn't look very good

```
# Fresh (Dark) 2.1 by Henrique Alves <hcarvalhoalves@gmail.com>
# http://hcalves.deviantart.com

# Set GtkSettings color scheme property.
# This can be overriden (via an xsetting) with eg. the gnome-appearance-properties.
gtk_color_scheme = "fg_color:#333\nbg_color:#dedede\nbase_color:#fff\ntext_color:#ffffff\nselected_bg_color:#61758d\nselected_fg_color:#f2f9ff\ntooltip_bg_color:#fff4c8\ntooltip_fg_color:#000"

gtk-icon-sizes = "gtk-button=16,16"
#gtk-button-images = 0

style "clearlooks-default"
{
	########
	# Style Properties
	########
	GtkButton      ::child-displacement-x = 1
	GtkButton      ::child-displacement-y = 1
	GtkButton      ::default-border       = { 0, 0, 0, 0 }
	GtkCheckButton ::indicator-size       = 14

	GtkPaned       ::handle-size          = 6

	GtkRange       ::trough-border        = 0
	GtkRange       ::slider-width         = 16
	GtkRange       ::stepper-size         = 16

	GtkScale       ::slider-length        = 28
	GtkScale       ::trough-side-details  = 1
	GtkScrollbar   ::min-slider-length    = 30
    GtkVScrollbar  ::has-backward-stepper = 0
    GtkVScrollbar  ::has-secondary-backward-stepper = 1
    GtkScrolledWindow::scrollbar-spacing  = 0

	GtkMenuBar     ::internal-padding     = 2
	GtkExpander    ::expander-size        = 16
	GtkToolbar     ::internal-padding     = 1
	GtkTreeView    ::expander-size        = 14
	GtkTreeView    ::vertical-separator   = 0

	GtkMenu        ::horizontal-padding   = 0
	GtkMenu        ::vertical-padding     = 0

	# Glow the tasklist by changing the color, instead of overlaying it with a rectangle
	# WnckTasklist   ::fade-overlay-rect    = 0

	#flat menubars and toolbar
	#GtkMenuBar::shadow_type = GTK_SHADOW_NONE
    #GtkToolbar::shadow_type = GTK_SHADOW_NONE

	xthickness = 1
	ythickness = 1

	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]	  = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (0.9, @selected_bg_color)
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @bg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)

	engine "clearlooks"
	{
		colorize_scrollbar = FALSE
		reliefstyle        = 1
		menubarstyle       = 2      # 0 = flat, 1 = sunken, 2 = flat gradient
		toolbarstyle       = 1      # 0 = flat, 1 = enable effects
		animation          = TRUE
        radius             = 3.0
		style              = GUMMY

		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "clearlooks-wide"
{
	xthickness = 2
	ythickness = 2
}

style "clearlooks-wider"
{
	xthickness = 3
	ythickness = 3
}

style "clearlooks-entry" = "clearlooks-wider"
{
    engine "clearlooks" {
        contrast = 0.75
    }
}

style "clearlooks-button"
{
	xthickness   = 3
	ythickness   = 3

	bg[NORMAL]   = shade (0.90, @bg_color)
	bg[PRELIGHT] = shade (1.10, @bg_color)
	bg[ACTIVE]   = shade (0.85, @bg_color)

    engine "clearlooks" {
        contrast = 0.9
    }
}

style "clearlooks-notebook-bg" = "clearlooks-wider"
{
    bg[NORMAL] = shade (1.10, @bg_color)
    bg[ACTIVE] = shade (0.9, @bg_color)

	engine "clearlooks" {
        hint = "notebook"
		contrast = 0.9
	}
}

style "clearlooks-notebook" = "clearlooks-notebook-bg"
{
    engine "clearlooks" {
        hint = "notebook"
    }
}

style "clearlooks-tasklist"
{
	xthickness = 5
	ythickness = 3
}

style "clearlooks-panel"{
	fg[NORMAL] = shade (1.1, @bg_color)
    bg[NORMAL] = shade (0.2, @bg_color)
	bg[PRELIGHT] = @selected_bg_color
    # Menu
    fg[PRELIGHT] = @selected_fg_color
    bg[SELECTED] = @selected_bg_color
}

style "clearlooks-menu" = "clearlooks-panel"
{
	xthickness = 0
	ythickness = 0

    # Radius of the menu items (inside menus)
	engine "clearlooks"
	{
		radius = 0.0
	}
}

style "clearlooks-menu-item" = "clearlooks-panel"
{
	xthickness = 3
	ythickness = 3
}

style "clearlooks-separator-menu-item" = "clearlooks-panel"
{
	GtkSeparatorMenuItem::horizontal-padding = 0
	# We are setting the desired height by using wide-separators
	# There is no other way to get the odd height ...
	GtkWidget::wide-separators = 1
	GtkWidget::separator-width = 1
	GtkWidget::separator-height = 5
	xthickness = 1
	ythickness = 0
}

style "clearlooks-treeview"
{
	engine "clearlooks" {
		hint = "treeview"
		contrast = 1.0
	}
}

# Based on the default style so that the colors from the button
# style are overriden again.
style "clearlooks-treeview-header" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 1

	engine "clearlooks" {
		hint = "treeview-header"
		contrast = 1.0
	}
}

style "clearlooks-frame-title"
{
	fg[NORMAL] = lighter (@fg_color)
}

style "clearlooks-tooltips"
{
	xthickness = 4
	ythickness = 4

	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
}

style "clearlooks-progressbar"
{
	xthickness = 1
	ythickness = 1

	fg[PRELIGHT] = @selected_fg_color

	engine "clearlooks"
	{
		# Explicitly set the radius, for progress
		# bars inside menuitems
		radius = 0.0
		hint	= "progressbar"
	}
}

style "clearlooks-statusbar"
{
    xthickness = 3
    ythickness = 3
    engine "clearlooks"
	{
		hint	= "statusbar"
	}
}

style "clearlooks-comboboxentry"
{
	# NOTE:
	# If you set the appears-as-list option on comboboxes in the theme
	# you should set this hint on the combobox instead.
	engine "clearlooks"
	{
		hint	= "comboboxentry"
	}
}

style "clearlooks-spinbutton"
{
	engine "clearlooks"
	{
		hint	= "spinbutton"
		contrast = 0.85
	}
}

style "clearlooks-scale"
{
	engine "clearlooks"
	{
		hint	= "scale"
	}
}

style "clearlooks-hscale"
{
	engine "clearlooks"
	{
		hint	= "hscale"
	}
}

style "clearlooks-vscale"
{
	engine "clearlooks"
	{
		hint	= "vscale"
	}
}

style "clearlooks-scrollbar"
{
    bg[NORMAL] = shade(1.1, @bg_color)
    bg[PRELIGHT] = shade(1.2, @bg_color)
	engine "aurora"
	{
	  curvature = 6.0
	}
}


style "clearlooks-menubar" = "clearlooks-panel"
{
    xthickness = 2
    ythickness = 2
	engine "clearlooks"
	{
		hint	= "menubar"
	}
}

style "clearlooks-low"
{
	engine "clearlooks"
	{
		contrast = 0.85
	}
}

style "clearlooks-nautilus-location"
{
	bg[NORMAL] = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}




#########################################
# Matches
#########################################

# Clearlooks default style is applied to every widget
class "GtkWidget"    style "clearlooks-default"

# Increase the x/ythickness in some widgets
class "GtkToolbar"   style "clearlooks-default"
class "GtkRange"     style "clearlooks-wide"
class "GtkFrame"     style "clearlooks-wide"
class "GtkSeparator" style "clearlooks-wide"

class "GtkEntry"     style "clearlooks-entry"
class "GtkSpinButton"  style "clearlooks-spinbutton"
class "GtkScale"       style "clearlooks-scale"
class "GtkVScale"      style "clearlooks-vscale"
class "GtkHScale"      style "clearlooks-hscale"
class "GtkScrollbar"   style "clearlooks-scrollbar"
class "GtkVScrollbar"  style "clearlooks-scrollbar"
class "GtkHScrollbar"  style "clearlooks-scrollbar"

# General matching following, the order is choosen so that the right styles override each other
# eg. progressbar needs to be more important then the menu match.

#Panel
widget "*PanelWidget*" 					style "clearlooks-panel"
widget "*PanelApplet*" 					style "clearlooks-panel"
widget "*fast-user-switch*"				style "clearlooks-panel" # Workaround for Fast User Switch applet
class "PanelApp*" 					style "clearlooks-panel"
class "PanelToplevel*" 					style "clearlooks-panel"


# This is not perfect, it could be done better
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"     style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>"  style "clearlooks-notebook-bg"
widget_class "*<GtkNotebook>*<GtkLayout>"       style "clearlooks-notebook-bg"

widget_class "*<GtkButton>"      style "clearlooks-button"
widget_class "*<GtkNotebook>"    style "clearlooks-notebook"
widget_class "*<GtkStatusbar>*"  style : highest "clearlooks-statusbar"

widget_class "*<GtkComboBoxEntry>*" style "clearlooks-comboboxentry"
widget_class "*<GtkCombo>*"         style "clearlooks-comboboxentry"

widget_class "*<GtkMenu>*"              style "clearlooks-menu"
widget_class "*<GtkMenuItem>*"          style "clearlooks-menu-item"
widget_class "*<GtkMenuBar>*"           style "clearlooks-menubar"
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
# Special cases and work arounds
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "clearlooks-nautilus-location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
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
	text[NORMAL]        = @bg_color
	text[PRELIGHT]      = @selected_fg_color
	text[SELECTED]      = @selected_fg_color
	text[ACTIVE]        = @bg_color
	text[INSENSITIVE]   = darker (@bg_color)
}
widget "*.gtk-combobox-popup-menu.*"   style "clearlooks-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the
# base color set.
style "clearlooks-fg-is-text-color-workaround"
{
	fg[NORMAL]      = @text_color
	fg[PRELIGHT]    = @text_color
	fg[ACTIVE]      = @selected_fg_color
	fg[SELECTED]    = @selected_fg_color
	fg[INSENSITIVE] = darker (@bg_color)
}
widget_class "*<GtkListItem>*" style "clearlooks-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree
# Only match GtkCList and not the parent widgets, because that would also change the headers.
widget_class "*<GtkCList>" style "clearlooks-fg-is-text-color-workaround"

```

---

