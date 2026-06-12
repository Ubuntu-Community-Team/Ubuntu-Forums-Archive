---
title: "Conky Multiple Monitor (already tried gap_x)"
date: 2013-03-30
forum: Desktop Environments
---

### Post by Slimmons on 2013-03-30
Hi, I have worked with conky a decent amount, and I've come into a problem using one that I found pre made.  It works on single monitor, and when I use dual monitor, I've tried every variation of gap_x I can think of, and I thought possibly it's because this uses a .lua file as well.  I have two 1920x1080 monitors.  On my other conky files, i just gap_x 1920, and they show correctly on the left monitor at top right.  

conkyrc_grey    
```
background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius

double_buffer yes
no_buffers yes
text_buffer_size 2048


minimum_size 190 450
maximum_width 190
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment tr
gap_x 1920
gap_y 30

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 666666

lua_load ~/.conky/conky_grey.lua
lua_draw_hook_post main

TEXT
${voffset 35}
${goto 95}${color4}${font ubuntu:size=22}${time %e}${color1}${offset -50}${font ubuntu:size=10}${time %A}
${goto 85}${color2}${voffset -2}${font ubuntu:size=9}${time %b}${voffset -2} ${color3}${font ubuntu:size=12}${time %Y}${font}

${voffset 80}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}CPU
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top name 1}${alignr}${top cpu 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top name 2}${alignr}${top cpu 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top name 3}${alignr}${top cpu 3}%
${goto 90}${cpugraph 10,100 666666 666666}
${goto 90}${voffset -10}${font Ubuntu:size=7,weight:normal}${color}${threads} process 

${voffset 20}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}MEM
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top_mem name 1}${alignr}${top_mem mem 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top_mem name 2}${alignr}${top_mem mem 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top_mem name 3}${alignr}${top_mem mem 3}%

${voffset 15}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}DISKS

${goto 90}${diskiograph 30,100 666666 666666}${voffset -30}
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /home} /home
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /} /

${voffset 10}
${goto 70}${font Ubuntu:size=18,weight:bold}${color3}NET${alignr}${color2}${font Ubuntu:size=7,weight:bold}${color1}${if_up eth0}eth ${addr eth0} ${endif}${if_up wlan0}wifi ${addr wlan0}${endif}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}open ports: ${alignr}${color2}${tcp_portmon 1 65535 count}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}${offset 10}IP${alignr}DPORT
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  0}${alignr 1}${tcp_portmon 1 65535 rport  0}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  1}${alignr 1}${tcp_portmon 1 65535 rport  1}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  2}${alignr 1}${tcp_portmon 1 65535 rport  2}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  3}${alignr 1}${tcp_portmon 1 65535 rport  3}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  4}${alignr 1}${tcp_portmon 1 65535 rport  4}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  5}${alignr 1}${tcp_portmon 1 65535 rport  5}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  6}${alignr 1}${tcp_portmon 1 65535 rport  6}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  7}${alignr 1}${tcp_portmon 1 65535 rport  7}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  8}${alignr 1}${tcp_portmon 1 65535 rport  8}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  9}${alignr 1}${tcp_portmon 1 65535 rport  9}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 10}${alignr 1}${tcp_portmon 1 65535 rport 10}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 11}${alignr 1}${tcp_portmon 1 65535 rport 11}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 12}${alignr 1}${tcp_portmon 1 65535 rport 12}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 13}${alignr 1}${tcp_portmon 1 65535 rport 13}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 14}${alignr 1}${tcp_portmon 1 65535 rport 14}


```


