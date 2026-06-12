---
title: "How to change desktop icons (Trash, File System, Home) name"
date: 2014-04-02
forum: Desktop Environments
---

### Post by kosiek2 on 2014-04-02
Hi. How to change desktop icons text. I have this icons locale pl name, and i want to change it. Where can i do this? I have xubuntu with default theme chosen.

---

### Post by slickymaster on 2014-04-02
Hi kosiek2, welcome to the forums.

I'm not sure if I understood what you intend. Do you want to change the icons' names, or do you want to change the font used in the icons' names?

If you want to change the icons' names, just right-click any icon on your desktop and choose the **Properties...** option from the context menu and in the 'General' tab you'll have a _Name:_ text-box where you can change the icon name.

If you want to change the font used in the icons' names, just right click your desktop and select the **Desktop Settings...** option, navigate to the icons tab and use _Use custom font size:_ picklist to set the the font size to your convenience

---

### Post by kosiek2 on 2014-04-02
Yest I want to change the icon's names. But only desktop (system) icons like: home directory, file system, trash and removable devices (? i don't know how it names original). Try to click right on trash and go to properties?

---

### Post by slickymaster on 2014-04-02
With those you can perform some customization, but not changing their label text though, because they're handled by Xfdesktop, which is the desktop manager for the Xfce Desktop Environment. Desktop in this respect means the root window (or, rather, a window that sits on top of the root window).

If you'd like to change how the text looks, you have three things you can change: the opacity (transparency) of the rounded text background, the color of the rounded text background, and the color of the text itself.

You'd want to add something like this to your **~/.gtkrc-2.0** file (if this file doesn't exist in your system, just create one):
```
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

    XfdesktopIconView::cell-spacing = 2
    XfdesktopIconView::cell-padding = 6
    XfdesktopIconView::cell-text-width-proportion = 1.9

    base[NORMAL] = "#00ff00"
    base[SELECTED] = "#5050ff"
    base[ACTIVE] = "#0000ff"

    fg[NORMAL] = "#ff0000"
    fg[SELECTED] = "#ff0000"
    fg[ACTIVE] = "#ff0000"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

The first four entries set the opacity of the rounded text background (allowed values are from 0 (totally transparent) to 255 (totally opaque), and whether or not unselected icons get their labels ellipsized (truncated) to fit on one line.  (The 'selected-' version controls the opacity of icons that have been selected with the mouse.) The tooltip-size determines how large the image preview will be when the mouse is hovered over an icon (allowed values are from 0 (not shown) to 512, values larger than 256 may cause poor image quality however.)

The second six entries can be used to enable a text shadow to be painted with the icon labels.  The offsets are in pixels.  Setting them to 0 (the defaults) will disable the shadows entirely.  Again, the 'selected-' versions apply to icons that have been selected with the mouse.

The third four entries set spacing and sizing for individual icons on the grid.  The 'cell-spacing' property specifies the spacing between each 'cell' in the grid of icons.  The 'cell-padding' property sets extra padding placed around each icon+text.  The units for these two are in pixels.  The 'cell-text-width-proportion' property specifies the maximum width of the text label underneath the icon, as a multiplier of the icon width.

The fourth three entries set the color of the rounded text background.
* NORMAL sets the color for the regular, unselected state.
* SELECTED sets the color for when the icon is selected, and the desktop has keyboard/mouse focus.
* ACTIVE sets the color for when the icon is selected, but the desktop does not have keyboard/mouse focus.

The only way I see to achieve what you want is to grab Xfdesktop source (which you can get from [here]("http://git.xfce.org/xfce/xfdesktop/tree/src/xfdesktop-special-file-icon.c")), change it and compile it against your system, or **for a simpler solution just file a bug report and request that new feature**.

---

