---
title: "New ubuntu interface, need some help"
date: 2009-09-01
forum: Desktop Environments
---

### Post by guillaume22 on 2009-09-01
Hello !

I'm trying to create a new Ubuntu theme (for Gnome), but I need help because it's the first time I'm using gtkrc file.

I use The Widget Factory to test my new theme.

**First problem**
I tried to use "gtk_color_scheme" to define default colors. But when I call the defined variable in the gtkrc file, it doesn't work. The default gnome color are used in stead of the defined colors.

For example, here is a gtkrc file :

```
gtk_color_scheme = "fg_color:#ff0000"

style "visualart-default" 
{

	bg[ACTIVE]		= @fg_color

}

class "GtkWidget" style "visualart-default"
```

So I always need to enter exact color (for example bg[ACTIVE] = "#ff0000") but it is not useful if future users want to customize the theme.

**Second problem**

When I want to change the color in an other style than "visualart-default" which is liked to "GtkWidget", it doesn't work.

For example, here is a gtkrc file :

```
style "visualart-default" 
{

	fg[ACTIVE] 		= "#000000"

}

style "visualart-button"
{

	fg[ACTIVE]		= "#ffffff"

}

class "GtkButton" 	style "visualart-button"
class "GtkWidget" 	style "visualart-default"
```

When I load the theme in The Widget Factory, the active position text of buttons is black (#000000) in stead of being white (#ffffff)

**Last problem**

I want the loading bar to be like the first attached file :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127033&stc=1&d=1251802503[/IMG]

But what I finally get is the second attached file :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127034&stc=1&d=1251802503[/IMG]

Here is my gtkrc for the loadingbar :

```
style "visualart-progressbar"
{
	
	xthickness = 0
	ythickness = 0
	GtkProgressBar::xspacing	= 10
	GtkProgressBar::yspacing	= 10
	
	engine "pixmap" 
	{
		
		image
		{
			function			= BOX
			detail				= "trough"
			file				= "images/progressbar/loading-bg-h.png"
			border				= { 5, 5, 5, 5 }
			stretch				= TRUE
			overlay_file                    = "images/progressbar/loading-fg.png"
			overlay_stretch                 = TRUE
			overlay_border			= { 10, 10, 10, 10 }
			orientation			= HORIZONTAL
		}
		
		image
		{
			function			= BOX
			detail				= "bar"
			file				= "images/progressbar/loading-h.png"
			border				= { 5, 5, 5, 5 }
			stretch				= TRUE
			overlay_file                    = "images/progressbar/loading-fg.png"
			overlay_stretch                 = TRUE
			overlay_border			= { 10, 10, 10, 10 }
			orientation			= HORIZONTAL
		}
		
		image
		{
			function			= BOX
			detail				= "trough"
			file				= "images/progressbar/loading-bg-h.png"
			border				=  { 5, 5, 5, 5 }
			stretch				= TRUE
			overlay_file                    = "images/progressbar/loading-fg.png"
			overlay_stretch                 = TRUE
			overlay_border			= { 10, 10, 10, 10 }
			orientation			= VERTICAL
		}
		
		image
		{
			function			= BOX
			detail				= "bar"
			file				= "images/progressbar/loading-h.png"
			border				= { 5, 5, 5, 5 }
			stretch				= TRUE
			orientation			= VERTICAL
		}
		
	}

}
```

Thanks for your help ...

---

### Post by guillaume22 on 2009-09-01
Please anybody... or maybe this thread must be post in the development forum.... :confused:

---

### Post by earthpigg on 2009-09-01
> **guillaume22 said:**
>  maybe this thread must be post in the development forum.... :confused:

it is almost certain to attract the attention of more folks that know about this stuff, yes.

best of luck! i like how your 2nd screenshot looks.

---

