---
title: "[Conky]refresh adds new duplicate layer every 1 second."
date: 2013-05-04
forum: Desktop Environments
---

### Post by rootSU on 2013-05-04
Hi Everyone,

I do apologise if this is in the wrong area.  Please feel free to move it if it is.  I also apologise if I have not supplied enough info.  Please ask for anything else that may help resolve this and I will happily supply.  I really would love any input you guys may be able to give me please.

This issue first surfaced in Ubuntu 12.10 for me I think.  It wasn't as bad as it is now, since upgrading to 13.04 though.  I use Unity (3d).

The issue essentially is that sometimes (more often than not) my Conky decides on every refresh, to (instead of refreshing) add the refresh as a new layer.  Instead of my Conky display being 1, nice, semi transparent layer, it builds and builds to a ridiculous point.

On 12.10, I could zoom out of my desktop (using the initiate function of the compiz desktop cube) and hold it there for a second and the layers would disappear, leaving 1, nicely refreshing layer.

This is how it should look:

[IMG]http://img.photobucket.com/albums/v420/jungleman/screencap/Screenshotfrom2013-05-04192102.png[/IMG]

Here is an example of what is happening.  It happens when I start it from bash script or terminal manually:

[IMG]http://img.photobucket.com/albums/v420/jungleman/screencap/conky.png[/IMG]

As you can see, the conky process is running only once in this example

Zooming out of the desktop doesn't work since the upgrade, although curiously using the same button combination BEFORE I set up the cube on 13.04 did work - but no longer (maybe a conflict?)

That key combo is Alt + Button 1.

Also please see

.conky.rc

```
background noupdate_interval 1.0
double_buffer yes
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2
text_buffer_size 2048
imlib_cache_size 0
override_utf8_locale yes




# +++++ Window +++++
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


border_inner_margin 0
border_outer_margin 0


minimum_size 1280 800
maximum_width 1280


alignment bottom_middle
gap_x 0
gap_y 0




# +++++ Styles +++++
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes




# +++++ Colors +++++
default_shade_color 101010
default_color 8F8F8F
color0 White        #FFFFFF
color1 Ivory        #FFFFF0
color2 Ivory2        #EEEEE0
color3 Ivory3        #CDCDC1
color4 Tan1        #FFA54F
color5 Tan2        #EE9A49
color6 Gray        #7E7E7E
color7 AntiqueWhite4    #8B8378
color8 DimGray        #696969
color9 Tomato        #FF6347


lua_load ~/.conky/desktopconky.lua


# +++++ LUA +++++
lua_draw_hook_pre ring_stats




# +++++ Font +++++
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.1
uppercase no




TEXT




${goto 530}${color0}Last Backup: ${scroll 25 ${execi 5 cat /home/dan/bash/backup.log}}


${goto 530}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color0}${voffset -2}${hr 1}${font}


${goto 530}${sysname}${goto 650}${kernel}${goto 745}${machine}
${goto 530}Intel${offset 3}core${offset 3}i5-M560${goto 650}${freq_g cpu0}${offset 1}GHz
${goto 530}Kingston${offset 3}DDR3-1333${goto 650}${memmax}${offset 1}
${goto 530}System${offset 3}Uptime${goto 650}${uptime_short}


${goto 530}${font DroidSans:bold:size=8.25}${color4}TOP PROCESSES${offset 8}${color0}${voffset -2}${hr 1}${font}
${goto 1030}CPU4
${goto 530}${top_mem name 1}${goto 650}${top_mem mem_res 1}${goto 1030}${cpu cpu4}%
${goto 530}${top_mem name 2}${goto 650}${top_mem mem_res 2}
${goto 530}${top_mem name 3}${goto 650}${top_mem mem_res 3}${goto 940}CPU2
${goto 530}${top_mem name 4}${goto 650}${top_mem mem_res 4}${goto 940}${cpu cpu2}%
${goto 530}${top_mem name 5}${goto 650}${top_mem mem_res 5}
${goto 530}${top_mem name 6}${goto 650}${top_mem mem_res 6}${goto 860}SWAP
${goto 868}${swap}
${goto 530}${font DroidSans:bold:size=8.25}${color4}NETWORK${offset 8}${color0}${voffset -2}${hr 1}${font}
${goto 800}HOME
${goto 530}Downspeed${goto 650}${downspeed wlan0}${goto 800}${fs_used /home}
${goto 530}Upspeed${goto 650}${upspeed wlan0}


${goto 530}Total Download${goto 650}${totaldown wlan0}
${goto 530}Total Upload${goto 650}${totalup wlan0}


${goto 530}LAN${offset 3}IP${goto 650}${addr wlan0}
${goto 530}WAN${offset 3}IP${goto 650}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}










${goto 428}MediaPC
${goto 435}${fs_used /mnt/MediaPC}
${goto 375}RAM 
${goto 365}${mem}


${goto 290}CPU3 
${goto 290}${cpu cpu3}%


${goto 210}CPU1 
${goto 210}${cpu cpu1}%
${goto 500}${font OpenLogos:size=150}${color2}v${voffset -75}${font}
${goto 510}${font UbuntuTitleBold:size=24}${color4}1${offset 1}3${offset 1}.${offset 0}0${offset 0}4${font}
${voffset -30}${goto 610}${font Ubuntu-B:size=18}${color4}Raring Ringtail${font}
```


