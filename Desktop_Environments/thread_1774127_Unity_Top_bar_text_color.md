---
title: "Unity: Top bar text color"
date: 2011-06-02
forum: Desktop Environments
---

### Post by arpad9 on 2011-06-02
In Unity, on a dark themed background (most of them), I can't see the top menu text.  If I change the "Input Boxes" Text color to white, then I can't see the text in input boxes.  (Why didn't they have the top bar conform to titlebar colors??  Lame.)

Any fixes?  (Other than making the foreground of Input boxes darker).

---

### Post by kerry_s on 2011-06-02
theres a gtkrc2.0 fix for that. i have it on 1 of my usb's, i'll try & find it for you. be back in a minute or so.

press-> alt+f2
type-> gedit .gtkrc-2.0
paste this:
```

style "panel-clock"
{
fg[NORMAL] = "#FFFFFF"
font_name = "Sans Bold 14"
}
widget "*.clock-applet-button.*" style "panel-clock"


```

save it to your home folder

log out & back in

ps: you can adjust the font type & size you want.

---

### Post by arpad9 on 2011-06-02
Thanks, but it had no effect.

---

### Post by kerry_s on 2011-06-02
> **arpad9 said:**
> Thanks, but it had no effect.

try changing "*.clock-applet-button.*" to "*-applet-*"

i forgot in unity it's only using indicator applets. you just have to find the name of the widget.

i switched to lubuntu, so i can't test what would work.

---

### Post by arpad9 on 2011-06-02
Nope. Still the same.

---

### Post by kerry_s on 2011-06-03
> **arpad9 said:**
> Nope. Still the same.

time to go to the terminal. :)

in the terminal type-> xprop
the mouse will turn into a cross, click on the text to get the info of it. paste here so i can look at.

no guarantees been awhile for me, i can barely remember commands these days. :lolflag:

---

### Post by arpad9 on 2011-06-03
There's a new command for me.  xprop.  Cool.  Here it is (thanks).

```

arpad@sasangasana:~$ xprop
_NET_WM_ICON_GEOMETRY(CARDINAL) = 9, 1057, 48, 48
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
		window state: Normal
		icon window: 0x0
_NET_WM_DESKTOP(CARDINAL) = 0
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
_NET_WM_STRUT_PARTIAL(CARDINAL) = 0, 0, 24, 0, 0, 0, 0, 0, 0, 1919, 0, 0
XdndAware(ATOM) = BITMAP
WM_NAME(STRING) = "panel"
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_DOCK
_NET_WM_STATE(ATOM) = _NET_WM_STATE_STICKY, _NET_WM_STATE_SKIP_TASKBAR, _NET_WM_STATE_SKIP_PAGER

```

---

### Post by kerry_s on 2011-06-03
looks like its just reading as "panel", so try this:

```

style "panel"
{
fg[NORMAL] = "#FFFFFF"
font_name = "Sans Bold 14"
}
widget "*panel*" style "panel"

```

---

### Post by kxxe on 2011-06-24
go to /home/you/.themes/yourtheme/gtk-2.0 .. gedit file "panel.rc" or "panel" (if you dont see it might be in folder "panel" or "style" ..) .. so if u open panel.rc find there 

> style "panel" {

and add 

> text[NORMAL] = "#ffffff" 

then just save file and reset theme ... thats all

---

### Post by boddhisatva on 2011-06-28
@kxxe
Doesn't work. Nothing changes.
It's "theme-panel" not "panel" in my panel.rc file.
I've changed fg[INSENSITIVE], text[NORMAL], and text[INSENSITIVE] to pure white, with no effect on main panel text or indicator text.

```

style "theme-panel"
{
#	bg_pixmap[NORMAL] = "paneltrans.png"
#	bg[SELECTED]	= "#666666" # Makes selected items dark.
	bg[NORMAL] 	= shade (0.37, @bg_color) # Makes panel background dark.
	bg[PRELIGHT]	= mix (0.50, shade (0.50,@bg_color), shade (0.90,@selected_bg_color)) # Makes panel button prelight dark.
	bg[ACTIVE]	= shade (0.22, @bg_color) # Makes active buttons dark.
	bg[INSENSITIVE]	= shade (0.52, @bg_color)
	fg[NORMAL]	= @selected_fg_color # Makes panel text light.
	fg[PRELIGHT]	= @selected_fg_color  # Makes prelighted text colored.
	fg[SELECTED]	= @selected_fg_color  # Makes prelighted text colored.
	fg[ACTIVE]	= @selected_fg_color  # Makes active text colored.
	fg[INSENSITIVE]	= "#ffffff" # Color for insensitive text.
	text[NORMAL]	= "#ffffff"
	text[PRELIGHT]	= @selected_fg_color  # Makes prelighted text colored.
	text[SELECTED]	= @selected_fg_color  # Makes prelighted text colored.
	text[ACTIVE]	= @selected_fg_color  # Makes active text colored.
	text[INSENSITIVE]	= "#ffffff"
}

```

---

### Post by s-p-n on 2011-07-07
In general if you're reading this because you're using Unity and a theme does this to your panel,

Open a terminal, type:
```

gksudo nautilus ~/.themes

```If you don't see the theme you're using, try:
```

gksudo nautilus /usr/share/themes

```Find the theme you're using, open the folder, open the file gtkrc with gEdit (Text Editor)

Search for ```
panel
``` Look for something like: (note by 'etc', I mean, it could be anything.)
```

style "panel"
style "murrine-panel"
style "etc-panel"
style "panel-etc"

```In any case, add the following line to the style:
```

text[NORMAL]

```For example, for the theme UbuntuStudio saved for all users, type in a terminal:
```

gksudo gedit /usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc

```Find:
```

style "murrine-panel"

```under (or above) the line "bg_pixmap[NORMAL] = "panel/panel.png",
add:
```

text[NORMAL] = "#FFFFFF"

```For those of you who don't already know, "#FFFFFF" is white. More specifically, hexadecimal for 255 red, 255 green, and 255 blue.

I prefer a color more like "#009BF9" for my theme. (that's the select-color for UbuntuStudio theme).
You can pick your favorite color on this web-site, [http://www.colorpicker.com](http://www.colorpicker.com)


Hopefully in Ubuntu 11.10, there will be a way to edit this text with a GUI for all themes, the same way. (Like in Gnome2.x how you can right-click the panel to edit the text... Not sure why we can't just do that in Unity..

---

### Post by danep on 2011-07-20
@s-p-n Thanks for the fix! It helped me 'solve', or at least work around, the issue described in [http://ubuntuforums.org/showthread.php?p=11043876](http://ubuntuforums.org/showthread.php?p=11043876)

---

### Post by MyD0j0 on 2011-09-23
Woo Hoo!! solved my issue too!  And I borrowed s-p-n s uggestion to use the select color instead of just white--looks tasty once again!

Woo Hoo!!

Woo Hoo!!

---

### Post by engineer on 2012-01-31
The fix by setting text[NORMAL] seems to only apply to gtk-2 themes. Is there a similar workaround for gtk-3 themes with .css files?

---

