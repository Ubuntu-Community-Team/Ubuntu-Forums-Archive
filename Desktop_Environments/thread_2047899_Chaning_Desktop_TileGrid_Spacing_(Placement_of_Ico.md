---
title: "Chaning Desktop Tile/Grid Spacing (Placement of Icons)"
date: 2012-08-25
forum: Desktop Environments
---

### Post by neu5eeCh on 2012-08-25
I recall reading, somewhere, that the spacing of the XFCE desktop "grid" could be changed somewhere, allowing icons to be grouped closer together. Does anyone recall where this change should be made?

---

### Post by neu5eeCh on 2012-08-25
OK. Solved by googling.

I'm using 4.10. The desktop grid can be adjusted via the ~/.gtkrc-2.0 file.

The instructions for editing the file are here: usr/share/doc/xfdesktop4-data/README

And here is the content:

> README for xfdesktop
================================

WHAT IS IT?
~~~~~~~~~~~

Xfdesktop is a desktop manager for the Xfce Desktop Environment. Desktop 
in this respect means the root window (or, rather, a window that sits on top
of the root window). The manager handles the following tasks:
- background image / color
- root menu, window list
- minimized app icons
- file icons on the desktop (using Thunar libs)


MINIMUM REQUIREMENTS
~~~~~~~~~~~~~~~~~~~~

* intltool 0.34
* GTK+ 2.14.0
* libxfce4util 4.8
* libxfce4ui 4.9
* libwnck 2.22
* libexo 0.6
* xfconf 4.8
* garcon 0.1.2 (optional; required for apps menu)
* thunar 1.2 (optional; required for file icons)
* dbus-glib 0.34  (optional; required for file icons)
* tumbler 1.6 (optional; enables thumbnail previews for file icons)


HIDDEN CUSTOMISATIONS
~~~~~~~~~~~~~~~~~~~~~

If you're using the icon view, and would like to change how the text looks,
you have three things you can change: the opacity (transparency) of the
rounded text background, the color of the rounded text background, and the
color of the text itself.

You'd want to add something like this to your ~/.gtkrc-2.0 file:

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75
    XfdesktopIconView::selected-label-alpha = 100
    XfdesktopIconView::ellipsize-icon-labels = 1
    XfdesktopIconView::tooltip-size = 128

    XfdesktopIconView::shadow-x-offset = 1
    XfdesktopIconView::shadow-y-offset = 1
    XfdesktopIconView::shadow-color = "#ff0000"
    XfdesktopIconView::selected-shadow-x-offset = 2
    XfdesktopIconView::selected-shadow-y-offset = 2
    XfdesktopIconView::selected-shadow-color = "#00ff00"

    XfdesktopIconView::cell-spacing = 6
    XfdesktopIconView::cell-padding = 6
    XfdesktopIconView::cell-text-width-proportion = 2.5

    base[NORMAL] = "#00ff00"
    base[SELECTED] = "#5050ff"
    base[ACTIVE] = "#0000ff"

    fg[NORMAL] = "#ff0000"
    fg[SELECTED] = "#ff0000"
    fg[ACTIVE] = "#ff0000"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

The first four entries set the opacity of the rounded text background
(allowed values are from 0 (totally transparent) to 255 (totally opaque),
and whether or not unselected icons get their labels ellipsized
(truncated) to fit on one line.  (The 'selected-' version controls the
opacity of icons that have been selected with the mouse.) The tooltip-size
determines how large the image preview will be when the mouse is hovered
over an icon (allowed values are from 0 (not shown) to 512, values larger
than 256 may cause poor image quality however.)

The second six entries can be used to enable a text shadow to be painted
with the icon labels.  The offsets are in pixels.  Setting them to 0 (the
defaults) will disable the shadows entirely.  Again, the 'selected-'
versions apply to icons that have been selected with the mouse.

The third four entries set spacing and sizing for individual icons on
the grid.  The 'cell-spacing' property specifies the spacing between each
'cell' in the grid of icons.  The 'cell-padding' property sets extra
padding placed around each icon+text.  The units for these two are in
pixels.  The 'cell-text-width-proportion' property specifies the maximum
width of the text label underneat the icon, as a multiplier of the icon
width (so for 30px icons, '2.5' would leave a 75px wide area underneath
for the text).

The fourth three entries set the color of the rounded text background.
* NORMAL sets the color for the regular, unselected state.
* SELECTED sets the color for when the icon is selected, and the desktop has
  keyboard/mouse focus.
* ACTIVE sets the color for when the icon is selected, but the desktop does
  not have keyboard/mouse focus.

The final three entries set the color of the label text.  See above for the
differences between NORMAL, SELECTED, and ACTIVE.

Copy & paste this:

> 
    XfdesktopIconView::cell-spacing = 6
    XfdesktopIconView::cell-padding = 6
    XfdesktopIconView::cell-text-width-proportion = 2.5

into your ~/.gtkrc-2.0 file.

The most important variable for reducing the grid is the third variable. I changed it to 1.8 rather than 2.5.

To see how adjusting the variables changes your desktop icon placement, issue the command:

> killall xfdesktop 

in terminal. The desktop should automatically restart.

---

### Post by vasa1 on 2012-08-25
> **VTPoet said:**
> OK. Solved by googling.

I'm using 4.10. The desktop grid can be adjusted via the ~/.gtkrc-2.0 file.

...
Some of these settings can also be adjusted via the gtkrc file in ~/.themes/theme_name/gtk-2.0. I realized that when I switched to the Greybird theme. This theme has a section for the Xfce desktop.

I prefer _not_ having a .gtkrc-2.0 file because that way each theme will do its own thing. Currently, the ~/.gtkrc-2.0 file seems to have the final say and it is not theme-specific.

I'm in the process of getting all my stuff out of gtkrc-2.0 and into gtkrc.

Of course, this is with reference to Xfce.

---