And /.conky/desktopconky.lua

```
--[[Ring Meters by londonali1010 (2009)
 
This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]


runscheck = 0 
--#####
if math.mod(runscheck, 2) == 0 then -- fix for draw shades running script twice on every update


conky_background_color = 0x151515
conky_background_alpha = 0


ring_background_color = 0x424242
ring_background_alpha = 0.1
ring_foreground_color = 0x86c113
ring_foreground_color2 = 0x1994d1
ring_foreground_color3 = 0xaa0000
ring_foreground_alpha = 0.3
 
settings_table = {
--    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
--        name='time',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
--        arg='%I.%M',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
--        max=12,
        -- "bg_colour" is the colour of the base ring.
--        bg_colour=ring_background_color,
        -- "bg_alpha" is the alpha value of the base ring.
--        bg_alpha=ring_background_alpha,
        -- "fg_colour" is the colour of the indicator part of the ring.
--        fg_colour=ring_foreground_color,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
--        fg_alpha=ring_foreground_alpha,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
--        x=26, y=25,
        -- "radius" is the radius of the ring.
--        radius=10,
        -- "thickness" is the thickness of the ring, centred around the radius.
--        thickness=6,
        -- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
--        start_angle=0,
        -- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle.
--        end_angle=360
--    },
    {
        name='cpu',
        arg='cpu3',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color,
        fg_alpha=ring_foreground_alpha,
        x=680, y=360,
        radius=410,
        thickness=86,
        start_angle=-120,
        end_angle=-60
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color2,
        fg_alpha=ring_foreground_alpha,
        x=680, y=360,
        radius=510,
        thickness=86,
        start_angle=-120,
        end_angle=-60
    },
    {
        name='cpu',
        arg='cpu2',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color2,
        fg_alpha=ring_foreground_alpha,
        x=580, y=360,
        radius=410,
        thickness=86,
        start_angle=60,
        end_angle=120
    },
    {
        name='cpu',
        arg='cpu4',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color,
        fg_alpha=ring_foreground_alpha,
        x=580, y=360,
        radius=510,
        thickness=86,
        start_angle=60,
        end_angle=120
    },    
    {
        name='swapperc',
        arg='',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color,
        fg_alpha=ring_foreground_alpha,
        x=580, y=360,
        radius=320,
        thickness=66,
        start_angle=60,
        end_angle=120
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color2,
        fg_alpha=ring_foreground_alpha,
        x=680, y=360,
        radius=320,
        thickness=66,
        start_angle=-120,
        end_angle=-60
    },
    {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color2,
        fg_alpha=ring_foreground_alpha,
        x=580, y=360,
        radius=250,
        thickness=46,
        start_angle=60,
        end_angle=90,
    },
    {
        name='fs_used_perc',
        arg='/mnt/MediaPC',
        max=100,
        bg_colour=ring_background_color,
        bg_alpha=ring_background_alpha,
        fg_colour=ring_foreground_color,
        fg_alpha=ring_foreground_alpha,
        x=680, y=360,
        radius=250,
        thickness=46,
        start_angle=-120,
        end_angle=-90,
    }
}
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end


function conky_round_rect(cr, x0, y0, w, h, r)
    if (w == 0) or (h == 0) then return end
    local x1 = x0 + w
    local y1 = y0 + h
    if w/2 < r then
        if h/2 < r then
            cairo_move_to  (cr, x0, (y0 + y1)/2)
            cairo_curve_to (cr, x0 ,y0, x0, y0, (x0 + x1)/2, y0)
            cairo_curve_to (cr, x1, y0, x1, y0, x1, (y0 + y1)/2)
            cairo_curve_to (cr, x1, y1, x1, y1, (x1 + x0)/2, y1)
            cairo_curve_to (cr, x0, y1, x0, y1, x0, (y0 + y1)/2)
        else
            cairo_move_to  (cr, x0, y0 + r)
            cairo_curve_to (cr, x0 ,y0, x0, y0, (x0 + x1)/2, y0)
            cairo_curve_to (cr, x1, y0, x1, y0, x1, y0 + r)
            cairo_line_to (cr, x1 , y1 - r)
            cairo_curve_to (cr, x1, y1, x1, y1, (x1 + x0)/2, y1)
            cairo_curve_to (cr, x0, y1, x0, y1, x0, y1- r)
        end
    else
        if h/2 < r then
            cairo_move_to  (cr, x0, (y0 + y1)/2)
            cairo_curve_to (cr, x0 , y0, x0 , y0, x0 + r, y0)
            cairo_line_to (cr, x1 - r, y0)
            cairo_curve_to (cr, x1, y0, x1, y0, x1, (y0 + y1)/2)
            cairo_curve_to (cr, x1, y1, x1, y1, x1 - r, y1)
            cairo_line_to (cr, x0 + r, y1)
            cairo_curve_to (cr, x0, y1, x0, y1, x0, (y0 + y1)/2)
        else
            cairo_move_to  (cr, x0, y0 + r)
            cairo_curve_to (cr, x0 , y0, x0 , y0, x0 + r, y0)
            cairo_line_to (cr, x1 - r, y0)
            cairo_curve_to (cr, x1, y0, x1, y0, x1, y0 + r)
            cairo_line_to (cr, x1 , y1 - r)
            cairo_curve_to (cr, x1, y1, x1, y1, x1 - r, y1)
            cairo_line_to (cr, x0 + r, y1)
            cairo_curve_to (cr, x0, y1, x0, y1, x0, y1- r)
        end
    end
    cairo_close_path (cr)
end


 
function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
 
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)
 
    -- Draw background ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end
 
cs, cr = nil -- initialize our cairo surface and context to nil
function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
 
        draw_ring(cr,pct,pt)
    end
 
    if conky_window==nil then return end
    --local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
    --local cr=cairo_create(cs)


    if cs == nil or cairo_xlib_surface_get_width(cs) ~= conky_window.width or cairo_xlib_surface_get_height(cs) ~= conky_window.height then
        if cs then cairo_surface_destroy(cs) end
        cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    end
    if cr then cairo_destroy(cr) end
    cr = cairo_create(cs)


 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        conky_round_rect(cr, 3, 0, conky_window.width-6, conky_window.height-3, 15)
        cairo_set_source_rgba(cr, rgb_to_r_g_b(conky_background_color, conky_background_alpha))
        cairo_fill(cr)
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
    cairo_destroy(cr)
    cr = nil
end


function conky_cairo_cleanup()
    cairo_surface_destroy(cs)
    cs = nil
end


end -- math.mod(runscheck, 2) == 0
runscheck = runscheck + 1



```

