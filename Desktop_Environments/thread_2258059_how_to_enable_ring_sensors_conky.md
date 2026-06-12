---
title: "how to enable ring sensors conky"
date: 2014-12-24
forum: Desktop Environments
---

### Post by frankyboynl on 2014-12-24
hello, I am trying to install some ring-sensors in conky-manager, but cannot seem to get them working properly. any suggestions??



grtz, Frank

---

### Post by Frogs Hair on 2014-12-24
Which sensors ? The image suggests there is an output from all except Internet which is set for a wireless connection. If you are using wired Internet the syntax in .conkyrc would need to be changed. I don't know if conky manager allows the user to select connection type or if you have to edit .conkyrc yourself. I think conky manager installs most if not all programs needed to display system information.

---

### Post by frankyboynl on 2014-12-24
my point is, I want the output of conky to be like that screenshot, but when I download it and install it in the .conky directory, it shows only the data, no graphical rings...



grtz, Frank

---

### Post by deadflowr on 2014-12-24
Post the conkyrc file.
Also, do you have the lua files(scripts) for the rings?

If you have the lua files you need to make sure the paths in the conkyrc file are set right.

Look for the lines for the rings in the conkyrc file, usually those lines are listed right before TEXT.

---

### Post by frankyboynl on 2014-12-24
```
# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit celsius

# Window specifications #
own_window_class Conky
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 520 600
maximum_width 520

alignment bottom_left
gap_x -20
gap_y 100

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

default_color gray
default_shade_color red
default_outline_color green

# Text settings #
use_xft yes
override_utf8_locale yes
xftfont Play:normal:size=7
xftalpha 0.9
uppercase no

default_color 333333
color0 414569
color1 333333
color2 1994D1
#color3 1994D1 

# Lua Load  ##${voffset 750}
lua_load ~/conky/rings-v1.2.1.lua
#lua_draw_hook_pre ring_stats
lua_draw_hook_pre conky_main

own_window_argb_value 0
own_window_argb_visual no
own_window_colour 000000
TEXT
${font Play:normal:size=7}${voffset 16}${color1}${goto 120}${freq_g cpu0} Ghz${alignr 330}${acpitemp} °C
${font Play:normal:size=7}${voffset 0}${goto 120}${color1}CPU 1 ${alignr 330}${color1}${cpu cpu0}%
${font Play:normal:size=7}${voffset 2}${goto 120}${color1}CPU 2${alignr 330}${color1}${cpu cpu1}%
${font Play:normal:size=7}${voffset 2}${goto 120}${color1}CPU 3${alignr 330}${color1}${cpu cpu2}%
${font Play:normal:size=7}${voffset 2}${goto 120}${color1}CPU 4${alignr 330}${color1}${cpu cpu3}%
${goto 50}${voffset 16}${font Play:normal:size=7}${color1}${top name 1}${alignr 306}${top cpu 1}%
${goto 50}${font Play:normal:size=7}${color1}${top name 2}${alignr 306}${top cpu 2}%
${goto 50}${font Play:normal:size=7}${color1}${top name 3}${alignr 306}${top cpu 3}%
${font Michroma:size=10}${color0}${goto 80}${voffset 4}CPU 
${font Michroma:size=10}${color0}${goto 394}${voffset 44}MEMORY
${goto 324}${voffset -6}${font Play:normal:size=7}${color1}${top_mem name 1}${alignr 40}${top_mem mem 1}%
${goto 324}${font Play:normal:size=7}${color1}${top_mem name 2}${alignr 40}${top_mem mem 2}%
${goto 324}${font Play:normal:size=7}${color1}${top_mem name 3}${alignr 40}${top_mem mem 3}%
${font Play:normal:size=7}${voffset 14}${goto 348}${color1}SWAP${alignr 40}${color1}${swap} / ${color1}${swapmax}
${font Play:normal:size=7}${voffset 4}${goto 348}${color1}RAM ${alignr 40}${color1}${mem} / ${color1}${memmax}
${font Play:normal:size=7}${goto 80}${voffset -68}Root${color1}${alignr 310}${fs_used /} / ${fs_size /}
${font Play:normal:size=7}${goto 80}${voffset 0}Home${alignr 310}${color1}${fs_used /home} / ${fs_size /home}
${font Play:normal:size=7}${goto 80}${voffset 0}Usr${alignr 310}${color1}${fs_used /usr} / ${fs_size /usr}
${font Michroma:size=10}${color0}${goto 66}${voffset 10}HARD  DRIVE
${font Michroma:size=10}${color0}${voffset 26}${goto 324}INTERNET  INFO
# EDITION FINIR WLAN
${if_existing /proc/net/route wlan0}${font Play:normal:size=7}${color1}${alignr 54}${voffset -8}WiFi  ${color1}${wireless_essid wlan0}
${font Play:normal:size=7}${color1}${goto 298}${voffset 2}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr wlan0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %x}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}
${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERIE
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT1}%
# |--ETH0
${else}${if_existing /proc/net/route eth0}${font Play:normal:size=7}${color1}${goto 298}${voffset 6}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr eth0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${font Michroma:size=9}${alignr 298}${voffset -42}${color0}${time %a} ${color0}${time %x}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}
${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERIE
${font Play:size=8}${color0}${goto 278}${voffset 4}${color1}${battery_percent BAT1}%${endif}${endif}
#${font Play:normal:size=7}${goto 180}Uptime${color1}${alignr 100}${uptime_short}
${font Michroma:size=11}${color0}${voffset 70}${alignr 130}${pre_exec cat /etc/issue.net}  ${machine}
#${execpi 53 $HOME/conky/nagios.sh}
```

