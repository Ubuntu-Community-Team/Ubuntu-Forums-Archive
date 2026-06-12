---
title: "How to add a border to the menus (edit gtkrc)"
date: 2015-01-01
forum: Desktop Environments
---

### Post by fkervin on 2015-01-01
Hi all,

I've found a theme that I like a lot, but have something bad in my opinion, it is, application menus have no border at all and it makes those menus to be much less visible than they should. It happens with menus in all applications, I attach an screenshot in firefox so you can see what i mean:

[IMG]http://i60.tinypic.com/2mzk2dv.png[/IMG]

It's difficult to see where menu ends and window (google in this case) starts, so I would like to add a border to this menu.

I know it must be done in the "gtkrc" file from the gtk-2.0 file in the theme, but I don't know where exacty, I've spent a lot of time trying but I don't find where.

Anyone can help me?

Regards and thanks in advance

---

### Post by vasa1 on 2015-01-01
I don't know about adding a border but you can change the color of the menu to whatever you like. BTW, why do you use that tinypic site? It has the most obnoxious distracting animations. You could use the attachment facility the forum offers instead :)

---

### Post by vasa1 on 2015-01-01
Here I edited my gtkrc to get what is shown in the attachment.

```
style "menu"
{
	ythickness        = 3
	xthickness        = 0
	GtkMenuBar	:: shadow-type		= GTK_SHADOW_NONE
	
	bg[SELECTED]      = @selected_bg_color
#	bg[NORMAL]        = shade (1.18, @bg_color)
	bg[NORMAL]        = shade (0.5, @maroon)
	bg[PRELIGHT]      = @selected_bg_color
	bg[ACTIVE]        = shade (1.18, @bg_color)
	bg[INSENSITIVE]   = shade (1.18, @bg_color)
	fg[NORMAL]        = @fg_color # Color for normal text.
	fg[PRELIGHT]      = @base_color
	fg[SELECTED]      = @base_color
	fg[ACTIVE]        = @base_color
	fg[INSENSITIVE]   = mix (0.4, @fg_color, @bg_color) # Text color for non-interactive menu items
	text[NORMAL]      = @text_color # Color for menu-item radio/checks.
	base[NORMAL]      = @bg_color # Color for menu-item radio/checks background.
	text[PRELIGHT]    = @base_color
	text[SELECTED]    = @base_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = @text_color
	
	engine "murrine" 
	{
		roundness = 0 # Roundness of menu items.
		gradient_shades = {1.0,1.1,1.1,1.0}
		contrast = 0.5 #0.9
#		lightborder_shade = 1.5
	}

```

---

### Post by fkervin on 2015-01-01
Hi vasa1 :)

I didn't know that feature of including images directly, i'm trying now.

I know that it's possible to make what I want since other themes draws the menus in this way:

[ATTACH=CONFIG]258927[/ATTACH]

I need to identify this part of the code and copy to the theme I want.

I'm gonna research and make more tests, if meanwhile someone gives a closer try, I'll thank :)

Regards

---

### Post by fkervin on 2015-01-01
I've replace **style "menu" **and  **style "menubar" = "menu" **, copying the ones of the theme where I have the line into the theme I want to use but doesn't work.

It quite weird since those functions defines the behaviour of this menu according to the tests I've made. Perhaps the problem is some variable used here that changes from one theme to other....

I'm testing...

regards

---

