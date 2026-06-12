---
title: "How to make conky windows transparent in 9.10?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by josephellengar on 2009-11-22
The old way I did it in 8.10 doesn't work any more.  I used to just use compiz opacity, but it's not working.  I want them to be semi-transparent, so that I can see my background.  Also, anybody have any idea how I can disable the minimize animation?  I just switched from 8.1 to 9.1, so I've got some searching to do.  Thanks!

---

### Post by taavi on 2010-02-01
Gratz on 1st hit on Google: conky ubuntu transparent 9.10

I was wandering the same, has anyone come up with decent solution. I'm not using Compiz -- plain nautilus or whatever is that what Ubuntu uses OOB

---

### Post by stinkeye on 2010-02-01
> **taavi said:**
> Gratz on 1st hit on Google: conky ubuntu transparent 9.10

I was wandering the same, has anyone come up with decent solution. I'm not using Compiz -- plain nautilus or whatever is that what Ubuntu uses OOB
If your not using compiz, metacity is your window manager.
If you just want your conky window to be transparent
check these settings in your conky config
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
draw_borders no
```


You can give conky a nice semi-transparent background with rounded corners using this script
from **londonali1010** using Lua/Cairo.
It will draw a background to the size of your conky window.
```
--[[
Background by londonali1010 (2009)
 
This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.
 
To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre
 
Changelog:
+ v1.0 -- Original release (07.10.2009)
]]
 
-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.
 
corner_r=15
 
-- Set the colour and transparency (alpha) of your background.
 
bg_colour=0xffffff
bg_alpha=0.5
 
require 'cairo'
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function conky_draw_bg()
	if conky_window==nil then return end
	local w=conky_window.width
	local h=conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
	cr=cairo_create(cs)
 
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h-corner_r)
	cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
	cairo_line_to(cr,corner_r,h)
	cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)
 
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)
end
```
Save as ```
draw_bg.lua
```
and make executable.

Add this to your conky above "TEXT"
```
lua_load [COLOR="DarkRed"]/home/glen/conky[/COLOR]/draw_bg.lua
lua_draw_hook_pre draw_bg
```
changing the highlighted path to where you saved *draw_bg.lua*

You need to be using the conky-all package with Lua/Cairo support, from synaptic.

If your using metacity you need to turn off it's compositng_manager.
gconf-editor /apps/metacity/general/compositing_manager.
Otherwise it will look like this:
[ATTACH]145595[/ATTACH]

What it should look like:
[ATTACH]145596[/ATTACH]

If it's not drawing add these to your conky above "TEXT"
```
max_specials 1024
max_user_text 4000
text_buffer_size 2048
imlib_cache_size 0
```

For anyone else reading this and needs to turn off the shadow effect caused by compiz
goto ccsm > effects > Window Decoration > shadow windows and add this
```
(any) & !(class=Conky)
```

---

### Post by Quint2020 on 2010-07-06
I'm currently messing around with londonali1010's script and while I've got it to launch fine it's actually drawing the transparent "mask" all over my desktop rather than just where conky sits.... Any ideas anyone??

EDIT: Cancel that, I've figured it out

.conkyrf needs the following line:

own_window yes

I originally set it to no....

---

