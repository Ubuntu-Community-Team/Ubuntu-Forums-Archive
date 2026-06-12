---
title: "Want to increase icon size of lauchers in panel"
date: 2013-03-22
forum: Desktop Environments
---

### Post by Ralph L on 2013-03-22
I recently installed xubuntu 12.04.2.  I have my main panel setup rather narrow so that I have more usable space on my small laptop screen.  Now my launcher icons are very small.  They are about half the width of the panel.  I can increase their size by making the panel wider, but I don't want to do that.  I believe that some place I set icons to small, but I can't find the place again.

Anybody know how I can make the launcher icons larger without increasing the panel width.

---

### Post by LarsKongo on 2013-03-22
It's a flaw in XFCE design. It resizes icons based on the horizontal xthickness value. You need to edit the theme you are using, or add this in ~/.gtkrc-2.0:
```
style "panel-icon-fix" {
	xthickness = 0
}

widget "*PanelWidget*" style "panel-icon-fix"
widget "*PanelApplet*" style "panel-icon-fix"
widget "*Xfce*Panel*Button*" style:highest "panel-icon-fix"
class "*Xfce*Panel*Button*" style:highest "panel-icon-fix"
widget_class "*LauncherPlugin*" style:highest "panel-icon-fix"
widget_class "*ActionsPlugin*" style:highest "panel-icon-fix"
```
That may be possible for the launcher only with ***widget_class "*LauncherPlugin*" style:highest "panel-icon-fix"***, but I've not tested it myself.
Note that some items may get an extremely narrow horizontal padding with xthickness set to 0. But that's the only way to resize icons properly in the panel that I know of. Setting the icon size in ***gtk-icon-sizes = "panel-menu=16,16:panel=16,16"*** does not seem to work in XFCE.

---

### Post by Ralph L on 2013-03-22
LarsKongo

Thank you very much for the response.  I really appreciate it.  I created the file ~/.gtkrc-2.0 (it did not exist previously) and installed the code you recommended in it.  I then restarted, but there was no change to the icon size.  Is there something else I need to do?

---

### Post by LarsKongo on 2013-03-22
Hmm, I also can't seem to get anything in the gtkrc-2.0 file to work. It would be easier if I could take a look directly at the theme you're using instead.
If you've installed a 3rd party theme you will probably know where it's located. The default theme in Xubuntu is called Greybird and is located in /usr/share/themes/Greybird. There should be a file there called gtkrc and/or *panel.rc in 1 or 2 sub folders. If there's no panel.rc post the gtkrc file here so I can take a look, otherwise post the panel.rc file instead.

EDIT: If you are using Greybird. Just try to change all xthickness and ythickness to 0 in */usr/share/themes/Greybird/gtk-2.0/apps/xfce-panel.rc*.

---

### Post by Ralph L on 2013-03-22
LarsKongo