conky_grey.lua
```

require 'cairo'

--------------------------------------------------------------------------------
--                                                                    clock DATA
-- HOURS
clock_h = {
    {
    name='time',                   arg='%H',                    max_value=12,
    x=110,                         y=80,
    graph_radius=53,
    graph_thickness=3,
    graph_unit_angle=30,           graph_unit_thickness=30,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.0,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.3,
    txt_radius=34,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.6,
    graduation_radius=53,
    graduation_thickness=6,        graduation_mark_thickness=2,
    graduation_unit_angle=30,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    },
}
-- MINUTES
clock_m = {
    {
    name='time',                   arg='%M',                    max_value=60,
    x=110,                         y=80,
    graph_radius=57,
    graph_thickness=2,
    graph_unit_angle=6,            graph_unit_thickness=6,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.3,
    txt_radius=70,
    txt_weight=0,                  txt_size=9.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.6,
    graduation_radius=57,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=30,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    },
}
-- SECONDS
clock_s = {
    {
    name='time',                   arg='%S',                    max_value=60,
    x=110,                         y=80,
    graph_radius=50,
    graph_thickness=2,
    graph_unit_angle=6,            graph_unit_thickness=2,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.0,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.2,
    txt_radius=40,
    txt_weight=0,                  txt_size=12.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.3,
    graduation_radius=0,
    graduation_thickness=0,        graduation_mark_thickness=0,
    graduation_unit_angle=0,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.0,
    },
}

--------------------------------------------------------------------------------
--                                                                    gauge DATA
gauge = {
{
    name='cpu',                    arg='cpu0',                  max_value=100,
    x=85,                          y=200,
    graph_radius=24,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.5,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=0.0,
    txt_radius=34,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.3,
    graduation_radius=28,
    graduation_thickness=0,        graduation_mark_thickness=1,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.3,
},
{
    name='cpu',                    arg='cpu1',                  max_value=100,
    x=85,                          y=200,
    graph_radius=18,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.5,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=0.0,
    txt_radius=10,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.3,
    graduation_radius=28,
    graduation_thickness=0,        graduation_mark_thickness=1,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.3,
},
{
    name='memperc',                arg='',                      max_value=100,
    x=85,                          y=300,
    graph_radius=24,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.5,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=0.0,
    txt_radius=10,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.3,
    graduation_radius=23,
    graduation_thickness=8,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.5,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.3,
},
{
    name='fs_used_perc',           arg='/',                     max_value=100,
    x=85,                          y=380,
    graph_radius=24,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.5,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=0.0,
    txt_radius=34,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.5,
    graduation_radius=28,
    graduation_thickness=0,        graduation_mark_thickness=1,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='/',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
},
{
    name='fs_used_perc',           arg='/home/',                max_value=100,
    x=85,                          y=380,
    graph_radius=18,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.5,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=0.0,
    txt_radius=10,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.5,
    graduation_radius=28,
    graduation_thickness=0,        graduation_mark_thickness=1,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='/home',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
},
}

-------------------------------------------------------------------------------
--                                                                 rgb_to_r_g_b
-- converts color in hexa to decimal
--
function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-------------------------------------------------------------------------------
--                                                            angle_to_position
-- convert degree to rad and rotate (0 degree is top/north)
--
function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * math.pi / 360) ) - (math.pi / 2) )
end

-------------------------------------------------------------------------------
--                                                              draw_clock_ring
-- displays clock
--
function draw_clock_ring(display, data, value)
    local max_value = data['max_value']
    local x, y = data['x'], data['y']
    local graph_radius = data['graph_radius']
    local graph_thickness, graph_unit_thickness = data['graph_thickness'], data['graph_unit_thickness']
    local graph_unit_angle = data['graph_unit_angle']
    local graph_bg_colour, graph_bg_alpha = data['graph_bg_colour'], data['graph_bg_alpha']
    local graph_fg_colour, graph_fg_alpha = data['graph_fg_colour'], data['graph_fg_alpha']

    -- background ring
    cairo_arc(display, x, y, graph_radius, 0, 2 * math.pi)
    cairo_set_source_rgba(display, rgb_to_r_g_b(graph_bg_colour, graph_bg_alpha))
    cairo_set_line_width(display, graph_thickness)
    cairo_stroke(display)

    -- arc of value
    local val = (value % max_value)
    local i = 1
    while i <= val do
        cairo_arc(display, x, y, graph_radius,(  ((graph_unit_angle * i) - graph_unit_thickness)*(2*math.pi/360)  )-(math.pi/2),((graph_unit_angle * i) * (2*math.pi/360))-(math.pi/2))
        cairo_set_source_rgba(display,rgb_to_r_g_b(graph_fg_colour,graph_fg_alpha))
        cairo_stroke(display)
        i = i + 1
    end
    local angle = (graph_unit_angle * i) - graph_unit_thickness

    -- graduations marks
    local graduation_radius = data['graduation_radius']
    local graduation_thickness, graduation_mark_thickness = data['graduation_thickness'], data['graduation_mark_thickness']
    local graduation_unit_angle = data['graduation_unit_angle']
    local graduation_fg_colour, graduation_fg_alpha = data['graduation_fg_colour'], data['graduation_fg_alpha']
    if graduation_radius > 0 and graduation_thickness > 0 and graduation_unit_angle > 0 then
        local nb_graduation = 360 / graduation_unit_angle
        local i = 1
        while i <= nb_graduation do
            cairo_set_line_width(display, graduation_thickness)
            cairo_arc(display, x, y, graduation_radius, (((graduation_unit_angle * i)-(graduation_mark_thickness/2))*(2*math.pi/360))-(math.pi/2),(((graduation_unit_angle * i)+(graduation_mark_thickness/2))*(2*math.pi/360))-(math.pi/2))
            cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_colour,graduation_fg_alpha))
            cairo_stroke(display)
            cairo_set_line_width(display, graph_thickness)
            i = i + 1
        end
    end

    -- text
    local txt_radius = data['txt_radius']
    local txt_weight, txt_size = data['txt_weight'], data['txt_size']
    local txt_fg_colour, txt_fg_alpha = data['txt_fg_colour'], data['txt_fg_alpha']
    local movex = txt_radius * (math.cos((angle * 2 * math.pi / 360)-(math.pi/2)))
    local movey = txt_radius * (math.sin((angle * 2 * math.pi / 360)-(math.pi/2)))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, txt_weight);
    cairo_set_font_size (display, txt_size);
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_colour, txt_fg_alpha));
    cairo_move_to (display, x + movex - (txt_size / 2), y + movey + 3);
    cairo_show_text (display, value);
    cairo_stroke (display);
end

-------------------------------------------------------------------------------
--                                                              draw_gauge_ring
-- displays gauges
--
function draw_gauge_ring(display, data, value)
    local max_value = data['max_value']
    local x, y = data['x'], data['y']
    local graph_radius = data['graph_radius']
    local graph_thickness, graph_unit_thickness = data['graph_thickness'], data['graph_unit_thickness']
    local graph_start_angle = data['graph_start_angle']
    local graph_unit_angle = data['graph_unit_angle']
    local graph_bg_colour, graph_bg_alpha = data['graph_bg_colour'], data['graph_bg_alpha']
    local graph_fg_colour, graph_fg_alpha = data['graph_fg_colour'], data['graph_fg_alpha']
    local hand_fg_colour, hand_fg_alpha = data['hand_fg_colour'], data['hand_fg_alpha']
    local graph_end_angle = (max_value * graph_unit_angle) % 360

    -- background ring
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, 0), angle_to_position(graph_start_angle, graph_end_angle))
    cairo_set_source_rgba(display, rgb_to_r_g_b(graph_bg_colour, graph_bg_alpha))
    cairo_set_line_width(display, graph_thickness)
    cairo_stroke(display)

    -- arc of value
    local val = value % (max_value + 1)
    local start_arc = 0
    local stop_arc = 0
    local i = 1
    while i <= val do
        start_arc = (graph_unit_angle * i) - graph_unit_thickness
        stop_arc = (graph_unit_angle * i)
        cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
        cairo_set_source_rgba(display, rgb_to_r_g_b(graph_fg_colour, graph_fg_alpha))
        cairo_stroke(display)
        i = i + 1
    end
    local angle = start_arc

    -- hand
    start_arc = (graph_unit_angle * val) - (graph_unit_thickness * 2)
    stop_arc = (graph_unit_angle * val)
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
    cairo_set_source_rgba(display, rgb_to_r_g_b(hand_fg_colour, hand_fg_alpha))
    cairo_stroke(display)

    -- graduations marks
    local graduation_radius = data['graduation_radius']
    local graduation_thickness, graduation_mark_thickness = data['graduation_thickness'], data['graduation_mark_thickness']
    local graduation_unit_angle = data['graduation_unit_angle']
    local graduation_fg_colour, graduation_fg_alpha = data['graduation_fg_colour'], data['graduation_fg_alpha']
    if graduation_radius > 0 and graduation_thickness > 0 and graduation_unit_angle > 0 then
        local nb_graduation = graph_end_angle / graduation_unit_angle
        local i = 0
        while i < nb_graduation do
            cairo_set_line_width(display, graduation_thickness)
            start_arc = (graduation_unit_angle * i) - (graduation_mark_thickness / 2)
            stop_arc = (graduation_unit_angle * i) + (graduation_mark_thickness / 2)
            cairo_arc(display, x, y, graduation_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
            cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_colour,graduation_fg_alpha))
            cairo_stroke(display)
            cairo_set_line_width(display, graph_thickness)
            i = i + 1
        end
    end

    -- text
    local txt_radius = data['txt_radius']
    local txt_weight, txt_size = data['txt_weight'], data['txt_size']
    local txt_fg_colour, txt_fg_alpha = data['txt_fg_colour'], data['txt_fg_alpha']
    local movex = txt_radius * math.cos(angle_to_position(graph_start_angle, angle))
    local movey = txt_radius * math.sin(angle_to_position(graph_start_angle, angle))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, txt_weight)
    cairo_set_font_size (display, txt_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_colour, txt_fg_alpha))
    cairo_move_to (display, x + movex - (txt_size / 2), y + movey + 3)
    cairo_show_text (display, value)
    cairo_stroke (display)

    -- caption
    local caption = data['caption']
    local caption_weight, caption_size = data['caption_weight'], data['caption_size']
    local caption_fg_colour, caption_fg_alpha = data['caption_fg_colour'], data['caption_fg_alpha']
    local tox = graph_radius * (math.cos((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    local toy = graph_radius * (math.sin((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, caption_weight);
    cairo_set_font_size (display, caption_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(caption_fg_colour, caption_fg_alpha))
    cairo_move_to (display, x + tox + 5, y + toy + 1)
    -- bad hack but not enough time !
    if graph_start_angle < 105 then
        cairo_move_to (display, x + tox - 30, y + toy + 1)
    end
    cairo_show_text (display, caption)
    cairo_stroke (display)
end

-------------------------------------------------------------------------------
--                                                               go_clock_rings
-- loads data and displays clock
--
function go_clock_rings(display)
    local function load_clock_rings(display, data)
        local str, value = '', 0
        str = string.format('${%s %s}',data['name'], data['arg'])
        str = conky_parse(str)
        value = tonumber(str)
        draw_clock_ring(display, data, value)
    end
    
    for i in pairs(clock_h) do
        load_clock_rings(display, clock_h[i])
    end
    for i in pairs(clock_m) do
        load_clock_rings(display, clock_m[i])
    end
    for i in pairs(clock_s) do
        load_clock_rings(display, clock_s[i])
    end
end

-------------------------------------------------------------------------------
--                                                               go_gauge_rings
-- loads data and displays gauges
--
function go_gauge_rings(display)
    local function load_gauge_rings(display, data)
        local str, value = '', 0
        str = string.format('${%s %s}',data['name'], data['arg'])
        str = conky_parse(str)
        value = tonumber(str)
        draw_gauge_ring(display, data, value)
    end
    
    for i in pairs(gauge) do
        load_gauge_rings(display, gauge[i])
    end
end

-------------------------------------------------------------------------------
--                                                                         MAIN
function conky_main()
    if conky_window == nil then 
        return
    end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local display = cairo_create(cs)
    
    local updates = conky_parse('${updates}')
    update_num = tonumber(updates)
    
    if update_num > 5 then
        go_clock_rings(display)
        go_gauge_rings(display)
    end
    
    cairo_surface_destroy(cs)
    cairo_destroy(display)
end


```

