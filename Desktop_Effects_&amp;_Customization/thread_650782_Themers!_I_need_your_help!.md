---
title: "Themers! I need your help!"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-12-26
Firstly, thanks in advance for any help I get here. 


Although I'd class myself a fairly good graphic artists I've only JUST started to approach the world of GTK theming. I'm currently modifying the "Burnt Orange Ice" theme. So far, so good... but there's a couple of things I'm not sure. I'll ask one question at a time for ease. 

Screenshot one:

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/dropdown_menu_question.png[/IMG]


You see this menu dropdown? I know it's possible to make an actual graphic for this. I have a graphic waiting for it, a sort of slightly glassy look. How do code this into the gtkrc file?

Thanks again. 

/izo\

---

### Post by Kimmik on 2007-12-26
```
style "menu" = "default"
{
	engine "pixmap"
	{
		# Menu background
		image
		{
		    function 		= BOX
		    recolorable 	= TRUE
		    detail 			= "menu"
		    file 			= "menu.png"   
		    border 			= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
	}
}
class "GtkMenu" style "menu"
```

---

### Post by Izobalax on 2007-12-26
Kimmik... you are an ANGEL. That worked, thank you SO much!


Another question. Screenshot time!

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/menubar_question.png[/IMG]

As you can see, I have quite a dark menubar, using a pixmap. The text is black and therefore largely unreadable but I can't locate in the gtkrc file where I can change the text colour JUST for the menubar. 

Many thanks in advance, again. 

P.S. Kimmik, I have your site bookmarked. EXCELLENT work!

/izo\

---

### Post by Kimmik on 2007-12-27
> **Izobalax said:**
> 
As you can see, I have quite a dark menubar, using a pixmap. The text is black and therefore largely unreadable but I can't locate in the gtkrc file where I can change the text colour JUST for the menubar. 


What engine are you primarily using?

Have you used the normal method to skin the menubar?

You could try this:
```

style "menubar-color"		
{
  fg[NORMAL] = "#fff"
  text[NORMAL] = "#fff"
  fg[PRELIGHT] = "#fff"
  fg[ACTIVE] = "#fff"
}
widget_class "*MenuBar.*" 			style "menubar-color"

```

Here's the full code I used for my Schwermetall-Dark-Ice theme (uses a dark menubar with white text):


```

style "menubar"		
{

  fg[NORMAL] = "#fff"
  text[NORMAL] = "#fff"
  fg[PRELIGHT] = "#fff"
  fg[ACTIVE] = "#fff"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function			= BOX
			recolorable		= TRUE
			state = PRELIGHT
			file				= "menubar-item.png"
			border			= { 10, 10, 10, 10 }
			stretch			= TRUE
		}

 	}
}


class "GtkMenuBar*"				style "menubar"
widget_class "*MenuBar.*" 			style "menubar"


```

---

### Post by Izobalax on 2007-12-27
> **Kimmik said:**
> What engine are you primarily using?

Pixmap.


> **Kimmik said:**
> Have you used the normal method to skin the menubar?

You could try this:
```

style "menubar-color"		
{
  fg[NORMAL] = "#fff"
  text[NORMAL] = "#fff"
  fg[PRELIGHT] = "#fff"
  fg[ACTIVE] = "#fff"
}
widget_class "*MenuBar.*" 			style "menubar-color"

```

Here's the full code I used for my Schwermetall-Dark-Ice theme (uses a dark menubar with white text):


```

style "menubar"		
{

  fg[NORMAL] = "#fff"
  text[NORMAL] = "#fff"
  fg[PRELIGHT] = "#fff"
  fg[ACTIVE] = "#fff"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "menubar.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function			= BOX
			recolorable		= TRUE
			state = PRELIGHT
			file				= "menubar-item.png"
			border			= { 10, 10, 10, 10 }
			stretch			= TRUE
		}

 	}
}


class "GtkMenuBar*"				style "menubar"
widget_class "*MenuBar.*" 			style "menubar"


```


That's awesome! I'll give that a whirl! Thanks again!

/izo\

---

### Post by Izobalax on 2008-03-13
OK, I have another GTK skinning question.

Here's my current theme:

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/aurora_blackwhite.png[/IMG]

I'm using the Aurora engine with the default theme modified. How do I change the buttons to a darker colour, like #484848, with the button text being white and how do I change the scrollbar colour to the same?

/izo\

---

### Post by Izobalax on 2008-03-20
BUMP!

/izo\

---

### Post by Izobalax on 2008-03-24
BUMPAROO!

/izo\

---

### Post by rainwalker on 2008-03-25
I don't know about changing the colors, but PLEASE, share that theme you're using right now! I love Aurora themes, and that black-and-white one looks amazing!

---

### Post by Izobalax on 2008-03-25
> **rainwalker said:**
> I don't know about changing the colors, but PLEASE, share that theme you're using right now! I love Aurora themes, and that black-and-white one looks amazing!



All I did was use the default aurora theme and change the colours. You do this when you click 'customize' in the Appearance program. Unfortunately, I didn't save the colours but I'm sure you could easily do this yourself. 

/izo\

---

### Post by rainwalker on 2008-03-25
Ah, thank you!

---

