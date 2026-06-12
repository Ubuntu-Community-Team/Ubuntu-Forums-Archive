---
title: "Problem with Conky and upspeedgraph/downspeedgraph"
date: 2021-06-02
forum: Desktop Environments
---

### Post by francky37 on 2021-06-02
Hi all!

I have a problem with new versions of conky since 1.11.
The problem is with upspeedgraph and downspeedgraph which do not show the history of values on graphs while it works very well with version 1.10. I tried on Xubuntu and openSUSE (with XFCE) but I get the same thing.
Identical behavior with Execgraph. The problem seems connected to templates.
If someone know the solution I thank him in advance.

```
conky.config = {
-- ********************************
-- "Network Panel" for Conky by FG
-- ********************************

      background = true,
    
    own_window = true,
    own_window_class = 'Conky',
    own_window_transparent = true,
    own_window_type = 'normal',
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    own_window_argb_visual = true,
    own_window_argb_value = 0,
    own_window_colour = '#000000',

    double_buffer = true,
    no_buffers = false,
    use_spacer = 'none',
    use_xft = true,
    xftalpha = 1,
    
    font = 'Ubuntu:size=10',
    update_interval = 2,
    uppercase = false,
    override_utf8_locale = true,
    stippled_borders = 0,
    border_width = 5,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    
    show_graph_scale = false,
    show_graph_range = false,
    
    net_avg_samples = 2,
    cpu_avg_samples = 6,
    short_units = true,
    pad_percents = 2,
    text_buffer_size = 2048,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,

    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,

    minimum_width = 200, minimum_height = 0,
    default_graph_width = 200, default_graph_height = 50,


    template1 = [[
${if_up \1}${font Ubuntu:Italic:size=10}Wireless lan (\1) ${hr}\n${font FontAwesome}&#61931;${font} AP ${alignr} ${wireless_essid}\n${font FontAwesome}&#62158; ${font} ${alignr} ${wireless_link_bar 10,150 \1}\n${font FontAwesome}&#61671;${font} bitrate ${alignr} ${wireless_bitrate \1} ${endif}]],

    template2 = [[
${if_up \1}${font Ubuntu:Italic:size=10}Wired lan (\1) ${hr} ${endif}]],

    template3 = [[
${font FontAwesome}&#61505;${font} ${alignr}${addr \1}]],

    template4 = [[
${font FontAwesome}&#61677;${font}${alignr}${downspeedf \1 }KiB/s (${totaldown \1})\n${downspeedgraph \1} \n${font FontAwesome}&#61678;${font}${alignr}${upspeedf \1}KiB/s (${totalup \1})\n${upspeedgraph \1} ]],

};

conky.text = [[
${if_gw}
${if_match "${gw_iface}"=="multiple"}\
Multiple (showing ${execpi 10 sed -n "2p" /proc/net/route | sed 's/\t.*//'}) ${hr}
${else}\
${if_match "${wireless_mode}" != "" }\
${execpi 10000 cat /proc/net/route | sed -n '2p' | sed 's/\t.*//' | sed 's/^/\$\{template1 /;s/$/\}/'}
${else}\
${execpi 10000 cat /proc/net/route | sed -n '2p' | sed 's/\t.*//' | sed 's/^/\$\{template2 /;s/$/\}/'}
${endif}\
${endif}\
${font FontAwesome}&#61612;${font} ${alignr}${execi 6000 wget http://ipinfo.io/ip -qO -}
${execpi 5 sed -n "2p" /proc/net/route | sed 's/\t.*//' | sed 's/^/\$\{template3 /;s/$/\}/'}
${voffset -5}${hr}
${execpi 5 sed -n "2p" /proc/net/route | sed 's/\t.*//' | sed 's/^/\$\{template4 /;s/$/\}/'}
${voffset -9}
${else}$hr
No network found !!!
$hr
${endif}
]];


```

---

