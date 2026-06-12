---
title: "How To Change Theme button Orientation/relief (config file)"
date: 2010-09-18
forum: Desktop Environments
---

### Post by UbuNoob001 on 2010-09-18
Hey all, 
   I am looking to change the button orientation on a default-right theme. The 1st config file is below. I would like to move the buttons to the Left.    On the second config file, I would like to make the deliniation between the menu bar (file edit etc) and the next (usually navigation) bar less obvious. Less stark/relief. Any help is greatly appreciated ```
# Based on Clearlooks Pro
# Modified by Ferenc Nagy - nferenc@users.sourceforge.net

# Please keep this gtkrc in sync with the other ones from Clearlooks based themes.

gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#86ABD9\nselected_fg_color:#ffffff\ntext_color:#1A1A1A\nbg_color:#E1E1E1\ntooltip_bg_color:#F5F5B5"

gtk-button-images = 0
gtk-menu-images = 1
#gtk-icon-sizes = "gtk-button=16,16" 

style "default" {
    xthickness = 1
    ythickness = 1

    #######################
    # Style Properties
    #######################
    GtkButton::child-displacement-x = 1
    GtkButton::child-displacement-y = 1
    GtkButton::default-border = { 0, 0, 0, 0 }

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
        toolbarstyle = 2
        animation = TRUE
        radius = 2.3
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
    bg[PRELIGHT]      = shade (1.3, @bg_color)
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
    xthickness = 0
    ythickness = 0

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
class "GtkEntry" style "wider"

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

# Workaround for the evolution ETable (bug #527532)
widget_class "*.ETable.ECanvas" style "treeview_header"
# Workaround for the evolution ETree
widget_class "*.ETree.ECanvas" style "treeview_header"

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "nautilus_location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that this work around assumes that the combobox is _not_ in appears-as-list mode.
widget_class "*.<GtkComboBox>.<GtkCellView>" style "text_is_fg_color_workaround"
# This is the part of the workaround that fixes the menus
widget "*.gtk-combobox-popup-menu.*" style "menuitem_text_is_fg_color_workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the base color.
widget_class "*<GtkListItem>*" style "fg_is_text_color_workaround"
# GtkCList also uses the fg color to draw text on top of the base colors.
widget_class "*<GtkCList>" style "fg_is_text_color_workaround"
# Nautilus when renaming files, and maybe other places.
widget_class "*<EelEditableLabel>" style "fg_is_text_color_workaround"

# See the documentation of the style.
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "evo_new_button_workaround"
```

