---
title: "Gnome main menu Gtk styling"
date: 2009-03-12
forum: Desktop Environments
---

### Post by tr33m4n on 2009-03-12
Hello there!

I've been fiddling around with some of the options available in gtkrc when using the murrine engine. I set a task of only rounding the corners of panel applet buttons (eg, the Applications, Places and System buttons) whilst not rounding the corners of the menu items themselves. This is the code I ended up putting into gtkrc:

```
style "murrine-gnomemainmenu"
{

	engine "murrine" 
	{
		roundness = 7
	}
}
```

```
widget_class "*Panel*MenuBar*" style "murrine-gnomemainmenu"
```

This works very well... however I was wondering whether there is a way of only applying the roundness to: 

a) certain corners
b) certain buttons

For example the gnome main menu applet has "Applications", "Places" and "System"... Ideally i would love to only apply roundness to the top-left corner of "Applications", no roundness on "Places" and roundness on the top-right corner of "System". If you can imagine what I mean, you would get a nice smooth curve over all the icons, rather than on each one individually...

If anyone has any ideas, all are welcome!

Many thanks
Dan

---

### Post by tr33m4n on 2009-03-15
shameless bump

---

