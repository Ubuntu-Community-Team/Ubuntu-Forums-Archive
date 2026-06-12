---
title: "greybird mods"
date: 2011-07-01
forum: Desktop Environments
---

### Post by rabideau on 2011-07-01
For those who are using greybird on Xubuntu, here are my gtk-2.0 mods to clean up the desktop, remove the icon text label backgrounds and tighten up the layout to fit better on a netbook.  Create or modify a file called ==> .gtkrc-2.0 
If you have one you should find it in your home/user_name/ directory.  If you don't already have one, simply create one and add the text below to the new file and save it in your home/user_name directory.

Enjoy.


# This file was written by Mark Rabideau.
# You can do with this what you will.  I make no guarantees....

include "/usr/share/themes/greybird/gtk-2.0/gtkrc"

style "user-font"
{
    font_name="Droid Sans 9"
}
widget_class "*" style "user-font"

gtk-theme-name="greybird"
gtk-font-name="Droid Sans 8"

style "xfdesktop-icon-view" {
# label setting for transparency  
XfdesktopIconView::label-alpha = 0

# text shadows on icon labels
XfdesktopIconView::shadow-x-offset = 1
XfdesktopIconView::shadow-y-offset = 1
XfdesktopIconView::selected-shadow-x-offset = 0
XfdesktopIconView::selected-shadow-y-offset = 0
XfdesktopIconView::shadow-color = "#080808"
XfdesktopIconView::selected-shadow-color = "#000000"

# icon and text spacing
XfdesktopIconVIew::cell-spacing = 1 
XfdesktopIconView::cell-padding = 1 
XfdesktopIconView::cell-text-width-proportion = 2.5 

base[NORMAL] = "#ffffff"
base[SELECTED] = "#CECECE"
base[ACTIVE] = "#78869A"

fg[NORMAL] = "#CECECE"
fg[SELECTED] = "#1A1A1A"
fg[ACTIVE] = "#1A1A1A"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

#end of the greybird mods

---

