---
title: "[SOLVED] removing arrow from menu"
date: 2008-12-13
forum: General Help
---

### Post by Izek on 2008-12-13
I have it so that the ubuntu menus are all self-contained under one menu, but that arrow pointing down is a little annoying. Is there any way to remove it?

---

### Post by Ivo Moelans on 2008-12-13
I think I gave the answer here: [http://ubuntuforums.org/showthread.php?t=991923]("http://ubuntuforums.org/showthread.php?t=991923")
Of course change *Human 2* for whatever theme you are using. If the theme has no separate *panel.rc* or *panelrc* you can append the code in the *gtkrc* file.
For the *arrows* subdirectory: if it doesn't exist, create it.

If you should have more questions or if this isn't to clear for you it would be helpful if you provide the name of the theme you are using (and the link where you downloaded it).

Succes.

---

### Post by Izek on 2008-12-13
There's nothing in my /home/name/.themes folder. I'm using one of the themes that comes with ubuntu by default. But it's customized,

Clearlooks Theme
Mist Iconset

---

### Post by Ivo Moelans on 2008-12-13
I've thought of a simpler solution.

First look if you have a hidden file in your home directory named *.gtkrc-2.0*. If so, open it with Text Editor (gedit) and append the code. Save the file. If not *create* a new file with Text Editor, insert the code and save it as *.gtkrc-2.0* in your home directory.
The arrow picture is not needed.

Change to another theme (and back).

This file supersedes the gtkrc files of the themes, so it should work for all of them.

Let me know how it goes.

---

### Post by Izek on 2008-12-13
Thanks man, it worked.

---

### Post by Ivo Moelans on 2008-12-13
Glad it worked.

***For the purists.***

The code was for a specific theme and it makes reference to a path needed in that theme but not necessarily present in other themes. And yet it works without the arrow picture being needed. However, that is probably due to the forgiving nature of GTK. The error of the missing picture is probably noted at some level, but the theme is executed nevertheless and a 'blank' image is rendered in the place of the missing picture. Which is, ironically, what we wanted to begin with.

However, if you want this to work cleanly, you could do the following.

1) rename *arrow-blank.png* to ***.**arrow-blank.png* an place it in your home directory

2) change the code so that it reads:

```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
	{
	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= ".arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= UP
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= ".arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= DOWN
	}
	}
}

widget_class "*PanelToplevel*" 			style "panel-arrow-remove"


```

---

### Post by buggix on 2009-01-17
It worked by me, too. Thanks very much. 

Best regards from germany!

---

### Post by mayacreator on 2009-01-18
Ivo, thank you so much! those little black arrow just was making me crazy :)

---

### Post by tagbre on 2009-12-24
Yes, it works, but it creates another problem: the icon that separates the tray area from the rest of the panel is changed. I don't want it to change. How could I get that result?

---

### Post by MastroPino on 2010-04-28
Awesome, it works!!! Thanks mate!:KS

---

### Post by dwiguna on 2010-05-09
wow....thankssssssssssssss:guitar:

---

### Post by freshnrg on 2010-05-20
> **tagbre said:**
> Yes, it works, but it creates another problem: the icon that separates the tray area from the rest of the panel is changed. I don't want it to change. How could I get that result?

same problem here. I've tried to modify the gtkrc file but nothing helped. any ideas?

---

### Post by Fisaulerod on 2010-06-30
> **freshnrg said:**
> same problem here. I've tried to modify the gtkrc file but nothing helped. any ideas?

Same problem :/.

---

### Post by koffeejv on 2010-08-08
> **freshnrg said:**
> same problem here. I've tried to modify the gtkrc file but nothing helped. any ideas?

After modify the gtkrc-2.0 change to another theme (and back).

---

### Post by XiaolinDraconis on 2010-12-27
i am pretty sure this Gelide error is related to this change. i dont know what to do about it.

* Process error output:
	/home/dojo/.gtkrc-2.0:12: Unable to locate image file in pixmap_path: "arrows/arrow-blank.png"
	/home/dojo/.gtkrc-2.0:16: Overlay image options specified without filename
	/home/dojo/.gtkrc-2.0:22: Unable to locate image file in pixmap_path: "arrows/arrow-blank.png"
	/home/dojo/.gtkrc-2.0:26: Overlay image options specified without filename
	
	(snes9x-gtk:10816): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field
	
	Segmentation fault



BUMP

---

### Post by XiaolinDraconis on 2010-12-29
bump

---

