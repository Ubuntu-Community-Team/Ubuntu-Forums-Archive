---
title: "Can i get rid of the stripes in Nautilus? (9.10)"
date: 2009-11-03
forum: Desktop Environments
---

### Post by Max Williams on 2009-11-03
I'd like to get rid of the striped rows in the Nautilus file browser, so it looks like 8.04, ie a plain white background.  But i can't work out how, can anyone tell me?

thanks
max

---

### Post by alienclone on 2009-11-03
open a nautilus window, click edit>backgrounds and emblems, then press the "colors" button on the left side of the box that pops up and drag the color square that you want over to the background and drop it.

---

### Post by Max Williams on 2009-11-03
> **alienclone said:**
> open a nautilus window, click edit>backgrounds and emblems, then press the "colors" button on the left side of the box that pops up and drag the color square that you want over to the background and drop it.
Hi - thanks.

I tried that, but it just flies back into the colors menu again, ie it doesn't "stick".

---

### Post by lordbinky on 2009-11-03
Are you viewing your icons as a list?  It doesn't work for me either when viewing as a list.  I don't think it is supposed to.

---

### Post by Max Williams on 2009-11-03
> **lordbinky said:**
> Are you viewing your icons as a list?  It doesn't work for me either when viewing as a list.  I don't think it is supposed to.

Ah yes, you're right - those backgrounds only apply to icon view, not list view.  So, they're irrelevant to my question then i guess.  My question should be 

"Can i get rid of the stripes in list view in Nautilus? (9.10)"

Thanks for clearing up that bit of confusion...i still want to get rid of the stripes though!

---

### Post by VCoolio on 2009-11-03
If I understand you correctly it's about the two background colors for the lines in a treeview. These are probably defined by "GtkTreeView::even_row_color" and "GtkTreeView::odd_row_color" inside the gtkrc file of your theme. Find your theme in /usr/share/themes or ~/.themes and change the colors to what you want in the gtkrc file inside the gtk-2.0 folder of the theme.

---

### Post by Max Williams on 2009-11-03
> **VCoolio said:**
> If I understand you correctly it's about the two background colors for the lines in a treeview. These are probably defined by "GtkTreeView::even_row_color" and "GtkTreeView::odd_row_color" inside the gtkrc file of your theme. Find your theme in /usr/share/themes or ~/.themes and change the colors to what you want in the gtkrc file inside the gtk-2.0 folder of the theme.

Hi Coolio - yes, assuming that by 'treeview' you mean the view that is called "List View" in nautilus.  It is a tree view though in that you can expand folders to show their contents, then expand subfolders etc.

I think you may be onto something with the gtkrc file, but i can't find the rows to change (there's no mention of 'odd', 'even', or 'row').  My desktop theme is "Human-Clearlooks", and here's the full contents - can you see anything that's setting these row colors?

thanks! max

#/usr/share/themes/Human-Clearlooks/gtk-2.0/gtkrc

# Ubuntu Human-Clearlooks Colorscheme
#
# Authors:
# Kenneth Wimar <kwwii@ubuntu.com>
# Conn O'Griofa <connogriofa@gmail.com>
#
# Feel free to modify and share!

gtk_color_scheme = "fg_color:#101010\nbg_color:#EFEBE7\nbase_color:#FFF\ntext_color:#1A1A1A\nselected_bg_color:#FFBE6B\nselected_fg_color:#1A1A1A\ntooltip_bg_color:#F5F5B5\ntooltip_fg_color:#000"

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
	GtkRange       ::slider-width         = 15
	GtkRange       ::stepper-size         = 15

	GtkScale       ::slider-length        = 30
	GtkScale       ::trough-side-details  = 1	# Restores sliders
	GtkScrollbar   ::min-slider-length    = 30

	GtkMenuBar     ::internal-padding     = 0
	GtkExpander    ::expander-size        = 16
	GtkToolbar     ::internal-padding     = 1
	GtkTreeView    ::expander-size        = 14
	GtkTreeView    ::vertical-separator   = 0

	GtkMenu        ::horizontal-padding   = 0
	GtkMenu        ::vertical-padding     = 0

	# Glow the tasklist by changing the color, instead of overlaying it with a rectangle
	WnckTasklist   ::fade-overlay-rect    = 0

	#GtkWidget * * *::link-color * * * *   = @fg_color
	#GtkWidget * * *::visited-link-color   = shade (0.2, @fg_color)

	xthickness = 1
	ythickness = 1

	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[ACTIVE]        = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[ACTIVE]        = shade (0.9, @bg_color)
	bg[SELECTED]	  = @selected_bg_color # Gnome Appearances Preferences workaround
	bg[INSENSITIVE]   = @bg_color

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (1.0, @selected_bg_color)
	base[SELECTED]    = shade (1.05, @selected_bg_color)
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
		toolbarstyle       = 0      # 0 = flat, 1 = enable effects
		animation          = TRUE
		radius		   = 2.0
		style              = GUMMY

		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "clearlooks-wide"
{
	xthickness   = 2
	ythickness   = 2
}