---

### Post by deadflowr on 2014-12-24
> lua_load ~/conky/rings-v1.2.1.lua

So do you have a file for rings-v1.2.1.lua inside the conky folder?

---

### Post by frankyboynl on 2014-12-24
yes, there is actually:

```

-[[
Ring Meters by londonali1010 (2009)

This script draws percentage meters as rings. It is fully customisable; all options are described in the script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement near the end of the script uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats
    
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)

        arg=conky_parse("${if_up wlan0}wlan0${else}eth0${endif}"),
        fg_colour=0xf0651f,
        fg_colour=conky_parse("${if_up wlan0}wlan0${else}eth0${endif}"),
        conky_parse("${cpu}")
        name=conky_parse("${acpitemp}"),
]]

-- A TESTER
--set alarm value, this is the value at which bar color will change
--alarm_value=80
----set alarm bar color, 1,0,0,1 = red fully opaque
--ar,ag,ab,aa=1,0,0,1

-- couleurs 1
-- 1faaf0
-- f0651f
-- f01f42
-- couleurs 2 + flashy
-- 008cff
-- ff7200
-- ff000d

--normal_temp="0x1faaf0"
--warn_temp="0xf0651f"
--crit_temp="0xf01f42"
-- Un mélange des deux
normal="0x1faaf0"
warn="0xff7200"
crit="0xff000d"

-- seulement quand fond nécessaire
corner_r=35
bg_colour=0x333333
bg_alpha=0.2


settings_table = {
    
    {
        name='acpitemp',
        arg='',
        max=110,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=200, y=120,
        radius=97,
        thickness=4,
        start_angle=0,
        end_angle=240
    },
    {
        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=200, y=120,
        radius=86,
        thickness=13,
        start_angle=0,
        end_angle=240
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.7,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=200, y=120,
        radius=71,
        thickness=12,
        start_angle=0,
        end_angle=240
    },
    {
        name='cpu',
        arg='cpu2',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=200, y=120,
        radius=57,
        thickness=11,
        start_angle=0,
        end_angle=240
    },
    {
        name='cpu',
        arg='cpu3',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.5,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=200, y=120,
        radius=44,
        thickness=10,
        start_angle=0,
        end_angle=240
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=340, y=234,
        radius=60,
        thickness=15,
        start_angle=180,
        end_angle=420
    },
    {
        name='swapperc',
        arg='',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.4,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=340, y=234,
        radius=45,
        thickness=10,
        start_angle=180,
        end_angle=420
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=220, y=280,
        radius=40,
        thickness=10,
        start_angle=0,
        end_angle=240
    },
    {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=220, y=280,
        radius=28,
        thickness=10,
        start_angle=0,
        end_angle=240
    },
    {
        name='fs_used_perc',
        arg='/usr',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.4,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=220, y=280,
        radius=16,
        thickness=10,
        start_angle=0,
        end_angle=240
    },
    {
        name='downspeedf',
        arg='',
        max=2000,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=290, y=346,
        radius=30,
        thickness=12,
        start_angle=180,
        end_angle=420
    },
    {
        name='upspeedf',
        arg='',
        max=200,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=290, y=346,
        radius=18,
        thickness=8,
        start_angle=180,
        end_angle=420
    },
    {
        name='time',
        arg='%S',
        max=60,
        bg_colour=0x000000,
        bg_alpha=0.8,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=230, y=410,
        radius=30,
        thickness=12,
        start_angle=0,
        end_angle=240
    },
    {
        name='time',
        arg='%M',
        max=60,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=230, y=410,
        radius=18,
        thickness=8,
        start_angle=0,
        end_angle=240
    },
    {
        name='time',
        arg='%H',
        max=24,
        bg_colour=0x000000,
        bg_alpha=0.4,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=230, y=410,
        radius=10,
        thickness=4,
        start_angle=0,
        end_angle=240
    },
    {
        name='battery_percent',
        arg='BAT1',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.8,
        x=274, y=464,
        radius=18,
        thickness=10,
        start_angle=180,
        end_angle=420
    },
    {
        name='',
        arg='',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.6,
        fg_colour=0x1faaf0,
        fg_alpha=0.6,
        x=274, y=464,
        radius=3,
        thickness=13,
        start_angle=0,
        end_angle=360
    },
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
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
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)

    if update_num>5 then
        for i in pairs(settings_table) do
                display_temp=temp_watch()
        setup_rings(cr,settings_table[i])
        end
    end
   cairo_surface_destroy(cs)
  cairo_destroy(cr)
end

-- Contrôle de l'espace disque
function disk_watch()

    warn_disk=93
    crit_disk=98

    -- poser une boucle plus tard... pas simple

    disk=tonumber(conky_parse("${fs_used_perc /}"))

    if disk<warn_disk then
        settings_table[8]['fg_colour']=normal
    elseif disk<crit_disk then
        settings_table[8]['fg_colour']=warn
    else
        settings_table[8]['fg_colour']=crit
    end

    disk=tonumber(conky_parse("${fs_used_perc /home}"))

    if disk<warn_disk then
        settings_table[9]['fg_colour']=normal
    elseif disk<crit_disk then
        settings_table[9]['fg_colour']=warn
    else
        settings_table[9]['fg_colour']=crit
    end

    disk=tonumber(conky_parse("${fs_used_perc /usr}"))

    if disk<warn_disk then
        settings_table[10]['fg_colour']=normal
    elseif disk<crit_disk then
        settings_table[10]['fg_colour']=warn
    else
        settings_table[10]['fg_colour']=crit
    end
end

-- Contrôle de la température
function temp_watch()

    warn_value=70
    crit_value=80

    temperature=tonumber(conky_parse("${acpitemp}"))

    if temperature<warn_value then
        settings_table[1]['fg_colour']=normal
    elseif temperature<crit_value then
        settings_table[1]['fg_colour']=warn
    else
        settings_table[1]['fg_colour']=crit
    end
end

-- Contrôle de l'interface active
function iface_watch()

    iface=conky_parse("${if_existing /proc/net/route eth0}eth0${else}wlan0${endif}")

    settings_table[11]['arg']=iface
    settings_table[12]['arg']=iface
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


function conky_main()
    temp_watch()
    disk_watch()
    iface_watch()
    conky_ring_stats()
-- quand fond nécessaire
--    conky_draw_bg()
end
```

---

### Post by deadflowr on 2014-12-24
Try uncommenting (#) the line below it 
*#lua_draw_hook_pre ring_stats*
to this
*lua_draw_hook_pre ring_stats*
and add a commen to the line for
*lua_draw_hook_pre conky_main*
like
[I]#lua_draw_hook_pre conky_main

[/I]I don't know if the hook command needs to be before or after the file entry or not, so you might look at moving the line above the file entries line, as well.

---

### Post by frankyboynl on 2014-12-24
Thanks a lot!!! this indeed worked for me!!


thanks, Frank

---

### Post by deadflowr on 2014-12-24
Glad to see.
I decided to  have a quick look at the conkyrc --I only wanted the top section before TEXT stuff, and the lua.
When I actually read the lua it states quite clearly:
> To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats


The # symbol tells the system to ignore that line, which is what was happening.

If you feel that the problem has been solved please[ mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

