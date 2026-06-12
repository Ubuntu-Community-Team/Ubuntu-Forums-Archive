---
title: "how to modify a theme?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Tares on 2011-10-19
hello,

as the title says. Is it possible to modify a theme? I want to change color of the highlighted items not the whole theme.

---

### Post by LarsKongo on 2011-10-19
Yep, locate the theme your using. It's either installed in */usr/share/themes* or *~/.themes*. Then locate your theme's gtkrc file in the gtk-2.0 folder. Open it in a text editor.

Which highlights do you want to change btw?
CTRL+F button/menu/menubar or whatever it is you that you wish to change.
Change bg[PRELIGHT] for the background color and fg[PRELIGHT] for the text color.

Window controls (close/min/max and titlebar text) works a bit different. They're located in a xfwm4 folder and contains a configuration file and maybe some images too.

---

### Post by Tares on 2011-10-19
To be exact I want to change desktop icon text and text background color.

---

### Post by LarsKongo on 2011-10-19
Try to add this at the bottom in the gtkrc file:
```
style "xfdesktop-icon-view" {
	bg[ACTIVE] = "#0000FF" # selected bg color
	bg[SELECTED] = "#0000FF" # selected bg color
	fg[ACTIVE] = "#ffffff" # selected text color
	fg[SELECTED] = "#ffffff" # selected text color
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```
Just change #0000FF and #ffffff to the colors you would like to use. (HTML colors.)

---

### Post by Tares on 2011-10-20
Thanks. I've modified it a little bit and used this:
```
style "xfdesktop-icon-view" {
        XfdesktopIconView::label-alpha = 0
        bg[NORMAL] = "#000000" # normal bg color
        fg[NORMAL] = "#ffffff" # normal text color
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```
On other forums I've found that you can paste it to ~/.gtkrc-2.0 but it didn't worked. So when you said to paste it actually to the theme itself it finally started to work. Thanks a lot.

Topic can be closed/marked as solved.

---

### Post by ankspo71 on 2011-10-20
Hi,
Here is some more info on this:
 [http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/](http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/)

---

