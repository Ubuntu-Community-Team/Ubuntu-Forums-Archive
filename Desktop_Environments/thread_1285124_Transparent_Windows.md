---
title: "Transparent Windows?"
date: 2009-10-07
forum: Desktop Environments
---

### Post by pop_n_fresh on 2009-10-07
I have my panels set quite transparent and I love the way this looks but when I have any windows open the borders are all solid colour. Is there any way that I can set them to be transparent also?

Thank you all

---

### Post by Subban on 2009-10-07
I'm not sure I understand, you aren't refering to the borders o nthe windows you open are you, such as Nautilus or Firefox?

Or do you mean something to do with the panels themselves, perhaps the buttons representing the current opened windows. If you mean these then to my knowledge its not adjustable on Gnome panels, you could replace the panel with something like Tint2, that does allow them to be transparent.

---

### Post by pop_n_fresh on 2009-10-07
> **Subban said:**
> I'm not sure I understand, you aren't refering to the borders o nthe windows you open are you, such as Nautilus or Firefox?

Or do you mean something to do with the panels themselves, perhaps the buttons representing the current opened windows. If you mean these then to my knowledge its not adjustable on Gnome panels, you could replace the panel with something like Tint2, that does allow them to be transparent.
Yes I am refering to the borders on things like Firefox or OpenOffice etc., they are all solid black and it kind of irritates me a bit, I'm just being vain.

---

### Post by user333 on 2009-10-07
I wondered this myself, but after a while, I figured it out. You will have to get compiz in order to do this. I got the compiz-fusion too. It can be helpful. You will find everything in in the add/remove app in the applications menu. (I'm assuming you are using ubuntu, and after all, that is a pretty safe, since you *are* on this site :) ) Search for "compiz" and download these things:

> Advanced Desktop Effects Settings (ccsm)

Compiz Fusion Icon

Desktop Effects


Then get emerald themer (for emerald themes), and get a theme off of a place like gnome art. (The link is in my signature) I think you need to put this command into the terminal in order to install emerald: 
> sudo apt-get install emerald

But I read you should do it this way:
> sudo apt-get install emerald libemeraldengine0

I would try the first way first, and if that fails, use the other one. 

Then just find a theme that is transparent. If you like aero clones, here is a good one:

[http://gnome-look.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399]("http://gnome-look.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399")

I hope this helps! and if you want to use a blur (good video card and a fair amount of memory are needed for this) you can enable it by going into the emerald and selecting the settings tab, and enabling "all decorations".

Then in the compiz manager, enable "window blur"

I hope this helps! :)

---

### Post by pop_n_fresh on 2009-11-04
That's not really done the trick to be honest, that's added a border around what I want to make transparent. 

I want the border to be transparent (ie the bit at the top which says 'Ubuntu Forums - Reply to Topic - etc., that is next to my control panel, I'd also like to make the drop down menues (Applications, Places, System) transparent as well like the panel is. Any ideas?

---

### Post by Subban on 2009-11-04
Edit... Do you have Compiz installed and running, for the transparency to work.. just a thought as you said the borders were black. Metacity can do its own transparency now.. using **gconf-editor** open the "**apps**" banch and locate "**metacity**" in the left column. Then in the right hand pane set:
**compositing_manager** with a tick.





Try this, it may be the appearance you are after.

Open up **gconf-editor** from a terminal and then in the left pane click to open the "apps" branch. Scroll down to find **gwd** and then in the right hand pane find these two keys.

metacity_theme_active_opacity
metacity_theme_opacity

Set both values to 0 (zero) which is full transparency, 1 is full opacity.

The effect is instant, changing window decoration can obviously affect the appearance. It might not be quite what you are after effect wise though, give it a try though as its super fast and simple.

Making popup menu's transparent is equally possible using compiz, but tends to make the text and icons transparent also which can make them harder to read, but setting things to blur the background behind the transparency helps a lot.

In compiz advanced settings manager open the "Opacity, Brightness and Saturation" settings found in the Accessibility section. On the Opacity tab the lower section is "Window Specific Settings", add a new entry with:

Tooltip | Menu | PopupMenu | DropdownMenu
and a value of 50 perhaps. 

Then while still in Compiz config ensure that "Blur Windows" is enabled and that in that section "Alpha blur" has a tick, the text box above it should have something like te following in it.. probably default:

normal | Tooltip | Menu | PopupMenu | DropdownMenu

I hope that helps or indeed works at all ;)

If neither method works as you want, then messing around in Emerald might be your best bet if sticking with Gnome as its very easy to make a fully transparent and glasslike window border, as for the popup  menus, there might be a better replacement for that though you may be looking at changing desktop environment perhaps, someone else may need to chip in at that point.

---

### Post by pop_n_fresh on 2009-12-02
Okay, I tried all of that and I've fiddled around with Emerald and it seems to change absolutely nothing. I'm confused.

---

