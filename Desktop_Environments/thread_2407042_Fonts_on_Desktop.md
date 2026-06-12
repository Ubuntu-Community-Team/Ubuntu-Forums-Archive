---
title: "Fonts on Desktop"
date: 2018-11-29
forum: Desktop Environments
---

### Post by zkab on 2018-11-29
When I drag-drop icons from Application Finder to desktop then the fonts look terrible.
How do I change the fonts?

---

### Post by ajgreeny on 2018-11-29
Go to **Settings Manager -> Appearance -> Fonts** tab and make changes there to the font used and its size.

You can also play around with the **Rendering** settings in the same Fonts tab which may make a difference to the display of fonts.

---

### Post by zkab on 2018-11-29
But that changes everything  ... panel. application finder ... I just want to change the font of the icons residing on the desktop

---

### Post by Dennis N on 2018-11-29
You can change text size in Deskttop Settings > Icons > Custom Font Size, and you can change characteristics of the text shadow under the letters, such as its offset and color. Also looks like you can change text color? All that can change the appearance of the text. These settings can be edited in the theme's gtk-2.0/gtkrc file, assuming your Xubuntu is old enough to be using gtk2.0 for that. I think 16.04 does - not sure about 18.04. Look at the section: style="xfdesktop-icon-view" within that file and experiment.

---

### Post by zkab on 2018-11-30
I could change the text size with Deskttop Settings > Icons > Custom Font Size but not the text shadow or color.
In the file /usr/share/themes/Greybird/gtk-2.0/gtkrc I found the section style "xfdesktop-icon-view" but I am not sure how to change color & shadow for text ...


```
style "xfdesktop-icon-view"
{
	XfdesktopIconView::label-alpha = 0
	XfdesktopIconView::selected-label-alpha = 80
	XfdesktopIconView::shadow-x-offset = 0
	XfdesktopIconView::shadow-y-offset = 1
	XfdesktopIconView::selected-shadow-x-offset = 0
	XfdesktopIconView::selected-shadow-y-offset = 1
	XfdesktopIconView::shadow-color = shade(1.5, @tooltip_bg_color)
	XfdesktopIconView::selected-shadow-color = shade(1.8, @tooltip_bg_color)
        XfdesktopIconView::shadow-blur-radius = 2
	XfdesktopIconView::cell-spacing = 2
	XfdesktopIconView::cell-padding = 6
	XfdesktopIconView::cell-text-width-proportion = 1.9

	fg[NORMAL] = shade (0.9, @selected_fg_color)
	fg[ACTIVE] = @selected_fg_color

	engine "murrine"
	{
	}
}

```

---

### Post by Dennis N on 2018-11-30
> I am not sure how to change color & shadow for text ...

Text Color:

Change this line:
```
fg[NORMAL] = shade (0.9, @selected_fg_color) 

```
to a color code:
```
fg[NORMAL] = "#FF0000"
```
fg[NORMAL] is text color when not selected. The one after this, fg[ACTIVE], is the color when you right-click on the icon. You could change that too.
As for shadow, I think (didn't try it) you can change the x-offset and y-offset values in these lines: 
```
XfdesktopIconView::shadow-x-offset = 1
XfdesktopIconView::shadow-y-offset = 1

```and the shadow color a few lines farther down. I assume those offset values are in pixels.
I verified that the text color changes work in Greybird theme of Xubuntu 16.04.

---