---

### Post by Slimmons on 2013-03-30
Just an update in case anybody wants to try and answer.  I have tried several other conky files, and I haven't been able to move any conky with a .lua to a visible location on dual monitors.  The problem is still the original, but I've tried several other files other than the above mentioned.

I have tried moving the x= in the .lua files as well as different orientations on the conky file.  I am guessing for now that there is a possibility that the inclusion of the .lua files somehow breaks the gap_x in conky?

---

### Post by gordintoronto on 2013-03-31
Your message doesn't say what result you want, or what result you are getting. Do you want Conky on both monitors? Is it appearing at all?

---

### Post by Slimmons on 2013-03-31
Sorry about that.  I can't get conky to show at all with both monitors attached.  With one, it does as expected.  With two, I can't get it to show at all.  I have no problems getting conky to work without a .lua file with double monitors, but with the .lua it doesn't work.  Once again, any conky config works with one monitor, and with two monitors I can get any configuration without a .lua to work.  Thanks for helping me state that correctly.

---

### Post by gordintoronto on 2013-04-01
Now that I understand the problem, it's not one I can answer. Sorry about that. I assume you already know the stuff on this page:
[http://crunchbang.org/forums/viewtopic.php?id=17246](http://crunchbang.org/forums/viewtopic.php?id=17246)

---

### Post by stinkeye on 2013-04-01
[COLOR="#FF0000"]Edit[/COLOR]: I ran your config in unity/compiz and it doesn't show unless
I use...```
own_window_type **normal**
```
[ATTACH=CONFIG]240871[/ATTACH]



Never used dual monitors. This is how it works with compiz virtual desktops.
When using **alignment tr** the conky will start at the top right and the gap_x will move it in from the right edge towards the left,
not out past the edge.

Try using...
```
own_window_type **normal**
```

and set it to start at top left and use a gap_x of 1920 and increase the gap to set your screen position..

eg
```
alignment tl
gap_x 1920
```

You also have a typo in your config...
```
own_window_hints [COLOR="#FF0000"]undecorate[/COLOR],sticky,skip_taskbar,skip_pager,below
```
Should be [COLOR="#FF0000"]undecorate**d**[/COLOR]
...and remove the **sticky** option if you only want it on one desktop.

---

### Post by Slimmons on 2013-04-05
And this is why I moved back to Ubuntu.  Thanks guys, the support here in this huge community is amazing.  changing own_window_type  to normal fixed it.  even before I fixed the typo.  Thanks stinkeye, and also gordintoronto for making me be more specific.

---

