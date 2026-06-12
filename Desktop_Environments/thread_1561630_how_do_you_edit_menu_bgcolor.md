---
title: "how do you edit menu bgcolor?"
date: 2010-08-26
forum: Desktop Environments
---

### Post by libihero on 2010-08-26
i absolutely love the faenza theme, but the problem with it is that the menu icons (such as create folder) are black.  this doesnt look good when the menu is already black, so how can i change the default background menu in the gtkrc?

i'm using impression and here is the gtkrc it has currently

```
#
# Name: Impression
# Author: John Baer <baerjj@gmail.com>
# Copyright: Creative Commons 3.0
# Date: August 2010
# Description: Ubuntu Community GTK Theme ( build: 69 - 100822 )
#
# **********************************************************************
# *********              A T T R I B U T I O N                 *********
# **********************************************************************
#
# This theme is based on the Ambiance theme by Kenneth Wimer
# <kwwii@ubuntu.com> and James Schriver <jws141@gmail.com>.
#
# **********************************************************************
# *********          Feel free to modify and share!            *********
# **********************************************************************
#
# Documentation: https://wiki.ubuntu.com/Artwork/Documentation/Murrine
#
# murrine engine: https://launchpad.net/~dashua/+archive/light-themes
#

# orange progressbar
gtk_color_scheme = "fg_color:#3c3b37\nbg_color:#ebe6e1\nbase_color:#ffffff\ntext_color:#3a3935"
gtk_color_scheme = "selected_bg_color:#d4cec7\nselected_fg_color:#222222"
gtk_color_scheme = "tooltip_bg_color:#000000\ntooltip_fg_color:#ffffff"
gtk_color_scheme = "link_color:#ff8433\nfocustrim_color:#eb785f\nprogressbar_color:#dd4814"
gtk_color_scheme = "black_color:#000000\nwhite_color:#ffffff\nerr_color:#ff00ff"

# **********************************************************************
# *********       A D D I T I O N A L   C O L O R S            *********
# **********************************************************************
# err_color                 #ff00ff
# focustrim_color           #eb785f - orange
# progressbar_color         #dd4814 - orange
# black_color               #000000
# white_color               #ffffff

# **********************************************************************
# *********               I S S U E   L O G                    *********
# **********************************************************************
#
# GtkToolbar::shadow-type = GTK_SHADOW_NONE
#   This disables toolbar background gradients
#
# Firefox scrollbars do not theme well with rounded
#   scrollbars.
#
# OpenOffice menus are tight. Unclear if tweaks can be applied
#   to wxGTK widgets.
#

gtk-icon-sizes = "panel-menu=22,22:gtk-button=16,16"

gtk-auto-mnemonics = 1

style "default"
{
  xthickness = 1
  ythickness = 1

  GtkWidget::new-tooltip-style = 1

  GtkImage::x-ayatana-indicator-dynamic = 1

  GtkScrolledWindow::scrollbar-spacing = 4
  GtkScrolledWindow::scrollbar-within-bevel = 0

  GtkButton::child-displacement-x = 1
  GtkButton::child-displacement-y = 1
  GtkButton::default-border = { 0, 0, 0, 0 }

  GtkCheckButton::indicator-size = 14

  GtkPaned::handle-size = 6

  GtkRange::trough-border = 2 # (1) space between bar and inner trough
  GtkRange::stepper-size = 15 # (14)
  GtkRange::trough-under-steppers = 0 # (1) include steppers in trough
  GtkRange::slider-width = 10 # (14)

  GtkScale::slider-length = 28
  GtkScale::trough-side-details = 1
  GtkScale::slider-width = 14 # button width
  GtkScale::slider-length = 14 # button length

  GtkScrollbar::min-slider-length = 36
  GtkScrollbar::activate-slider = 1
  # steppers
  GtkScrollbar::has-forward-stepper = 1
  GtkScrollbar::has-backward-stepper = 1
  GtkScrollbar::trough-border = 2
  GtkScrollbar::slider-width = 10

#  GtkMenuBar::internal-padding = 0 # (1)
  # http://library.gnome.org/devel/gtk/unstable/GtkExpander.html
  GtkExpander::expander-size = 11

  GtkToolbar::internal-padding = 5
  #GtkToolbar::shadow-type = GTK_SHADOW_NONE # see issue log

  GtkTreeView::expander-size = 15
  GtkTreeView::indent-expanders = 1
  GtkTreeView::vertical-separator = 0

  # don't know how to theme column shading :/
  GtkTreeView::odd_row_color = "#ededed"
  GtkTreeView::even_row_color = @white_color

  # thickness of progressbars
  GtkProgressBar::min-vertical-bar-width = 14
  GtkProgressBar::min-horizontal-bar-height = 14

  GtkMenu::horizontal-padding = 0
  GtkMenu::vertical-padding = 0

  WnckTasklist::fade-overlay-rect = 0
  # The following line hints to gecko (and possibly other appliations)
  # that the entry should be drawn transparently on the canvas.
  # Without this, gecko will fill in the background of the entry.
  GtkEntry::honors-transparent-bg-hint = 1
  GtkEntry::state-hint = 0

  GtkEntry::progress-border = { 2, 2, 2, 2 }
  GtkHandleBox::shadow-type = GTK_SHADOW_OUT

  GtkMenuBar::shadow-type = GTK_SHADOW_NONE
  GtkMenuBar::window-dragging = 1

  GtkStatusbar::has-resize-grip = TRUE

  GtkWidget::link-color = @link_color # main link
  GtkWidget::visited-link-color = shade ( 0.90, @link_color )
  GnomeHRef::link_color = @link_color
  GtkHTML::link-color = "#0000ff" # evolution email
  GtkIMHtml::hyperlink-color = @link_color
  GtkIMHtmlr::hyperlink-color = @link_color

  fg[NORMAL] = @fg_color
  fg[PRELIGHT] = @selected_fg_color
  fg[ACTIVE] = @fg_color
  fg[SELECTED] = @selected_fg_color
  fg[INSENSITIVE] = shade ( 0.50, @bg_color )

  bg[NORMAL] = @bg_color
  bg[PRELIGHT] = shade ( 1.02, @bg_color )
  bg[ACTIVE] = shade ( 0.80, @bg_color )
  bg[SELECTED] = @selected_bg_color
  bg[INSENSITIVE] = @bg_color

  base[NORMAL] = @base_color
  base[PRELIGHT] = shade ( 1.10, @selected_bg_color )
  base[ACTIVE] = shade ( 0.97, @selected_bg_color )
  base[SELECTED] = shade ( 1.05, @selected_bg_color )
  base[INSENSITIVE] = shade ( 1.00, @selected_bg_color )

  text[NORMAL] = @text_color
  text[PRELIGHT] = shade ( 1.20, @text_color )
  text[ACTIVE] = shade ( 1.10, @text_color )
  text[SELECTED] = shade ( 1.05, @text_color )
  text[INSENSITIVE] = shade ( 0.90, @text_color )

  engine "murrine"
  {
    animation = FALSE # FALSE = disabled, TRUE = enabled
    arrowstyle = 1 # 1 = filled arrows 2 = "v" arrows
    border_colors = FALSE # { "#ffffff", "#ffffff" } / FALSE colors used on borders of many widgets
    border_shades = { 1.20, 1.00 } # gradient to draw on border
    cellstyle = 1 # 0 = remove border, 1 = draw border around the selected cell
    colorize_scrollbar = FALSE # FALSE = disabled, TRUE = enabled
    comboboxstyle = 1 # 0 = normal combobox, 1 = colorized combobox below arrow
    contrast = 0.90 # 0.8 for less contrast, more than 1.0 for more contrast on borders
    default_button_color = mix ( 0.20, @focustrim_color, @bg_color ) # tint default button
    #disable_focus = TRUE # TRUE / FALSE
    expanderstyle = 2 # 0 = arrows, 1 = circles with plus and minus, 2 = buttons with plus and minus
    focus_color = @focustrim_color
    focusstyle = 3 # 0 = to disable focus drawing, 1 = to use dots, 2 = to use a small colored rectangle, 3 = to use a colored rectangle that touches the borders
    glazestyle = 3 # 0 = flat, 1 = curved, 2 = concave, 3 = top-curved, 4 = beryl
    glow_shade = 1.02 # sets glow amount for buttons or widgets
    glowstyle = 0 # 0 = top, 1 = bottom, 2 = top and bottom, 3 = center (vertical), 4 = center (horizontal), 5 = around the edges
    gradient_colors = FALSE # default to off
    gradient_shades = { 1.04, 1.0, 1.0, 0.96 } # default: {1.1,1.0,1.0,1.1}
    handlestyle = 0 # 0 = for three simple lines, 1 = for three simple lines with inset.
    highlight_shade = 1.00 # set highlight amount for buttons or widgets
    lightborder_shade = 1.10 # sets lightborder amount for buttons or widgets
    lightborderstyle = 1 # 0 = lightborder on top side, 1 = lightborder on all sides
    listviewheaderstyle = 1 # 0 = flat, 1 = glassy, 2 = raised
    listviewstyle = 2 # 0 = nothing, 1 = dotted 2 = solid
    menubaritemstyle = 0 # 0 = menuitem look, 1 = button look
    menubarstyle = 1 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
    menuitemstyle = 1 # 0 = flat, 1 = glassy, 2 = striped
    menustyle = 2 # 0 = no vertical menu stripe, 1 = display vertical menu stripe, 2 = ?
    prelight_shade = 1.00 # shade level for scrollbar's slider, comboboxstyle(1), and prelight state with gradient_colors
    progressbarstyle = 0 # 0 = no stripes, 1 = diagonal stripes, 2 = vertical stripes
    reliefstyle = 4 # 0 = flat, 1 = inset, 2 = shadow, 3 = shadow with gradient, 4 = stronger shadow with gradient
    rgba = FALSE # FALSE = disabled, TRUE = enabled
    roundness = 3 # 0 = squared, 1 = old default, more will increase roundness
    scrollbarstyle = 0 # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles
    separatorstyle = 1 # 1 to draw smooth separators
    shadow_shades = { 0.80, 2.20 } # draw gradient on shadow of some widgets
    sliderstyle = 0 # 0 = nothing added, 1 = handles, 2 = v, 3 = v & handles
    spinbuttonstyle = 0 # 0 = no seperator, 1 = with separator
    stepperstyle = 1 # 0 = standard, 1 = integrated stepper handles, 2 = squared steppers with round slider
    textstyle = 0 # 0 = normal text, 1 = shadow at the bottom, 2 = shadow at the top, 3 = shadow at the bottom right, 4 = shadow at the top left
    text_shade = 1.06 # 1.0 to specify the shade effect of the text's shadow
    toolbarstyle = 1 # 0 = flat, 1 = glassy, 2 = gradient
    trough_shades = { 0.90, 1.10 } # draw gradient on trough of GtkScrollbar
  }
}

# no style
style "widget_defaults"
{
}

# buttons & gtkview headers
style "selected" = "default"
{
  bg[NORMAL] = shade ( 1.00, @bg_color )
  bg[PRELIGHT] = shade ( 1.10, @bg_color )
  bg[SELECTED] = shade ( 0.95, @bg_color )
  bg[ACTIVE] = shade ( 0.90, @bg_color )
  bg[INSENSITIVE] = mix (0.30, @selected_bg_color, @bg_color)
}

style "dark"
{
  fg[NORMAL] = @white_color # menubar text ( light text on dark background )
  fg[PRELIGHT] = @white_color # menubar text ( light text on dark background )
  fg[ACTIVE] = shade ( 0.90, @fg_color )
  fg[SELECTED] = @white_color # shade ( 1.15, @fg_color )
  fg[INSENSITIVE] = shade ( 2.20, @fg_color ) # insensitive menu text

  # simular to button
  bg[NORMAL] = @selected_fg_color  # matches metacity title bar
  bg[PRELIGHT] = @selected_fg_color # menubar item background
  bg[ACTIVE] = shade ( 0.90, @selected_bg_color )
  bg[SELECTED] = shade ( 1.10, @selected_bg_color )
  bg[INSENSITIVE] = shade ( 0.85, @selected_bg_color )

  # defer to default
  #base[NORMAL] = @base_color
  #base[PRELIGHT] = shade ( 0.95, @base_color )
  #base[ACTIVE] = shade (0.90, @base_color)
  #base[SELECTED] = shade ( 0.85, @base_color )
  #base[INSENSITIVE] = shade ( 0.80, @base_color )

  text[NORMAL] = shade ( 0.95, @white_color )
  text[PRELIGHT] = shade ( 1.00, @white_color )
  text[ACTIVE] = shade ( 0.90, @white_color )
  text[SELECTED] = shade ( 0.85, @white_color )
  text[INSENSITIVE] = shade ( 0.70, @white_color )
}

style "thinner"
{
  xthickness = 0
  ythickness = 0
}

style "thin"
{
  xthickness = 1
  ythickness = 1
}

style "wide"
{
  xthickness = 2
  ythickness = 2
}

style "wider"
{
  xthickness = 3
  ythickness = 3
}

style "entry" = "wider"
{
  bg[SELECTED] = mix (0.40, @selected_bg_color, @base_color)
  fg[SELECTED] = @text_color

  engine "murrine"
  {
    border_shades = { 1.00, 1.00 }
    contrast = 0.80
  }
}

style "button" = "selected"
{
  xthickness = 3
  ythickness = 3

  engine "murrine"
  {
    contrast = 1.20
    glow_shade = 1.50
    gradient_shades = { 1.20, 1.00, 1.00, 0.87  }
    lightborder_shade = 1.06
  }
}

style "toolbar" = "default"
{
  bg[NORMAL] = shade ( 0.98, @bg_color )

  # provides better definition to toolbar buttons
  engine "murrine"
  {
    contrast = 0.80
    glazestyle = 1
    toolbarstyle = 1 # 1 = glassy
    gradient_shades = { 0.86, 0.96, 0.96, 1.00  }
  }
}

style "toolbar-handlebox" = "toolbar"
{
  bg[NORMAL] = shade(0.96, @bg_color)
}

style "notebook" = "wider"
{
  bg[NORMAL] = shade ( 1.02, @bg_color ) # Notebook primary tab
  bg[ACTIVE] = shade ( 0.65, @bg_color ) # Notebook secondary tabs
  bg[SELECTED] = shade ( 1.05, @bg_color )

  # Set to the same as roundness, used for better hotspot selection of tabs
  GtkNotebook::tab-curvature = 2.5
  GtkNotebook::tab-overlap = 0

  engine "murrine"
  {
    contrast = 1.00
    focusstyle = 0 # 0 = to disable focus drawing
    gradient_shades = { 2.55, 3.00, 4.00, 4.00 }
    roundness = 3
  }
}

style "notebook-label"
{
  fg[NORMAL] = @black_color # Text primary tab
  fg[ACTIVE] = mix ( 0.70, @progressbar_color, @selected_fg_color ) # Text secondary tabs

  engine "murrine"
  {
  }
}

style "panel" = "dark"
{
  bg_pixmap[NORMAL] = "images/panel/panel-bg-dark.svg" # desktop panels
  bg[NORMAL] = shade ( 0.30, @bg_color )

  xthickness = 0
  ythickness = 0

  engine "murrine"
  {
    border_colors = { @fg_color, @fg_color }
    border_shades = { 1.40, 1.20 }
    contrast = 1.0 # 0.8 for less contrast, more than 1.0 for more contrast on borders
    glow_shade = 0.90 # sets glow amount for buttons or widgets
    lightborder_shade = 0.90 # sets lightborder amount for buttons or widgets
    lightborderstyle = 0 # 0 = lightborder on top side, 1 = lightborder on all sides
  }
}

# https://lists.ubuntu.com/archives/maverick-changes/2010-May/000621.html
# default palette is tango
style "terminal"
{
  base[NORMAL] = @black_color # terminal screen background
  text[NORMAL] = @white_color # terminal screen text
  TerminalScreen::background-darkness = 0.85 # % transparency
}

style "menu" = "dark"
{
  xthickness = 0
  ythickness = 0

  engine "murrine"
  {
    border_shades = { 1.2, 0.80 }
    glow_shade = 1.05
    glowstyle = 4 # center (horizontal)
    gradient_shades = { 1.20, 1.00, 1.00, 0.80 }
    lightborder_shade = 1.7
    lightborderstyle = 1
    reliefstyle = 3
    roundness = 0
    shadow_shades = { 1.2, 0.8 }
  }
}

style "menu-item" = "wider"
{
  bg[SELECTED] = shade ( 1.70, @selected_fg_color ) # menu item background
  fg[PRELIGHT] = @white_color # prelight menubar text ( light text on dark background )

  GtkMenuItem::toggle-spacing = 6 # space between icon & text
  GtkMenuItem::horizontal-padding = 8 # space between left border & icon

  #xthickness = 0
  ythickness = 4

  engine "murrine"
  {
    glowstyle = 4 # center (horizontal)
    highlight_shade = 1.02
    lightborder_shade = 1.00
    roundness = 3
  }
}

style "separator-menu-item"
{
  bg[NORMAL]= shade ( 0.60, @selected_bg_color )

  #GtkSeparatorMenuItem::horizontal-padding = 6
  GtkWidget::wide-separators = 1
  GtkWidget::separator-width = 1
  GtkWidget::separator-height = 2

  xthickness = 4
  ythickness = 0

}

style "treeview-header" = "selected"
{
  GtkArrow::arrow-scaling = 0.6

  xthickness = 2
  ythickness = 1

  engine "murrine"
  {
    contrast = .8
  }
}

style "treeview" = "selected"
{

  bg[NORMAL] = shade ( 1.20, @selected_bg_color ) # separators
  base[ACTIVE] = shade ( 1.49, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # bar active
  base[SELECTED] = shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # bar selected

  engine "murrine"
  {
    contrast = .8
    focusstyle = 3 # 3 = to use a colored rectangle that touches the borders.
  }
}

style "tooltips"
{
  xthickness = 8
  ythickness = 5

  bg[NORMAL] = @tooltip_bg_color
  bg[SELECTED] = @black_color
  fg[NORMAL] = @tooltip_fg_color
}

style "progressbar" = "thinner"
{
  bg[NORMAL] = shade ( 1.00, @bg_color )
  bg[PRELIGHT] = shade ( 1.20, @bg_color )
  bg[ACTIVE] = @selected_bg_color # progress bar trough
  bg[SELECTED] = shade ( 1.00, mix ( 0.65, @progressbar_color, @selected_bg_color ) )

  fg[PRELIGHT] = @base_color

  engine "murrine"
  {
    # orange progressbar
    border_shades = { 1.00, 1.00 } # draw a gradient on the border.
    border_colors = { shade ( 1.00, mix ( 0.65, @progressbar_color, @selected_bg_color ) ), shade ( 1.00, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) } # blend to gradient
    contrast = 0.60
    glazestyle = 1 # 0 = flat, 1 = curved, 2 = concave, 3 = top-curved, 4 = beryl
    glow_shade = 1.02 # sets bar glow
    glowstyle = 4 # 4 = center (horizontal)
    gradient_shades = { 1.00, 0.96, 0.96, 1.00  }
    lightborder_shade = 1.00 # sets lightborder amount for bar
    roundness = 36 # there is a relationship between roundness and bar-width
    trough_shades = { 1.00, 1.20 } # draw gradient on trough of GtkProgressbar
  }
}

style "statusbar" = "default"
{
}

style "comboboxentry" = "wider"
{

  engine "murrine"
  {
    contrast = 1.00 # same as button
  }
}

style "spinbutton"
{
}

style "scale"
{
  bg[NORMAL] = shade ( 0.80, @bg_color ) # button
  bg[ACTIVE] = shade ( 0.80, @bg_color ) # Slider trough color
  bg[SELECTED] = shade ( 0.88, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # Slider trough color
  bg[PRELIGHT] = @white_color # button prelight

  GtkScale::trough-side-details = 1 # must be 1 for color trough
  GtkScale::trough-border = 0 # padding between button and end of bar
  GtkScale::focus-line-width = 0
  GtkScale::focus-padding = 4

  engine "murrine"
  {
    border_colors = { shade ( 1.60, @selected_fg_color ), shade ( 1.30, @selected_fg_color ) } # colors of button borders
    contrast = 1.25
    focus_color = mix ( 0.20, @progressbar_color, @bg_color )
    focusstyle = 0 # 0 = none
    glazestyle = 1 # 1 = curved
    glow_shade = 0.90 # sets glow amount for buttons or widgets
    glowstyle = 5 # 5 = edge
		gradient_shades = {1.1, 1.0, 1.0, 0.8}
		handlestyle = 2
    highlight_shade = 1.02 # set highlight amount for buttons or widgets
		lightborder_shade = 1.32
    sliderstyle = 0 # 3 = v & handles
    # this is not the button
    roundness = 36 # there is a relationship between roundness and trough-width
 		trough_border_shades = { 0.90, 1.40 }
  }
}

style "hscale" = "scale"
{
}

style "vscale" = "scale"
{
}

style "scrollbar" = "selected"
{
  bg[NORMAL] = shade ( 0.40, @bg_color )
  bg[ACTIVE] = shade ( 0.60, @bg_color )
  bg[PRELIGHT] = shade ( 1.00, mix ( 0.65, @progressbar_color, @selected_bg_color ) )
  bg[INSENSITIVE] = shade ( 0.60, @bg_color )

  # uncomment for disappearing arrows
  fg[NORMAL] = shade ( 2.00, @bg_color )
  fg[INSENSITIVE] = shade ( 2.00, @bg_color )

  engine "murrine"
  {
    border_shades = { 0.88, 1.12 } # bar border
    border_colors = { shade ( 0.88, @bg_color ), shade ( 1.12, @bg_color ) } # blend to trough
    contrast = 0.20 # to erase trough lines
    glazestyle = 3 # 3 = top-curved
    glow_shade = 1.00 # sets glow amount for buttons or widgets
    glowstyle = 4 # 4 = center (horizontal)
    highlight_shade = 1.00 # set highlight amount for buttons or widgets
    lightborder_shade = 1.0 # sets lightborder amount for buttons or widgets
    gradient_shades = { 1.00, 0.96, 0.96, 1.00 }
    roundness = 36 # there is a relationship between roundness and trough-width
    scrollbarstyle = 0 # nothing
    trough_shades = { 0.82, 1.22 } # draw gradient on trough of GtkProgressbar
  }
}

style "hscrollbar"
{
}

style "vscrollbar"
{
}

style "menubar" = "dark"
{
  bg[SELECTED] = shade ( 1.30, @selected_fg_color ) # menubar item background

  xthickness = 0
  ythickness = 4
}

style "panel-menubar" = "menubar"
{
  # this is the panel menu bar
  engine "murrine"
  {
    border_shades = { 1.2, 0.8 }
    contrast = 0.20
    focus_color = shade ( 0.50, @bg_color )
    glazestyle = 0 # flat
    glowstyle = 4 # center (horizontal)
    #gradient_shades = { 1.65, 1.15, 1.05, 0.70 }
    gradient_shades = { 1.85, 1.45, 1.25, 0.80 }
    lightborder_shade = 1.7
    lightborderstyle = 0
    menuitemstyle = 1 # glassy
    reliefstyle = 3
    roundness = 4
  }
}

style "frame" = "wide"
{
  bg[NORMAL] = shade ( 1.07, @selected_bg_color ) # frame lines
}

style "frame-title" = "frame"
{
}

style "nautilus-default"
{
  bg[NORMAL] = @base_color # info / emblem view

  base[NORMAL] = @base_color
  base[ACTIVE] = shade ( 1.49, mix ( 0.65, @progressbar_color, @selected_bg_color ) )
  base[SELECTED] = shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) )

  engine "murrine"
  {
    contrast = .8
  }
}

style "nautilus-iconview"
{
  #base[NORMAL] = @base_color
  base[SELECTED] = shade ( 0.70, @selected_bg_color )

  text[SELECTED] = @white_color

  engine "murrine"
  {
    contrast = 0.80
  }
}

style "nautilus-location"
{
  bg[NORMAL] = mix(0.60, @bg_color, @selected_bg_color)
}

style "nautilus-sidebar" = "thin"
{
  GtkTreeView::even_row_color = @base_color # shade ( 1.12, @selected_bg_color ) # this colors the panel

  bg[NORMAL]= @selected_bg_color # separator line

  engine "murrine"
  {
    contrast = 0.80
    gradient_colors = { shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) ), shade ( 1.31, mix ( 0.65, @progressbar_color, @selected_bg_color ) ), shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) ), shade ( 1.25, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) } # custom gradient
  }
}

style "radiocheck"
{
  bg[NORMAL] = mix ( 0.30, @selected_bg_color, @bg_color )
  bg[SELECTED] = @focustrim_color

  engine "murrine"
  {
    contrast = 0.60
    highlight_shade = 1.00
    lightborder_shade = 1.00
    focusstyle = 1 # 1 = dots
    gradient_shades = { 1.50, 1.30, 1.00, 0.90 }
  }
}

style "applet-text" = "panel"
{
  fg[NORMAL] = @bg_color
}

#########################################
# Matches
#########################################

widget "*IdoScaleMenuItem*" style "scale"
widget "*IdoEntryMenuItem*" style "wider"
widget "ido-offscreen-scale" style "widget_defaults"

# default style is applied to every widget
class "GtkWidget" style "default"

# Increase the x/ythickness in some widgets
class "GtkToolbar" style "toolbar"
class "GtkRange" style "wide"
class "GtkFrame" style "frame"
class "GtkSeparator" style "wide"
class "GtkEntry" style "entry"

class "GtkSpinButton" style "spinbutton"
class "GtkScale" style "scale"
class "GtkVScale" style "widget_defaults"
class "GtkHScale" style "widget_defaults"
class "GtkScrollbar" style "scrollbar"
class "GtkVScrollbar" style "vscrollbar"
class "GtkHScrollbar" style "hscrollbar"

class "GtkRadioButton" style:highest "radiocheck"
class "GtkCheckButton" style:highest "radiocheck"

widget_class "*HandleBox" style "toolbar-handlebox"

widget_class "*HandleBox" style "toolbar-handlebox"
widget_class "*<GtkToolbar>.*" style "toolbar"
widget_class "*<GtkToolbar>*<GtkScale>" style "scale"

widget_class "*<GtkNotebook>*<GtkEventBox>" style "notebook"
widget_class "*<GtkNotebook>*<GtkDrawingArea>" style "notebook"
widget_class "*<GtkNotebook>*<GtkLayout>" style "notebook"
widget_class "*<GtkNotebook>*<GtkViewport>" style "notebook"
widget_class "*<GtkNotebook>*<GtkScrolledWindow>" style "notebook"
widget_class "*.GtkNotebook.GtkLabel*" style "notebook-label"

widget_class "*<GtkButton>" style "button"
widget_class "*<GtkNotebook>" style "notebook"
widget_class "*<GtkStatusbar>*" style "statusbar"

widget_class "*<GtkComboBoxEntry>*" style:highest "comboboxentry"
widget_class "*<GtkComboBox>*" style:highest "comboboxentry"
widget_class "*<GtkOptionMenu>*" style:highest "comboboxentry"
widget_class "*<GtkCombo>*" style:highest "comboboxentry"

widget_class "*<GtkMenuBar>*" style "menubar"
widget_class  "*<GtkMenuBar>*<GtkMenuItem>*" style:highest "panel-menubar"
widget_class "*Panel*<GtkMenuBar>*" style:highest "panel-menubar"
widget_class "*<GtkMenu>*" style "menu"
widget_class "*<GtkMenuItem>*" style "menu-item"
widget_class "*<GtkSeparatorMenuItem>*" style "separator-menu-item"
#widget_class "*<GtkCheckMenuItem>*" style "radiocheck"
#widget_class "*<GtkRadioMenuItem>*" style "radiocheck"

widget_class "*.<GtkFrame>.<GtkLabel>" style "frame-title"
widget_class "*.<GtkTreeView>*" style "treeview"

widget_class "*<GtkProgressBar>" style "progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" style "treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>" style "treeview-header"
widget_class "*.<GtkList>.<GtkButton>" style "treeview-header"
widget_class "*.<GtkCList>.<GtkButton>" style "treeview-header"

# theme gtk calendar to match evolution ;)
style "calendar" = "radiocheck"
{
  bg[NORMAL] = shade ( 1.00, @bg_color ) # Title background / insensitive days

  base[NORMAL] = @base_color # background
  base[ACTIVE] = @base_color
  base[SELECTED] = shade ( 1.42, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # today

  text[NORMAL] = @selected_fg_color
  text[ACTIVE] = shade ( 0.90, @progressbar_color ) # today & days of week in title
  text[SELECTED] = @black_color

}
widget_class "*<GtkCalendar>*" style "calendar"

# Workarounds for Evolution

style "GtkECalendar" = "radiocheck"
{
  bg[NORMAL] = shade ( 1.00, @bg_color ) # Title background / insensitive days
  bg[SELECTED] = shade ( 1.42, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # border of today

  base[NORMAL] = @base_color # background
  base[ACTIVE] = shade ( 1.42, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # today
  base[SELECTED] = @base_color # background Mon - Sun header

  fg[NORMAL] = @selected_fg_color # days of week & month

  text[ACTIVE] = shade ( 0.80, @progressbar_color ) # today & days of week in title
}
widget_class "*.ECalendar" style "GtkECalendar"

style "GtkETreeView" = "selected"
{
  # make it the same as other treeviews :)
  bg[ACTIVE] = shade ( 1.42, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # active bar active
  bg[SELECTED] = shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # select bar selected

  engine "murrine"
  {
    contrast = 0.75
    glazestyle = 0 # 0 = flat highlight, 1 = curved highlight, 2 = concave style, 3 = top curved highlight, 4 = beryl highlight
    gradient_shades = { 1.2, 1.0, 1.0, 0.87  } # TreeHeader
    roundness = 0
  }
}
widget_class "*.ETree.*" style "GtkETreeView"
widget_class "*.ETree.ECanvas" style "GtkETreeView"
widget_class "*.ETable.ECanvas" style "GtkETreeView"

# Theme panel elements
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
widget "*fast-user-switch*" style "panel" # workaround for Fast User Switch applet
class "PanelApp*" style "panel"
class "PanelToplevel*" style "panel"
widget_class "*notif*" style "panel"
widget_class "*Notif*" style "panel"
widget_class "*CPUFreqApplet*" style:highest "applet-text" # CPU Frequency Applet

#XFCE panel
widget_class "*notif*" style "panel"
widget_class "*Notif*" style "panel"
widget_class "*Tray*" style "panel"
widget_class "*tray*" style "panel"
widget "*Xfce*Panel*" style "panel"
class "*Xfce*Panel*" style "panel"

#Fix textboxes on toolbars (memenu LP:#532843)
style "text-dark" = "default"
{
}

widget_class "*<GtkToolbar>*<GtkEntry>*" style "text-dark"
widget_class "*<GtkMenu>*<GtkEntry>*" style "text-dark"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" style "tooltips"

###################################################
# Special cases and work arounds
###################################################

#widget "*Nautilus*Desktop*" style "nautilus-default"

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style:highest "nautilus-location"

# Nautilus tweaks
widget_class "*NautilusPlacesSidebar*" style:highest "nautilus-default"
widget_class "*NautilusHistorySidebar*" style:highest "nautilus-default"

widget_class "*Nautilus*Side*.GtkWidget" style "nautilus-sidebar"
widget_class "*NautilusSidePane*Notes*" style "nautilus-default"
widget_class "*NautilusSidePane*GtkNotebook*" style "nautilus-default"

widget_class "*Nautilus*IconView*" style "nautilus-iconview"
widget_class "*Nautilus*IconView*Scroll*" style:highest "scrollbar"

widget "*NautilusSidePane*Information*" style "nautilus-default"
widget "*NautilusSidePane*GtkNotebook*Scroll*" style:highest "scrollbar"
widget "*NautilusEmblemSidebar*GtkViewport*" style:highest "nautilus-default"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that the work around assumes that the combobox is _not_ in
# appears-as-list mode.
# Similar hack also in the menuitem style.
# This style does not affect GtkComboBoxEntry, it does have an effect
# on comboboxes in appears-as-list mode though.
style "combobox-text-color-workaround"
{
  text[NORMAL] = @fg_color
  text[PRELIGHT] = @fg_color
  text[ACTIVE] = @fg_color
  text[SELECTED] = @selected_fg_color
  text[INSENSITIVE] = shade (0.65, @bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>" style "combobox-text-color-workaround"

style "menuitem-text-is-fg-color-workaround"
{
  text[NORMAL] = @bg_color # "#dfd8c8"
  text[PRELIGHT] = @base_color
  text[SELECTED] = @base_color
  text[ACTIVE] = @base_color
  text[INSENSITIVE] = darker ( @bg_color ) # "#99958b"
}

widget "*.gtk-combobox-popup-menu.*" style "menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the
# base color set.
style "fg-is-text-color-workaround"
{
  fg[NORMAL] = @text_color
  fg[PRELIGHT] = @text_color
  fg[ACTIVE] = @selected_fg_color
  fg[SELECTED] = @selected_fg_color
  fg[INSENSITIVE] = shade (0.65, @bg_color)
}

widget_class "*<GtkListItem>*" style "fg-is-text-color-workaround"

# The same problem also exists for GtkCList and GtkCTree
# Only match GtkCList and not the parent widgets, because that would also change the headers.
widget_class "*<GtkCList>" style "fg-is-text-color-workaround"

style "evo-new-button-workaround"
{
  engine "murrine"
  {
    toolbarstyle = 0
  }
}

widget "*swt*toolbar*" style "default"
class "TerminalScreen" style "terminal"

# banshee workaround
# add color to left treeview
style "banshee-treeview"
{
  bg[SELECTED] = shade ( 1.30, mix ( 0.65, @progressbar_color, @selected_bg_color ) ) # bar selected

  engine "murrine"
  {
  }
}

style "banshee-toolbar"
{
  fg[NORMAL] = shade ( 0.50, mix ( 0.65, @progressbar_color, @selected_bg_color ) )

  engine "murrine"
  {
  }
}

widget "__gtksharp_1*View*" style "banshee-treeview"
widget "__gtksharp_1*SeekSlider*" style "scale"
#widget "__gtksharp_1*Player*croll*" style "scrollbar"
widget_class "__gtksharp_1*<GtkButton>*" style "button"
widget_class "__gtksharp_1*<GtkScale>*" style "scale"
widget_class "__gtksharp_1*<GtkToolbar>*" style "banshee-toolbar"

# firefox scrollbars
# round scrollbars don't theme well with firefox :(
style "firefox-scrollbar" = "scrollbar"
{
  #GtkScrollbar::has-forward-stepper = 0
  #GtkScrollbar::has-backward-stepper = 0
  GtkScrollbar::trough-border = 3
  #GtkScrollbar::slider-width = 8

  # = 4 # (1) space between bar and inner trough
  #GtkRange::slider-width = 10 # (14)

  engine "murrine"
  {
  }
}

widget "MozillaGtkWidget*Scrollbar*" style:highest "firefox-scrollbar"
widget  "MozillaGtkWidget*Statusbar*" style:highest "wider"
#widget "MozillaGtkWidget*GtkProgressBar*" style:highest "firefox-progressbar"
#widget "MozillaGtkWidget.GtkFixed.GtkHandleBox.GtkToolbar" style "theme-dark-toolbar"
#widget "MozillaGtkWidget.GtkFixed.GtkEntry"  style "theme-dark-entry"
#widget "MozillaGtkWidget.GtkFixed.GtkButton" style "theme-dark-button"

# nautilus breadcrums
style "nautilus-breadcrum-text"
{
  fg[NORMAL] = @text_color
  fg[ACTIVE] = @selected_fg_color # when pressed
  fg[PRELIGHT] = shade ( 0.90, mix ( 0.98, @progressbar_color, @selected_bg_color ) ) # mouse over
  fg[SELECTED] = @selected_fg_color
  fg[INSENSITIVE] = shade ( 0.50, @bg_color )

}

style "nautilus-breadcrum"
{
  ythickness = 0
  xthickness = 10 # Spacing between arrow pathbar buttons

  GtkButton::child-displacement-y = 0
  GtkButton::child-displacement-x = 0
  GtkButton::inner-border = {0, 13, 0, 0} # Spacing between arrow pathbar buttons

  engine "pixmap"
  {
    image
    {
    function = BOX
    state = NORMAL
    file = "images/nautilus/pathbar-arrow-right.svg"
    border = { 0, 13, 0, 0 }
    stretch = TRUE
    }

    image
    {
    function = BOX
    state = ACTIVE
    file = "images/nautilus/pathbar-arrow-right.svg"
    border = { 0, 13, 0, 0 }
    stretch = TRUE
    }

    image
    {
    function = BOX
    state = PRELIGHT
    file = "images/nautilus/pathbar-arrow-left.svg"
    border = { 0, 13, 0, 0 }
    stretch = TRUE
    }

    image
    {
    function = BOX
    state = SELECTED
    file = "images/nautilus/pathbar-arrow-left.svg"
    border = { 0, 13, 0, 0 }
    stretch = TRUE
    }

    #grey square fix#
    image
    {
    function = BOX
    state = INSENSITIVE
    file = "images/null.png"
    border = { 0, 13, 0, 0 }
    stretch = TRUE
    }
  }
}

#Pathbar/Location Bar Arrows
widget "*Gtk*PathBar*Button" style "nautilus-breadcrum"
widget "*Gtk*PathBar*Button*Label*" style "nautilus-breadcrum-text"
widget "*Gtk*PathBar*Button*Arrow" style "nautilus-breadcrum" # 1st arrow
```

I want to change the background color to #F0F0F0 and the text color to #1F1F1F

---