style "clearlooks-wider"
{
	xthickness   = 3
	ythickness   = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
	bg[NORMAL]   = shade (0.98, @bg_color)
	bg[PRELIGHT] = shade (1.04, @bg_color)
	bg[ACTIVE]   = shade (0.92, @bg_color)
}

style "clearlooks-notebook"
{
	bg[ACTIVE]   = shade (0.92, @bg_color)
}

style "clearlooks-tasklist" = "clearlooks-wide"
{
}

style "clearlooks-menu" = "clearlooks-wider"
{
	bg[NORMAL] = shade (1.04, @bg_color)
}

style "clearlooks-menu-item" = "clearlooks-wider"
{
	fg[PRELIGHT] = @selected_fg_color

	engine "clearlooks" 
	{
		radius = 1.5
	}
}

style "clearlooks-separator-menu-item"
{
}

style "clearlooks-treeview"
{
	fg[SELECTED] = @base_color

	engine "clearlooks" 
	{
		hint = "treeview"
	}
}

style "clearlooks-treeview-header"
{
	engine "clearlooks" 
	{
		hint = "treeview-header"
	}
}

style "clearlooks-frame-title"
{
	fg[NORMAL] = lighter (@fg_color)
}

style "clearlooks-tooltips" = "clearlooks-wider"
{
	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
}

style "clearlooks-progressbar"
{
	xthickness = 1
	ythickness = 1

	fg[PRELIGHT] = @base_color

	engine "clearlooks"
	{
		hint = "progressbar"
	}
}

style "clearlooks-statusbar"
{
	engine "clearlooks"
	{
		hint = "statusbar"
	}
}

style "clearlooks-comboboxentry"
{
	# NOTE:
	# If you set the appears-as-list option on comboboxes in the theme
	# you should set this hint on the combobox instead.
	engine "clearlooks"
	{
		hint = "comboboxentry"
	}
}

style "clearlooks-spinbutton"
{
	engine "clearlooks"
	{
		hint = "spinbutton"
	}
}

style "clearlooks-scale"
{
	engine "clearlooks"
	{
		hint  = "scale"
		style = CLASSIC
	}
}

style "clearlooks-hscale"
{
	engine "clearlooks"
	{
		hint = "hscale"
	}
}

style "clearlooks-vscale"
{
	engine "clearlooks"
	{
		hint = "vscale"
	}
}

style "clearlooks-scrollbar"
{
	engine "clearlooks"
	{
		hint   = "scrollbar"
		#style = CLASSIC
	}
}

style "clearlooks-hscrollbar"
{
	engine "clearlooks"
	{
		hint = "hscrollbar"
	}
}

style "clearlooks-vscrollbar"
{
	engine "clearlooks"
	{
		hint = "vscrollbar"
	}
}

style "clearlooks-menubar"
{
	engine "clearlooks"
	{
		hint = "menubar"
	}
}

style "clearlooks-nautilus-location"
{
	bg[NORMAL] = @selected_bg_color
}

style "metacity-frame"
{
}

style "clearlooks-radiocheck"
{
	text[PRELIGHT] = @base_color # Text on Mouseover
}

style "clearlooks-panel"
{
}

#########################################
# Matches
#########################################

# Theme radio buttons and checkmarks
class "GtkRadio*"                        		style "clearlooks-radiocheck"
class "GtkCheck*"                           		style "clearlooks-radiocheck"

# Keep proper colour for Metacity
class "MetaFrames" 					style "metacity-frame"
#class "GtkWindow"    			    		style "metacity-frame"

# Theme default style is applied to every widget
class "GtkWidget"    					style "clearlooks-default"

# Increase the x/ythickness in some widgets
class "GtkToolbar"   					style "clearlooks-default" 
class "GtkRange"     					style "clearlooks-wide"
class "GtkFrame"     					style "clearlooks-wide"
class "GtkSeparator" 					style "clearlooks-wide"
class "GtkEntry"     					style "clearlooks-wider"

