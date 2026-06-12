---
title: "Panel Adjustments"
date: 2014-02-23
forum: Desktop Environments
---

### Post by JazzyJeff502 on 2014-02-23
Would anyone happen to know how to adjust the font size of the text in panels? I've tried adjusting the row height, but that only increases/decreases the size of icons in the panel. I'm also not sure how to change the font of the panel text.

---

### Post by Toz on 2014-02-23
Try adding the following code to ~/.gtkrc-2.0 (create the file if it doesn't exist):
```
style "panel-font" {
     font_name = "Sans 16"
}
widget_class "*Panel*" style "panel-font"
widget "*PanelWidget*" style "panel-font"
widget "*PanelApplet*" style "panel-font"
widget "*Panel*" style "panel-font"
widget_class "*Panel*" style "panel-font"
class "*Panel*" style "panel-font"
class "*Tray*" style "panel-font"
class "*tray*" style "panel-font"
```
...change the font name and size to suit. You'll need to restart the panel for the change to take effect:
```
xfce4-panel -r
```

---

### Post by Bucky Ball on 2014-02-24
You can use 'Applications>Settings>Appearance>Fonts' but this will resize fonts globally.

---

