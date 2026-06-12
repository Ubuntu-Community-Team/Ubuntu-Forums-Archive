---
title: "indicator-applet-session Font color"
date: 2009-11-02
forum: Desktop Environments
---

### Post by LinuxFanBoi on 2009-11-02
I would like to change the font colour displayed by indicator-applet-session within gnome pannel.  It seems to have it's own configuration making the font colour settings for gnome panel not apply to it.

Does anyone know where the file, if there is one that controls this program's display settings?  I would like the font to match the rest of the panel.

---

### Post by LinuxFanBoi on 2009-11-02
Perhaps those crickets are because people don't know what I'm referring to.
[IMG]http://img266.imageshack.us/img266/3774/screenshottj.png[/IMG]
This.

I can make all the text on gnome-panel any color I choose but this little bad boy likes to be special for some reason.

---

### Post by LinuxFanBoi on 2009-11-03
anyone?

---

### Post by LinuxFanBoi on 2009-11-03
crickets, I know it can be done,  I see screen shots with colors other than black fonts everywhere.

---

### Post by LinuxFanBoi on 2009-11-04
Still chirping,

Here is my .gtkrc-2.0 if it helps.

```
style "panel"
{
  fg[NORMAL]             	  = "#ffffff"	#panel txt normal
  fg[PRELIGHT]          	  = "#ffffff"
  fg[ACTIVE]            	  = "#ffffff"
  fg[SELECTED]          	  = "#ffffff"
  fg[INSENSITIVE]            	  = "#ffffff"
  bg[NORMAL]              	  = "#012CAD" 	#Background of switcher and wl fine outline
  bg[PRELIGHT]            	  = "#000000"	#Mouseover wl
  bg[ACTIVE]               	  = "#000000"	#Selected wl
  bg[SELECTED]             	  = "#000000"	#Mouseover outline
  bg[INSENSITIVE]            	  = "#ffffff"	#??
  base[NORMAL]           	  = "#617BC5"	#Background of things like deskbar or 'add to panel'
  base[PRELIGHT]          	  = "#ffffff"	#fine outline on windowlist items
  base[ACTIVE]            	  = "#ffffff"
  base[SELECTED]           	  = "#ffffff"
  base[INSENSITIVE]        	  = "#ffffff"
  text[NORMAL]           	  = "#ffffff"
  text[PRELIGHT]         	  = "#ffffff"
  text[ACTIVE]               	  = "#ffffff"
  text[SELECTED]                  = "#ffffff"
  text[INSENSITIVE]               = "#ffffff"
}
widget 		"*PanelWidget*" 		style "panel"
widget 		"*PanelApplet*" 		style "panel"
class 		"*Panel*" 			style "panel"
widget_class 	"*Mail*" 			style "panel"
class 		"*notif*" 			style "panel"
widget 		"indicator-applet-session" 	style "panel" 
```

---

### Post by LinuxFanBoi on 2009-11-05
Wow, no love for this thread?  Even the devs at Canonical must be stumped because they don't answer either.

---

### Post by hofi on 2009-11-07
I have this problem, too. Looks kind of ugly:

[IMG]http://dl.dropbox.com/u/1008673/Screenshot.png[/IMG]

Can anyone help?

Edit: It would be acceptable to just not show the name at all, if the color can't be changed.

---

### Post by VCoolio on 2009-11-07
Use this:

widget "*fast-user-switch-applet*" style "panel"

The indicator-applet is the one notifying for new mail etc. This is the fast-user-switch-applet and I agree they should listen to gtkrc better.

---

### Post by hofi on 2009-11-07
Thank you very much, VCoolio! You're the best! :D

---

