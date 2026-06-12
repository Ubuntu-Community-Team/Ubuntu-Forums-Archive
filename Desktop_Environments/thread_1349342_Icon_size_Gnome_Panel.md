---
title: "Icon size Gnome Panel"
date: 2009-12-08
forum: Desktop Environments
---

### Post by Sastra on 2009-12-08
Hello,

I have a question. Someone asked me if it is possible to make the icons from the Gnome panel bigger, because he has trouble with the default size of the icons. The people who use the PC have problems with their eyes and controlling the mouse, and the small icons doesn't make it easier.

I tried the following things I found on Google and on the forum:
1. Changing the size of the panel to 120px, but this only changes the height of the panel and not the size of the icons I added. 
2. Gnome Color Chooser. This changed the size of the icons system wide, except the Gnome panel.

So is there any other way I can force the icons on the Gnome panel to be like 120x120px? I also looked at options like Cairo Dock or something, but the problem with that software is that it adds all kind of graphical effects and I want the panel to be clean and simple.

---

### Post by fabounet on 2009-12-08
> it adds all kind of graphical effects and I want the panel to be clean and simple.
just untick the unnecessary effects ...

---

### Post by Sastra on 2009-12-08
> **fabounet said:**
> just untick the unnecessary effects ...

Ok, that`s one option. But isn`t it possible to make the icons bigger with the default Gnome panel?

---

### Post by etnlIcarus on 2009-12-08
Add this to your $HOME/.gtkrc-2.0 file:
```
style "panel"
{
	xthickness = 0
	ythickness = 0
}

widget "*PanelWidget*" 					style "panel"
widget "*PanelApplet*" 					style "panel"
widget "*fast-user-switch*"				style "panel"
class "PanelApp*" 					style "panel"
class "PanelToplevel*" 					style "panel"
#widget_class "*Mail*" 					style "panel"
widget_class "*notif*" 					style "panel"
widget_class "*Notif*" 					style "panel"

widget "*Xfce*Panel*" style "panel"
class "*Xfce*Panel*" style "panel"
```

You can change the x/y thickness to whatever you want, to alter the internal padding. Just don't expect all plugins to behave properly until you restart gnome-panel, though.

---

### Post by Sastra on 2009-12-08
> **etnlIcarus said:**
> Add this to your $HOME/.gtkrc-2.0 file:
```
style "panel"
{
	xthickness = 0
	ythickness = 0
}

widget "*PanelWidget*" 					style "panel"
widget "*PanelApplet*" 					style "panel"
widget "*fast-user-switch*"				style "panel"
class "PanelApp*" 					style "panel"
class "PanelToplevel*" 					style "panel"
#widget_class "*Mail*" 					style "panel"
widget_class "*notif*" 					style "panel"
widget_class "*Notif*" 					style "panel"

widget "*Xfce*Panel*" style "panel"
class "*Xfce*Panel*" style "panel"
```

You can change the x/y thickness to whatever you want, to alter the internal padding. Just don't expect all plugins to behave properly until you restart gnome-panel, though.

I tried changing x and y both to 48, but all I get is a big toolbar and no bigger icons :(

---

### Post by etnlIcarus on 2009-12-08
x/y changes the *widget padding*, not the icon size. Setting the padding to zero will mean the icons will take up as much space as they possibly can. Setting the padding higher will have the opposite effect.

---

