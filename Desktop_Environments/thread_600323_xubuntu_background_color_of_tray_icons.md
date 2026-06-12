---
title: "xubuntu background color of tray icons"
date: 2007-11-02
forum: Desktop Environments
---

### Post by micro_cz on 2007-11-02
hi, i have a problem with xfce panel color, even if i set black bg pixmap and bg[NORMAL] to “#000000&#8243; for it, the backround of tray icons on it remains the same color as is bg[NORMAL] of default style of current theme  .. is there any chance to fix it?

screen: [http://sweb.cz/M.Rost/2007-11-02-103240_1280x800_scrot.png]("http://sweb.cz/M.Rost/2007-11-02-103240_1280x800_scrot.png")

---

### Post by Thyme on 2007-11-02
Hi micro_cz,

Are you doing it like this?

```

style "panelbuttons"
{
         bg[NORMAL] = "#000000"
}

```

Did you manage to sought it out?

---

### Post by micro_cz on 2007-11-02
yes exactly, but with no effect

---

### Post by Thyme on 2007-11-02
hmm .. Do you also have that in style "panel" ?

---

### Post by Thyme on 2007-11-02
The theme that I'm using as the following panel configuration:

```

style "panel"{
    bg[NORMAL]   = "#202020"
    fg[NORMAL]   = "#fdfdfd"
    text[NORMAL] = "#fdfdfd"
}

style "panelbuttons"{
    bg[NORMAL] 		= "#202020"
    bg[ACTIVE]		= "#1576CF"
    bg[SELECTED]	= "#1576CF"
    bg[PRELIGHT]	= "#666666"
    
    fg[NORMAL]		= "#fdfdfd"
    fg[ACTIVE]		= "#ffffff"
    fg[PRELIGHT]	= "#ffffff"
}
class "*Panel*" style "panel"
widget_class "*Panel*GtkToggleButton" style "panelbuttons"
widget_class "*Panel*Button" style "panelbuttons"
widget_class "*Panel*b*" style "panelbuttons"

```

Don't know if it will help but I thought I'll post it anyway :)

---

### Post by micro_cz on 2007-11-02
this is style, which i am using for panel: 

```

style "panel-black"
{
  xthickness           	= 2
  ythickness           	= 0

  fg[NORMAL]		= "#161616"
  fg[PRELIGHT]		= "#FFFFFF"
  fg[ACTIVE]		= "#FFFFFF"
  fg[SELECTED]		= "#FFFFFF"
  fg[INSENSITIVE]	= "#8A857C"

  bg[NORMAL]		= "#000000"
  bg[PRELIGHT]		= "#000000"
  bg[ACTIVE]		= "#000000"
  bg[SELECTED]		= "#000000"
  bg[INSENSITIVE]	= "#000000"

  base[NORMAL]          = "#000000"
  base[PRELIGHT]	= "#000000"
  base[ACTIVE]		= "#000000"
  base[SELECTED]	= "#000000"
  base[INSENSITIVE]	= "#000000"

  text[NORMAL]		= "#161616"
  text[PRELIGHT]	= "#FFFFFF"
  text[ACTIVE]		= "#000000"
  text[SELECTED]	= "#FFFFFF"
  text[INSENSITIVE]	= "#8A857C"

#bg_pixmap[NORMAL]		= "ickle/icklekicker/kickerslate.png"
#bg_pixmap[SELECTED]		= "Panel/panel-bg.png"
#bg_pixmap[INSENSITIVE]		= "Panel/panel-bg.png"
#bg_pixmap[PRELIGHT]		= "Panel/panel-bg.png"
  bg_pixmap[NORMAL]		= "Panel/panel-bg-black-24.png"
  bg_pixmap[INSENSITIVE]	= "<parent>"

  bg_pixmap[PRELIGHT]		= "<parent>"

  bg_pixmap[SELECTED]		= "<parent>"

  bg_pixmap[ACTIVE]		= "<parent>"

}

```

