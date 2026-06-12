---
title: "How to modify a theme without the Theme Configurator?"
date: 2014-12-14
forum: Desktop Environments
---

### Post by ineuw on 2014-12-14
I am using the Greybird theme and the Humanity-dark icon theme. This scheme allows me to set the desktop icon captions to white with a transparent background. A change with the Theme Configurator setting of "Highlight background" and "highlight text" (the first option) to black text also affects the desktop icon text and renders them unreadable. My question is which is the theme color settings file, so that I can modify the desktop icons from being affected by the Theme Configuraton?

---

### Post by Dennis N on 2014-12-14
I looked at this in the past, and don't think there is any independent setting for the desktop icon text color. In Xubuntu, it is set to the selected foreground color (selected_fg_color) in the theme configuration files - usually this is white. We can only set the font size. If you use the Theme Configurator, you just have to leave the Highlight Text (or Selection Text) color as it is, or use a color acceptable for the desktop as well. 

In Lubuntu on the other hand, the Desktop Settings dialog allows setting custom font size AND text color - a nice feature.

---

### Post by ineuw on 2014-12-14
Dennis N, thanks for the reply. You confirmed my suspicions and I am doing exactly as you recommended.

---

### Post by Dennis N on 2014-12-15
@ineuw,

This will be on interest should you come back to this thread. Contrary to what I had thought, I now find a couple of themes in the default set where the desktop icon text is NOT set to the highlighted text color (selected_fg_color). One is Albatross, the other is Raleigh. Albatross has a GTK-3.0 theme, so is preferable. The highlighted text color (selected_fg_color) in the theme configuration file for Albatross is near black (#333333), but the desktop icon's text color is white. In the attached image, I changed it to yellow with the Theme Configurator. Notice that the icon text color remains white.

---

### Post by vasa1 on 2014-12-15
My gtkrc has this:

```
style "xfdesktop-icon-view"
{
	font_name = "normal"
	XfdesktopIconView::label-alpha = 0
	XfdesktopIconView::selected-label-alpha = 0
	XfdesktopIconView::tooltip-size = 32
	fg[NORMAL] = @bg_color
	fg[ACTIVE] = @bg_color
	fg[SELECTED] = @link_color
        base[SELECTED] = "#f07745"

	engine "murrine"
	{
		textstyle = 5
		text_shade = 0.05
	}
}

```

---

### Post by ineuw on 2014-12-15
Thanks to you both. I will try both because I am curious and want to control my workspace.

---

### Post by Dennis N on 2014-12-16
> **vasa1 said:**
> My gtkrc has this:

```
style "xfdesktop-icon-view"
{
	font_name = "normal"
	XfdesktopIconView::label-alpha = 0
	XfdesktopIconView::selected-label-alpha = 0
	XfdesktopIconView::tooltip-size = 32
	fg[NORMAL] = @bg_color
	fg[ACTIVE] = @bg_color
	fg[SELECTED] = @link_color
        base[SELECTED] = "#f07745"

	engine "murrine"
	{
		textstyle = 5
		text_shade = 0.05
	}
}

```

**@vasa1**

Thanks very much. I had looked at this section of the theme config. and didn't get my changes to work. I tried it again and now it does! Obviously I was doing something wrong, but I don't know what.

**@ineuw**

Change fg[NORMAL] and fg[ACTIVE] to hex color codes you want. These set the icon text color independent of anything else. Such as:

fg[NORMAL] = "#E2EF70"
fg[SELECTED] = "#000000"

These are not affected by the Theme Configurator choices.

---

### Post by ineuw on 2014-12-16
I looked into gtkrc, and my question is which version of GTK is Xubuntu using for the color management? I also noticed that GTK-3 is based on .css. Very interesting and thanks again for introducing me to GTK.

---