class "GtkSpinButton"  					style "clearlooks-spinbutton"
class "GtkScale"       					style "clearlooks-scale"
class "GtkVScale"      					style "clearlooks-vscale"
class "GtkHScale"      					style "clearlooks-hscale"
class "GtkScrollbar"   					style "clearlooks-scrollbar"
class "GtkVScrollbar"  					style "clearlooks-vscrollbar"
class "GtkHScrollbar"  					style "clearlooks-hscrollbar"

# General matching following, the order is choosen so that the right styles override each other
# eg. progressbar needs to be more important then the menu match.

# This is not perfect, it could be done better
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"     	style "clearlooks-notebook"
widget_class "*<GtkNotebook>*<GtkDrawingArea>"  	style "clearlooks-notebook"
widget_class "*<GtkNotebook>*<GtkLayout>"       	style "clearlooks-notebook"

widget_class "*<GtkButton>"      			style "clearlooks-button"
widget_class "*<GtkNotebook>"    			style "clearlooks-notebook"
widget_class "*<GtkStatusbar>*"  			style "clearlooks-statusbar"

widget_class "*<GtkComboBoxEntry>*"			style "clearlooks-comboboxentry"
widget_class "*<GtkCombo>*"         			style "clearlooks-comboboxentry"

widget_class "*<GtkMenuBar>*"           		style "clearlooks-menubar"
widget_class "*<GtkMenu>*"              		style "clearlooks-menu"
widget_class "*<GtkMenuItem>*"          		style "clearlooks-menu-item"
widget_class "*<GtkSeparatorMenuItem>*" 		style "clearlooks-separator-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>" 			style "clearlooks-frame-title"
widget_class "*.<GtkTreeView>*"        			style "clearlooks-treeview"

widget_class "*<GtkProgressBar>"       			style "clearlooks-progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" 		style "clearlooks-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"    		style "clearlooks-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"     		style "clearlooks-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"    		style "clearlooks-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"    			style "clearlooks-treeview-header"
widget_class "*.ETree.ECanvas"    			style "clearlooks-treeview-header"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" 					style "clearlooks-tooltips"

###################################################
# Special cases and work arounds
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" 			style : highest "clearlooks-nautilus-location"