and for panel buttons:
```

style "panelbuttons-black" = "default"
{

  fg[NORMAL]		= "#707070" # very dark brown
  fg[PRELIGHT]		= "#000000" # text on buttons (hover)
  fg[ACTIVE]		= "#FFFFFF" # text on unfocused tabs
  fg[SELECTED]		= "#000000" # selected text on lists
  fg[INSENSITIVE]	= "#000000" # greyed "unused" text

  bg[NORMAL]		= "#000000"

  xthickness	= 2
  ythickness	= 1

  GtkWidget::focus_padding = 2

	engine "pixmap" {

		image
		{
			function	= BOX
			recolorable	= TRUE
			state		= NORMAL
			file		= "Panel/panelbutton_black_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function	= BOX
			recolorable	= TRUE
			state		= PRELIGHT
			file		= "Panel/panelbutton_black_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function	= BOX
			recolorable	= TRUE
			shadow		= OUT
			state		= PRELIGHT
			file		= "Panel/panelbutton_black_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
			#overlay_file	= "panelbutton2.png"
			#overlay_border	= { 4, 4, 4, 4 }
			#overlay_stretch	= TRUE
		}

		image
		{
			function	= BOX
			recolorable	= TRUE
			shadow		= IN
			state		= PRELIGHT
			file		= "Panel/panelbutton_black_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
			#overlay_file	= "panelbutton2.png"
			#overlay_border	= { 4, 4, 4, 4 }
			#overlay_stretch	= TRUE
		}

		image
		{
			function	= BOX
			recolorable	= TRUE
			state		= ACTIVE
			file		= "Panel/panelbutton_black_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function	= BOX
			recolorable	= TRUE
			state		= INSENSITIVE
			file		= "Panel/panelbutton_black_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}  

	}

}

```

---

### Post by micro_cz on 2007-11-02
thanks, i'll try

---

### Post by micro_cz on 2007-11-02
again, any change...maybe those buttons with "bad" background aren't  properly panel buttons

---

### Post by crimesaucer on 2007-11-09
> **micro_cz said:**
> hi, i have a problem with xfce panel color, even if i set black bg pixmap and bg[NORMAL] to “#000000&#8243; for it, the backround of tray icons on it remains the same color as is bg[NORMAL] of default style of current theme  .. is there any chance to fix it?

screen: [http://sweb.cz/M.Rost/2007-11-02-103240_1280x800_scrot.png]("http://sweb.cz/M.Rost/2007-11-02-103240_1280x800_scrot.png")

I had the same problem and I solved it the lazy way... I used Orage clock/calendar instead and it doesn't do that with the background not matching.

I also stopped using the icon box which I also had a problem with.


If you look at this old post of mine from last January, you can see I had the same problem: [http://ubuntuforums.org/showthread.php?t=339984&highlight=panel+gtkrc](http://ubuntuforums.org/showthread.php?t=339984&highlight=panel+gtkrc)


... but if you look further down, you will see that the Orage clock doesn't draw the background wrong like the regular clock plug-in (Orage clock is a better xfce4 plug-in in my opinion). 


As for the system tray icons I'm not sure... I never use it anyway so I removed it.

---

### Post by micro_cz on 2007-11-10
thank you very much for reply ....thats the solution, that i was afraid is only possible, orageclock is little bit more processor consuming and on the system tray i have nm-applet, which is quite usefull for me ..but better than ugly gray patches on the panel ....btw: maybe somewhere could be alternative notif area for xfce ...i will take a look ... thanks, micro

---

### Post by micro_cz on 2007-11-23
HOOOORAY ... SOLVED ...the xfce and gnome panel has probably same name, but one starts with capital letter and another is in lower case 

ading, this to gtkrc, where panel-black is style for a panel will help:
```

widget "*Panel*"          style "panel-black"
class  "*Panel*"           style "panel-black"
widget_class "*Panel*" style "panel-black"
widget "*panel*"          style "panel-black"
class  "*panel*"           style "panel-black"
widget_class "*panel*" style "panel-black"

```

and my desktop now finally looks eyecandy :o))

---