I am using the Clearlooks-Phenix theme [http://www.jpfleury.net/en/software/clearlooks-phenix.php](http://www.jpfleury.net/en/software/clearlooks-phenix.php) .  I like it because it is bright and has the stepper arrows are restored.  It does waste screen space in that the titlebar, menubar, toolbars, and sliders are all too wide, but I guess I can't have everything.  For icons I am using elementary Xfce, although I really don't like rather gray dingy look of the Xfce panel icons.  Clearlooks-Phenix has no panel.rc file, but does have an gtkrc file in folder gtk-2.0.  I am including listing of it below.  I noticed that the size of the icons is controlled by the overall theme rather than the icons theme as I would have thought.  If I switch the overall theme to Graybird, the launcher icons get much bigger.

Thank you very much for your help.
```

# Please keep this gtkrc in sync with the other ones from Clearlooks based themes.

gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#86abd9\nselected_fg_color:#ffffff\ntext_color:#1a1a1a\nbg_color:#edeceb\ntooltip_bg_color:#f5f5b5\nlink_color:#0000ee\nvisited_link_color:#551a8b"

style "default" {
	xthickness = 1
	ythickness = 1

	#######################
	# Style Properties
	#######################
	GtkButton::child-displacement-x = 1
	GtkButton::child-displacement-y = 1
	GtkButton::default-border = { 0, 0, 0, 0 }
	GtkButton::image-spacing = 4
	GtkToolButton::icon-spacing = 4

	GtkCheckButton::indicator-size = 14

	GtkPaned::handle-size = 6

	GtkRange::trough-border = 0
	GtkRange::slider-width = 15
	GtkRange::stepper-size = 15

	GtkScale::slider-length = 23
	GtkScale::trough-side-details = 1

	GtkScrollbar::min-slider-length = 30
	GtkMenuBar::internal-padding = 0
	GtkExpander::expander-size = 16
	GtkToolbar::internal-padding = 1
	GtkTreeView::expander-size = 14
	GtkTreeView::vertical-separator = 0

	GtkMenu::horizontal-padding = 0
	GtkMenu::vertical-padding = 0

	WnckTasklist::fade-overlay-rect = 0
	# The following line hints to gecko (and possibly other appliations)
	# that the entry should be drawn transparently on the canvas.
	# Without this, gecko will fill in the background of the entry.
	GtkEntry::honors-transparent-bg-hint = 1

	GtkEntry::progress-border = { 2, 2, 2, 2 }

	GtkWidget::link-color = @link_color
	GtkWidget::visited-link-color = @visited_link_color

	####################
	# Color Definitions
	####################
	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]      = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[INSENSITIVE]   = darker (@bg_color)
	fg[ACTIVE]        = @fg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)
	text[ACTIVE]      = @selected_fg_color

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @bg_color
	base[ACTIVE]      = shade (0.9, @selected_bg_color)

	engine "clearlooks" {
		colorize_scrollbar = TRUE
		reliefstyle = 1
		menubarstyle = 2
		toolbarstyle = 1
		animation = FALSE
		radius = 3.0
		style = GUMMY

		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "wide" {
	xthickness = 2
	ythickness = 2
}

style "wider" {
	xthickness = 3
	ythickness = 3
}

style "entry" {
	xthickness = 3
	ythickness = 3

	bg[SELECTED] = mix (0.4, @selected_bg_color, @base_color)
	fg[SELECTED] = @text_color

	engine "clearlooks" {
		focus_color = shade (0.65, @selected_bg_color)
	}
}

style "spinbutton" {

	engine "clearlooks" {
		hint = "spinbutton"
	}
}

style "scale" {
	xthickness = 2
	ythickness = 2

	engine "clearlooks" {
		hint = "scale"
	}
}

style "vscale" {

	engine "clearlooks" {
		hint = "vscale"
	}
}

style "hscale" {

	engine "clearlooks" {
		hint = "hscale"
	}
}

style "scrollbar" {
	xthickness = 2
	ythickness = 2

	engine "clearlooks" {
		hint = "scrollbar"
	}
}

style "hscrollbar" {

	engine "clearlooks" {
		hint = "hscrollbar"
	}
}

style "vscrollbar" {

	engine "clearlooks" {
		hint = "vscrollbar"
	}
}

style "notebook_bg" {

	bg[NORMAL]        = shade (1.02, @bg_color)
}

style "button" {
	xthickness = 3
	ythickness = 3

	bg[NORMAL]        = shade (1.04, @bg_color)
	bg[PRELIGHT]      = shade (1.06, @bg_color)
	bg[ACTIVE]        = shade (0.85, @bg_color)
}

# The color is changed by the notebook_bg style, this style
# changes the x/ythickness
style "notebook" {
	xthickness = 3
	ythickness = 3
}

style "statusbar" {

	engine "clearlooks" {
		hint = "statusbar"
	}
}

style "comboboxentry" {

	engine "clearlooks" {
		# Note:
		# If you set the appears-as-list option on comboboxes in the theme,
		# then you should set this hint on the combobox instead.
		hint = "comboboxentry"
	}
}

style "menubar" {

	engine "clearlooks" {
		hint = "menubar"
	}
}

style "menu" {
	xthickness = 1
	ythickness = 1

	bg[NORMAL]        = shade (1.08, @bg_color)

	engine "clearlooks" {
		radius = 0.0
	}
}

style "menu_item" {
	xthickness = 2
	ythickness = 3

	fg[PRELIGHT]      = @selected_fg_color
}

# This style is there to modify the separator menu items. The goals are:
# 1. Get a specific height.
# 2. The line should go to the edges (ie. no border at the left/right)
style "separator_menu_item" {
	xthickness = 1
	ythickness = 0

	GtkSeparatorMenuItem::horizontal-padding = 0
	GtkWidget::wide-separators = 1
	GtkWidget::separator-width = 1
	GtkWidget::separator-height = 7
}

style "frame_title" {

	fg[NORMAL]        = lighter (@fg_color)
}

style "treeview" {

	engine "clearlooks" {
		hint = "treeview"
	}
}

# The almost useless progress bar style
style "progressbar" {
	xthickness = 1
	ythickness = 1

	fg[PRELIGHT]      = @selected_fg_color

	engine "clearlooks" {
		# Explicitly set the radius for the progress bars inside menu items.
		radius = 3.0

		hint = "progressbar"
	}
}

# This style is based on the default style, so that the colors from the button
# style are overriden again.
style "treeview_header" = "default" {
	xthickness = 2
	ythickness = 1

	engine "clearlooks" {
		hint = "treeview-header"
	}
}

style "tooltips" {
	xthickness = 4
	ythickness = 4

	bg[NORMAL]        = @tooltip_bg_color
	fg[NORMAL]        = @tooltip_fg_color
}

style "nautilus_location" {

	bg[NORMAL]        = mix (0.60, shade (1.05, @bg_color), @selected_bg_color)
}

# Wrokaroudn style for places where the text color is used instead of the fg color.
style "text_is_fg_color_workaround" {

	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for menus where the text color is used instead of the fg color.
style "menuitem_text_is_fg_color_workaround" {

	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for places where the fg color is used instead of the text color.
style "fg_is_text_color_workaround" {

	fg[NORMAL]        = @text_color
	fg[PRELIGHT]      = @text_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @selected_fg_color
	fg[INSENSITIVE]   = darker (@bg_color)
}

# Style to set the toolbar to use a flat style. This is because the "New" button in
# Evolution is not drawn transparent. So if there is a gradient in the background it will
# look really wrong.
# See http://bugzilla.gnome.org/show_bug.cgi?id=446953.
style "evo_new_button_workaround" {

	engine "clearlooks" {
		toolbarstyle = 0
	}
}

###############################################################################
# The following part of the gtkrc applies the different styles to the widgets.
###############################################################################

# The default style is applied to every widget
class "GtkWidget" style "default"

class "GtkSeparator" style "wide"
class "GtkFrame" style "wide"
class "GtkCalendar" style "wide"
class "GtkEntry" style "entry"

class "GtkSpinButton" style "spinbutton"
class "GtkScale" style "scale"
class "GtkVScale" style "vscale"
class "GtkHScale" style "hscale"
class "GtkScrollbar" style "scrollbar"
class "GtkHScrollbar" style "hscrollbar"
class "GtkVScrollbar" style "vscrollbar"

# General matching follows. The order is choosen so that the right styles override
# each other. EG. progressbar needs to be more important than the menu match.
widget_class "*<GtkNotebook>" style "notebook_bg"
# This is not perfect, it could be done better.
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkLayout>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkViewport>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkScrolledWindow>" style "notebook_bg"

widget_class "*<GtkButton>" style "button"
widget_class "*<GtkNotebook>" style "notebook"
widget_class "*<GtkStatusbar>*" style "statusbar"

widget_class "*<GtkComboBoxEntry>*" style "comboboxentry"
widget_class "*<GtkCombo>*" style "comboboxentry"

widget_class "*<GtkMenuBar>*" style "menubar"
widget_class "*<GtkMenu>*" style "menu"
widget_class "*<GtkMenuItem>*" style "menu_item"
widget_class "*<GtkSeparatorMenuItem>*" style "separator_menu_item"

widget_class "*.<GtkFrame>.<GtkLabel>" style "frame_title"
widget_class "*.<GtkTreeView>*" style "treeview"

widget_class "*<GtkProgress>" style "progressbar"

# Treeview headers (and similar stock GTK+ widgets)
widget_class "*.<GtkTreeView>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCTree>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkList>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCList>.<GtkButton>" style "treeview_header"

# The window of the tooltip is called "gtk-tooltip"
##################################################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
##################################################################
widget "gtk-tooltip*" style "tooltips"

##########################################################################
# Following are special cases and workarounds for issues in applications.
##########################################################################

include "applications.rc"


```

---

### Post by LarsKongo on 2013-03-23
I wrote something wrong in the .gtkrc-2.0 file. This should do the trick: (It did for me.) ;)
```
style "panel-icon-fix" {
	xthickness = 0
	ythickness = 0
}

widget "*Xfce*Panel*"	style "panel-icon-fix"
class "*Xfce*Panel*"	style "panel-icon-fix"
```

---

### Post by Ralph L on 2013-03-25
That fixed it.

Thank you very much

Ralph

---

