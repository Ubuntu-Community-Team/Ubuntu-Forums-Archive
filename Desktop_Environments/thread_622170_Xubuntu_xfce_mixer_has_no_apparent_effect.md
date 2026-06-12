---
title: "Xubuntu xfce mixer has no apparent effect"
date: 2007-11-24
forum: Desktop Environments
---

### Post by tenbbs on 2007-11-24
Installed Xubuntu 7.10 today on my HP laptop / AMD64-3700+ 

Like Xubuntu so far. First issue:

Audio plays through the internal speakers even when the headphones are plugged in.
Searched on it a little bit and came to the following attempt:
Opened Apps>Settings>Mixer Settings. 
Under device "Default" deselected "Headphone Jack Sense, 0" and "Line Jack Sense, 0"
Did the same de-selections under device "#0: NVidia nForce3"

Unfortunately no change in audio behavior. Restarted and still no change in behavior.
Searched on the problem more and haven't seen any good suggestions.

Little help over here?

-HelicopterJay

---

### Post by bunadm on 2008-01-17
having the same issue... Sound come out of the laptop speakers on XFCE, but works fine under the gnome desktop...

The initial install was gnome, and then I added XFCE.

I like it other than this issue....it seems much fast...

hope someone knows how to fix this though...

---

### Post by hangar_18 on 2008-02-26
old topic, but i just found out:
"..I&#8217;ve solved my volume control problems **by dragging the Volume Control plugin from the item list to the panel**. Simple, but it works..."
[http://xubuntu.wordpress.com/tag/mixer/]("http://xubuntu.wordpress.com/tag/mixer/")

it worked for me, hope it will help others, btw it (was :) ) very anoying bug :mad:

---

### Post by hangar_18 on 2008-02-26
> old topic, but i just found out:
"..I&#8217;ve solved my volume control problems by dragging the Volume Control plugin from the item list to the panel. Simple, but it works..."
[http://xubuntu.wordpress.com/tag/mixer/](http://xubuntu.wordpress.com/tag/mixer/)

it worked for me, hope it will help others, btw it (was  ) very anoying bug 

f*ck, this didnt work after restarting xfce..
after about 2 hours of reading bug reports i found out that it is theme issue,
i use Xfce-dark theme, i have succesfully fixed it now!
just edit your theme..volume control is working only with engine murrine
most of the themes are using xfce engine
editing file /usr/share/themes/your_theme/gtk-2.0/gtkrc,
replacing engine part

with engine part grabbed from MurrinaStormCloud
>   engine "murrine" 
  {
	listviewstyle = 0 # 0 = nothing, 1 = dotted
	menuitemstyle = 1 # 0 = flat, 1 = glassy, 2 = striped
	glazestyle = 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style, 3 = top curved hilight, 4 = beryl style
	scrollbar_color = "#d4d4d4"
    	contrast = 1.5
	menubarstyle = 1 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	menubaritemstyle = 1 # 0 = menuitem look, 1 = button look
	listviewheaderstyle = 1 # 0 = flat, 1 = glassy, 2 = raised
	roundness = 2 # 0 = squared, 1 = old default, more will increase roundness
    	animation = TRUE # FALSE = disabled, TRUE = enabled
	scrollbarstyle = 0 # Enable or disable circles, stripes, handles
  }
fixed the problem, volume control is still there after restarting xfce!
it changed some colors,but thats no problem to fix,question of 5 minutes :)
hope this will help

---

### Post by hangar_18 on 2008-02-26
omg, SORRY, wrong topic...am i blind or wtf?:lolflag:

---