# Work around for [http://bugzilla.gnome.org/show_bug.cgi?id=382646](http://bugzilla.gnome.org/show_bug.cgi?id=382646)
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
style "clearlooks-combobox-text-color-workaround"
{
	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @fg_color
	text[ACTIVE]      = @fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>"		style "clearlooks-combobox-text-color-workaround"

style "clearlooks-menuitem-text-is-fg-color-workaround"
{
	text[NORMAL]        = @fg_color
	text[PRELIGHT]      = @selected_fg_color
	text[ACTIVE]        = @fg_color
	text[SELECTED]      = @selected_fg_color
	text[INSENSITIVE]   = darker (@bg_color)
}

widget "*.gtk-combobox-popup-menu.*"   			style "clearlooks-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the
# base color set.
style "clearlooks-fg-is-text-color-workaround"
{
	bg[SELECTED]    = @selected_bg_color
	fg[NORMAL]      = @text_color
	fg[PRELIGHT]    = @text_color
	fg[ACTIVE]      = @selected_fg_color
	fg[SELECTED]    = @selected_fg_color
	fg[INSENSITIVE] = darker (@bg_color)
}

widget_class "*<GtkListItem>*" 				style "clearlooks-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree
# Only match GtkCList and not the parent widgets, because that would also change the headers.

widget_class "*<GtkCList>" 				style "clearlooks-fg-is-text-color-workaround"

style "clearlooks-evo-new-button-workaround"
{

	engine "clearlooks"
	{
		toolbarstyle = 0
	}
}
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "clearlooks-evo-new-button-workaround"

# Theme panel elements
widget "*PanelWidget*" 					style "clearlooks-panel"
widget "*PanelApplet*" 					style "clearlooks-panel"
widget "*fast-user-switch*"				style "clearlooks-panel"
class "PanelApp*" 					style "clearlooks-panel"
class "PanelToplevel*" 					style "clearlooks-panel"
widget_class "*Mail*" 					style "clearlooks-panel"
widget_class "*notif*" 					style "clearlooks-panel"
widget_class "*Notif*" 					style "clearlooks-panel"

---

### Post by VCoolio on 2009-11-03
Starting on line 135 you see:
```
style "clearlooks-treeview"
{
  fg[SELECTED] = @base_color

  engine "clearlooks"
  {
    hint = "treeview"
  }
}

```

Now add the lines I mentioned like this and change the colors of course to whatever you like ("#ffffff" or "white" if you want white, or @base_color (which is also white at the moment) if you want it to change along with the other colors if you modify the colors in appearance manager):

```

style "clearlooks-treeview"
{
  GtkTreeView::odd_row_color = "red"
  GtkTreeView::even_row_color = "yellow"

  fg[SELECTED] = @base_color

  engine "clearlooks"
  {
    hint = "treeview"
  }
}

```

You'll need root permission to edit the clearlooks gtkrc file, so "gksudo gedit /usr/share/themes/Human-Clearlooks/gtk-2.0/gtkrc". You can also put the two lines on top of the file among the other similar-looking definitions (under Style properties).

---

### Post by Max Williams on 2009-11-04
Thanks a lot - but i'm afraid that didn't work... :/  

I edited as follows, with some primary colours just to make it really obvious.

style "clearlooks-treeview"
{
	fg[SELECTED] = @base_color
	GtkTreeView::odd_row_color = "#ff0000"
	GtkTreeView::even_row_color = "#00ff00"


	engine "clearlooks" 
	{
		hint = "treeview"
	}
}

That didn't appear to work so i restarted gnome with "killall gnome-panel" - this definitely restarted as most of my apps disappeared temporarily and then came back.  But, i still get the rows as before - no bright red or green anywhere.  I tried setting them to @base_color as well, still no joy.

I also tried putting the lines in the treeview-default section


style "clearlooks-default"
{
	########
	# Style Properties
	########
	GtkButton      ::child-displacement-x = 1
	GtkButton      ::child-displacement-y = 1
        .....

	GtkMenu        ::horizontal-padding   = 0
	GtkMenu        ::vertical-padding     = 0
	GtkTreeView    ::odd_row_color        = "#FF0000"
	GtkTreeView    ::even_row_color       = "#00FF00"

That didn't work either.  Maybe the variable names are wrong?  I tried changing them to "odd-row-color" and "even-row-color", no luck.

This bug, which may be relevant, seems to use odd_row_color AND odd-row-color...
[https://bugzilla.redhat.com/show_bug.cgi?id=454644](https://bugzilla.redhat.com/show_bug.cgi?id=454644)

Although this page suggests that you had the right variable names to start off with.
[http://www.daa.com.au/pipermail/pygtk/2003-March/004680.html](http://www.daa.com.au/pipermail/pygtk/2003-March/004680.html)

Thanks so much for your patience - do you have any other ideas?  Will "killall gnome-panel" actually cause the settings to be reloaded?  (i thought it would but i could be wrong)
max

---

### Post by VCoolio on 2009-11-04
Sorry, I should have mentioned this. I disabled gnome-settings-daemon and use the file ~/.gtk-2.0 to set gtk-theme and icon theme, so if I start an app the modified gtkrc is used immediately. "killall gnome-panel" only reloads the panel, not gtk. You can use [twl]("https://launchpad.net/~freshapplepy/+archive/twl") or [pytwf]("http://www.gtk-apps.org/content/show.php/PyTWF?content=102024") to check changes you make in themes. To apply themes either change theme in appearance and then change back, or logout and back in. (I checked my suggested modifications and it worked for me, so try again plz).

---

### Post by Max Williams on 2009-11-05
> **VCoolio said:**
> Sorry, I should have mentioned this. I disabled gnome-settings-daemon and use the file ~/.gtk-2.0 to set gtk-theme and icon theme, so if I start an app the modified gtkrc is used immediately. "killall gnome-panel" only reloads the panel, not gtk. You can use [twl]("https://launchpad.net/~freshapplepy/+archive/twl") or [pytwf]("http://www.gtk-apps.org/content/show.php/PyTWF?content=102024") to check changes you make in themes. To apply themes either change theme in appearance and then change back, or logout and back in. (I checked my suggested modifications and it worked for me, so try again plz).

Aha!  Yes, changing the theme and then changing it back again worked.  

Thanks again for all your help!  I'm off to play with more theme settings now i know how to see the results :)

cheers!
max

---

### Post by mohdyusuf on 2009-11-18
worked brilliantly for me.. just what the doctor's order.. :)

---