Has anyone seen anything like this before?

Any advice or troubleshooting tips anyone could give me please, would surely be greatly appreciated.

Thanking you in advance

---

### Post by stinkeye on 2013-05-05
The way the setting "own_window_type" behaves, seems to change with each Ubuntu release.
Try replacing **own_window_type override**
with
```
own_window_type normal
```

If your conky window now has an unwanted shadow see [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2076882&p=12584657&viewfull=1#post12584657").

---

### Post by rootSU on 2013-05-05
Thank you for the suggestion.  I have made the adjustment and will feedback after a period of monitoring.

Thank you for taking the time to read this.

edit > The CCSM shadows setting resolved that issue too.  Thanks

---

### Post by stinkeye on 2013-05-05
> **rootSU said:**
> Thank you for the suggestion.  I have made the adjustment and will feedback after a period of monitoring.

Thank you for taking the time to read this.

edit > The CCSM shadows setting resolved that issue too.  Thanks
No probs.

Also in your conkyrc, is the first line a copy/paste error...
```
background noupdate_interval 1.0
```

Should be 2 lines...
```
background no
update_interval 1.0

```

---

### Post by gordintoronto on 2013-05-05
I also suggest going to a 5-second update interval.

---

### Post by rootSU on 2013-05-06
> **stinkeye said:**
> No probs.

Also in your conkyrc, is the first line a copy/paste error...
```
background noupdate_interval 1.0
```

Should be 2 lines...
```
background no
update_interval 1.0

```

Thank you and well spotted.  It is a copy / paste error.  It is 2 distinct lines in the .conky.rc ;)

Your suggestion has worked so thank you once more, I will mark as solved.

One thing though, after a reboot, I noticed that conky overrode my wallpaper with a black screen so I also set own window no.  This comes with it's own drawbacks though, in that as I minimise other windows, it disappears for a split second.  I may try own_window_argb_visual yes [COLOR=#333333][FONT=Ubuntu Mono]own_window_[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]argb_visual yes'[/FONT][/COLOR]

> **gordintoronto said:**
> I also suggest going to a 5-second update interval.

Thanks, but 1 second is long enough for me.  I wan't the CPU load to give as "live" a picture as possible.  1 second is my best compromise.

---

### Post by stinkeye on 2013-05-06
Are you delaying the start of your conky to allow the window manager time to load?

Conky has an in built pause feature (-p secs)
eg Delay start for 20secs...needed at boot when using compiz.
```
conky -p 20
```

Decrease/increase pause for your load time.

---

### Post by rootSU on 2013-05-06
Yep, I delay by 2 minutes.

```
own_window yes
own_window_type normal
own_window_arbg_visual yes
```

seems to work great, thank you.

---

### Post by stinkeye on 2013-05-06
OK, goodluck.

PS: where the conky nuts hang out...
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2189&p=12634867#post12634867")

---