and ```
# absolute 1.0 by Alexey S. Ignatiev <twosev@gmail.com>

# Set GtkSettings color scheme property.
# This can be overriden (via an xsetting) with eg. the gnome-appearance-properties.
gtk_color_scheme = "fg_color:#333333333333\nbg_color:#e147e147e147\ntext_color:#1a1a1a1a1a1a\nbase_color:#ffffffffffff\nselected_fg_color:#47ae33d32546\nselected_bg_color:#BDBDCECEE3E3\ntooltip_fg_color:#000000000000\ntooltip_bg_color:#fffff9f9dfdf"
# orig selected_bg_color:#8686ababd9d9

gtk_color_scheme    = "frame_color:#dcdcdc\ninactive_frame_color:#e1e1e1" # Fix for Chrome

gtk-icon-sizes = "gtk-button=16,16:\ngtk-dnd=16,16:\npanel=16,16:\ngtk-small-toolbar=16,16:\ngtk-large-toolbar=24,24:"

gtk-button-images = 0
gtk-menu-popup-delay = 0

style "bold-text" {
  font_name = "semi-bold"
}

style "small-text" {
  font_name = "8"
}

style "murrine-default" {
  ########
  # Style Properties
  ########
######################
  # GtkWidget         ::new-tooltip-style     = 1
  GtkButton         ::child-displacement-x  = 1
  GtkButton         ::child-displacement-y  = 1
  GtkButton         ::default-border        = { 0, 0, 0, 0 }
  GtkCheckButton    ::indicator-size        = 14

  GtkPaned          ::handle-size           = 6

  GtkRange          ::trough-border         = 0
  GtkRange          ::slider-width          = 13
  GtkRange          ::stepper-size          = 13
  GtkRange          ::stepper-spacing       = 1
  GtkRange          ::activate-slider       = 1
  GtkRange          ::arrow-displacement-x  = 1
  GtkRange          ::arrow-displacement-y  = 1
  GtkRange          ::arrow-scaling         = 0.7

  GtkScale          ::slider-length         = 25
  GtkScale          ::trough-side-details   = 0
  GtkScrollbar      ::min-slider-length     = 30
  GtkScrolledWindow ::scrollbar-spacing     = 3

  GtkMenuBar        ::internal-padding      = 2
  GtkExpander       ::expander-size         = 16
  GtkToolbar        ::internal-padding      = 1
  GtkTreeView       ::expander-size         = 14
  GtkTreeView       ::vertical-separator    = 0

  GtkMenu           ::horizontal-padding    = 0
  GtkMenu           ::vertical-padding      = 0

  GtkNotebook       ::tab-overlap           = -1

  # The following line hints to gecko (and possibly other appliations)
  # that the entry should be drawn transparently on the canvas.
  # Without this, gecko will fill in the background of the entry.
  GtkEntry::honors-transparent-bg-hint      = 1
  GtkEntry::state-hint                      = 0

  GtkEntry::progress-border                 = { 2, 2, 2, 2 }

  # GtkProgressBar::min-horizontal-bar-height = 5
  # GtkProgressBar::min-vertical-bar-width    = 5

  # Glow the tasklist by changing the color, instead of overlaying it
  # with a rectangle
  # WnckTasklist    ::fade-overlay-rect    = 0

  # Flat menubars and toolbar
  # GtkMenuBar::shadow_type = GTK_SHADOW_NONE
  # GtkToolbar::shadow_type = GTK_SHADOW_NONE

  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = @fg_color
  fg[PRELIGHT]      = @fg_color
  fg[SELECTED]      = @selected_fg_color
  fg[ACTIVE]        = @fg_color
  fg[INSENSITIVE]   = darker (@bg_color)

  bg[NORMAL]        = @bg_color
  bg[PRELIGHT]      = shade (1.02, @bg_color)
  bg[SELECTED]      = @selected_bg_color
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

  engine "murrine" {
    animation           = TRUE
    arrowstyle          = 0      # Not filled arrows   
    colorize_scrollbar  = FALSE
    comboboxstyle       = 0      # not colored combobox below the arrow
    contrast            = 0.8    # 0.8 for less contrast, more than 1.0 for more
                                 # contrast on borders
    expanderstyle       = 2      # buttons with plus and minus
    focusstyle          = 3      # colored rectangle touching the borders
    glazestyle          = 0      # 0 = flat highlight, 1 = curved highlight,
                                 # 2 = concave style, 3 = top curved highlight,
                                 # 4 = beryl highlight
    gradient_shades     = { 1.01, 1.0, 1.0, 0.99 }
    handlestyle         = 0      # three simple lines
    highlight_shade     = 1.0    # set highlight amount for buttons or widgets
    lightborder_shade   = 1.2    # sets lightborder amount for buttons or widgets
    lightborderstyle    = 0      # 0 = lightborder on top side, 1 = lightborder
                                 # on all sides
    listviewheaderstyle = 0      # 0 = flat, 1 = glassy, 2 = raised
    listviewstyle       = 1      # 0 = nothing, 1 = dotted
    menubaritemstyle    = 1      # 0 = menuitem look, 1 = button look
    menubarstyle        = 0      # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
    menuitemstyle       = 1      # 0 = flat, 1 = glassy, 2 = striped
    menustyle           = 0      # 0 = no vertical menu stripe, 1 = display
                                 # vertical menu stripe
    progressbarstyle    = 0      # 0 = flat, 1 = stripped, 2 = blocks
    reliefstyle         = 2      # 0 = flat, 1 = inset, 2 = shadow
    rgba                = FALSE  # FALSE = disabled, TRUE = enabled
    roundness           = 3      # 0 = squared, 1 = old default, more will
                                 # increase roundness
    scrollbarstyle      = 2      # 0 = nothing, 1 = circles, 2 = handles,
                                 # 3 = diagonal stripes, 4 = diagonal stripes
                                 # and handles, 5 = horizontal stripes,
                                 # 6 = horizontal stripes and handles
    separatorstyle      = 1      # smooth separator
    sliderstyle         = 0      # 0 = nothing added, 1 = handles
    stepperstyle        = 1      # 0 = standard, 1 = integrated stepper handles,
                                 # 2 = unknown
    toolbarstyle        = 2      # 0 = flat, 1 = glassy, 2 = gradient
    }
}

style "murrine-nogap" {
  xthickness   = 0
  ythickness   = 0
}

style "murrine-wide" {
  xthickness   = 2
  ythickness   = 2
}

style "murrine-wider" {
  xthickness   = 3
  ythickness   = 3
}

style "murrine-button" {
  xthickness   = 3
  ythickness   = 3
  bg[NORMAL]   = shade (1.05, @bg_color)
  bg[ACTIVE]   = shade (0.95, @bg_color)
}

style "murrine-entry" {
  xthickness   = 3
  ythickness   = 3

  bg[SELECTED] = mix (0.4, @selected_bg_color, @base_color)
  fg[SELECTED] = @text_color

  engine "murrine" {
    border_shades = { 1.0, 1.0 }
    contrast      = .7
  }
}

style "murrine-notebook-bg" = "murrine-wider" {
  bg[NORMAL]   = shade (1.05, @bg_color)
  bg[ACTIVE]   = shade (0.95, @bg_color)
}

style "murrine-notebook" = "murrine-notebook-bg" {
}

style "murrine-tasklist" {
  xthickness   = 5
  ythickness   = 3
}

style "murrine-panel" {
}

style "murrine-menu" {
  xthickness   = 0
  ythickness   = 0
  fg[PRELIGHT] = @selected_fg_color
  # Radius of the menu items (inside menus)
  engine "murrine" {
    roundness  = 3
  }
}

style "murrine-menu-item" { # = "bold-text"
  xthickness   = 3
  ythickness   = 3
  # bg[PRELIGHT] = @selected_bg_color # for menu's headers
}

style "murrine-separator-menu-item" {
  GtkSeparatorMenuItem::horizontal-padding = 0
  # We are setting the desired height by using wide-separators
  # There is no other way to get the odd height ...
  GtkWidget::wide-separators  = 1
  GtkWidget::separator-width  = 1
  GtkWidget::separator-height = 5
  xthickness   = 1
  ythickness   = 0
}

style "murrine-treeview" {
  engine "murrine" {
    roundness = 1 # The radius for progress bars insied treeview.
  }
}

# Based on the default style so that the colors from the button
# style are overriden again.
style "murrine-treeview-header" = "murrine-button" {
  xthickness   = 2
  ythickness   = 1
}

style "murrine-frame-title" {
  fg[NORMAL]   = lighter (@fg_color)
}

style "murrine-tooltips" {
  xthickness   = 4
  ythickness   = 4

  bg[NORMAL]   = @tooltip_bg_color
  fg[NORMAL]   = @tooltip_fg_color
}

style "murrine-progressbar" {
  xthickness   = 0
  ythickness   = 0

  fg[PRELIGHT] = @selected_fg_color

  engine "murrine" {
    # Explicitly set the radius, for progress
    # bars inside menuitems
    roundness  = 1
    trough_border_shades = { .98, 1.1 }
  }
}

style "murrine-statusbar" {
  xthickness   = 2
  ythickness   = 2
}

style "murrine-comboboxentry" {
  # NOTE:
  # If you set the appears-as-list option on comboboxes in the theme
  # you should set this hint on the combobox instead.
}

style "murrine-spinbutton" {
}

style "murrine-scale" {
  GtkRange::slider-width  = 12
  GtkScale::slider-length = 12

  engine "murrine" {
    roundness  = 2
    trough_border_shades = { .98, 1.1 }
  }
}

style "murrine-hscale" {
}

style "murrine-vscale" {
}

style "murrine-scrollbar" = "murrine-button" {
  GtkRange::trough-under-steppers = 0
  bg[NORMAL]   = shade (0.95, @bg_color)

  engine "murrine" {
    roundness  = 3
  }
}

style "murrine-menubar" {
  xthickness   = 2
  ythickness   = 2
  engine "murrine" {
    roundness     = 3
  }
}

style "murrine-low" {
  engine "murrine" {
    contrast   = 0.85
  }
}

style "murrine-nautilus-location" {
  bg[NORMAL]   = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}

style "murrine-nautilus-sidebar" {
  font_name                     = "Regular"
  GtkTreeView::odd_row_color    = @bg_color
  GtkTreeView::even_row_color   = @bg_color

  GtkPaned::handle_size         = 1
  GtkWidget::wide_separator     = 1
  GtkWidget::separator_width    = 1
  GtkWidget::separator_height   = 0
  GtkWidget::focus_line_width   = 0
  GtkWidget::draw_border        = { 0, 0, 0, 0 }

  # these make the padding from left window edge a little more sane
  GtkTreeView::vertical_separator   = 4
  GtkTreeView::horizontal_separator = 15
  GtkTreeView::indent-expanders     = 1 # 1 means TRUE
  GtkTreeView::expander-size        = 12
  GtkExpander::expander_spacing     = 16
  GtkButton::image_spacing          = 4
  xthickness                        = 8
  ythickness                        = 0
}

style "pixmap-nautilus-handle" {
  GtkPaned::handle-size = 1

  engine "pixmap" {
    image { # for the thin gray line separating the sidepane and viewpane
      function    = HANDLE
      recolorable = TRUE
      file        = "transparent_dot.png"
      stretch     = TRUE
      border      = { 0, 0, 0, 0 }
    }
  }
}

style "murrine-evo-new-button" {
  engine "murrine" {
    toolbarstyle = 1
  }
}

style "murrine-gedit-sidetoolbar" {
  GtkToolbar::shadow_type = GTK_SHADOW_NONE
}

#########################################
# Matches
#########################################

# Murrine default style is applied to every widget
class "GtkWidget"     style "murrine-default"

# Increase the x/ythickness in some widgets
class "GtkToolbar"    style "murrine-default"
class "GtkRange"      style "murrine-wide"
class "GtkFrame"      style "murrine-wide"
class "GtkSeparator"  style "murrine-wide"

class "GtkEntry"      style "murrine-entry"
class "GtkSpinButton" style "murrine-spinbutton"
class "GtkScale"      style "murrine-scale"
class "GtkVScale"     style "murrine-vscale"
class "GtkHScale"     style "murrine-hscale"
class "GtkScrollbar"  style "murrine-scrollbar"
class "GtkVScrollbar" style "murrine-scrollbar"
class "GtkHScrollbar" style "murrine-scrollbar"

# General matching following, the order is choosen so that the right styles
# override each other eg. progressbar needs to be more important then the
# menu match.

#Panel
widget "*PanelWidget*"      style "murrine-panel"
widget "*PanelApplet*"      style "murrine-panel"
widget "*fast-user-switch*" style "murrine-panel" # Workaround for
                                                  # Fast User Switch applet
class  "PanelApp*"          style "murrine-panel"
class  "PanelToplevel*"     style "murrine-panel"

# This is not perfect, it could be done better
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"    style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>" style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkLayout>"      style "murrine-notebook-bg"

widget_class "*<GtkButton>"                    style "murrine-button"
widget_class "*<GtkNotebook>"                  style "murrine-notebook"
widget_class "*<GtkStatusbar>*"                style : highest "murrine-statusbar"

widget_class "*<GtkComboBoxEntry>*"            style "murrine-comboboxentry"
widget_class "*<GtkCombo>*"                    style "murrine-comboboxentry"

widget_class "*<GtkMenu>*"                     style "murrine-menu"
widget_class "*<GtkMenuItem>*"                 style "murrine-menu-item"
widget_class "*<GtkMenuBar>*"                  style "murrine-menubar"
widget_class "*<GtkSeparatorMenuItem>*"        style "murrine-separator-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>"         style "murrine-frame-title"
widget_class "*.<GtkTreeView>*"                style "murrine-treeview"

widget_class "*<GtkProgressBar>"               style "murrine-progressbar"

widget_class "*ToolButton*"                    style "small-text"
widget_class "*Statusbar*"                     style "small-text"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>"     style "murrine-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"        style "murrine-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"         style "murrine-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"        style "murrine-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"                style "murrine-treeview-header"
widget_class "*.ETree.ECanvas"                 style "murrine-treeview-header"
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "murrine-evo-new-button"

# Nautilus Places
widget_class "*Nautilus*Places*Sidebar*"       style "murrine-nautilus-sidebar"
widget_class "*Nautilus*Side*.GtkWidget"       style "murrine-nautilus-sidebar"
widget       "*Nautilus*Splitter"              style "pixmap-nautilus-handle"

# Toolbar appearance for Gedit sidepane
widget_class "*Gedit*Pane*"                    style "murrine-gedit-sidetoolbar"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" style "murrine-tooltips"

###################################################
# Special cases and work arounds
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "murrine-nautilus-location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
style "murrine-text-is-fg-color-workaround" {
  text[NORMAL]      = @fg_color
  text[PRELIGHT]    = @fg_color
  text[SELECTED]    = @selected_fg_color
  text[ACTIVE]      = @fg_color
  text[INSENSITIVE] = darker (@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>" style "murrine-text-is-fg-color-workaround"

style "murrine-menuitem-text-is-fg-color-workaround" {
  text[NORMAL]      = @fg_color
  text[PRELIGHT]    = @selected_fg_color
  text[SELECTED]    = @selected_fg_color
  text[ACTIVE]      = @fg_color
  text[INSENSITIVE] = darker (@bg_color)
}
widget "*.gtk-combobox-popup-menu.*" style "murrine-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the
# base color set.
style "murrine-fg-is-text-color-workaround" {
  fg[NORMAL]        = @text_color
  fg[PRELIGHT]      = @text_color
  fg[ACTIVE]        = @selected_fg_color
  fg[SELECTED]      = @selected_fg_color
  fg[INSENSITIVE]   = darker (@bg_color)
}
widget_class "*<GtkListItem>*" style "murrine-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree
# Only match GtkCList and not the parent widgets, because that would also
# change the headers.
widget_class "*<GtkCList>"     style "murrine-fg-is-text-color-workaround"
```

---

