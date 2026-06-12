---
title: "Conky problem"
date: 2011-09-14
forum: Desktop Environments
---

### Post by weschilders on 2011-09-14
I am trying to set up a conky config but it keeps on telling me that there is a segmentation fault so can anyone tell me how to fix this? I found the file from a website with a bunch of cool designs and had to translate it from french. I'm really new at linux so can someone help me? Here's the code:

```
# How conky
  total_run_times 0 # Time in seconds, 0 = always on
  background no # conky runs in the background, no = for testing

# System settings
  cpu_avg_samples 1 # Number of samples to calculate the average CPU utilization
  net_avg_samples 2 # # of samples to calculate the average CPU utilization

# Memory
  double_buffer yes # Do not blink
  no_buffers yes # Subtract the buffers of the memory used
  text_buffer_size 1024 # cache size for text

# Display
  out_to_console no # Displays text to standard output
  update_interval 1 # refresh rate of the window (s)

# Conky window
  alignment top_right #
 # ---
  minimum_size 350 # Minimum size (px) width / height
  maximum_width 350 # Maximum width (px)
 # ---
  gap_x -1 # Difference with the left edge / right
  # 60 gap_y gap with the edge up / down
 # ---
  draw_shades no # Show shadows
  draw_outline no # Show the outline of window
  draw_borders no # show contours around blocks of text
  border_width 1 # Width of the outline
  # 1 border_inner_margin width margins
 # ---
  own_window yes # Using its own window
  own_window_type override # Window type, normal / override / desktop
  own_window_transparent yes # Nickname transparency

# Formatting
  # Use Xft use_xft (aliased fonts etc)
  # Use Xft xftalpha .1
  override_utf8_locale yes # Force UTF8
  uppercase no # All text uppercase
  use_spacer right # Adds spaces after certain objects (with fixed fonts)
 # ---
  xftfont saxMono: size = 9 # Default Font
 # ---
  default_bar_size 82 3 # default bar (length height)
  # 3 stippled_borders dots

# Colors
  default_color FFFFFF # Default color
  default_shade_color # 333333 color shade
  default_outline_color black # color contours
 # ---
  color1 # D6D6D6
  # light blue color2 40CEFF
  color3 A3ADB0 # Grey

 # ---
  short_units yes # Units short
  pad_percents # 2 Unit to 2 decimal places

# Support for LUA (CORRECT WITH YOUR PATH!)
  lua_load ~ / .conky / lua / clock.lua
  lua_draw_hook_pre clock_rings

TEXT
$ {Color} $ {0778ec offset 56} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3

$ {Voffset -27} $ {offset 110} $ {font Neuropol: size = 20} $ {time% H:% M} $ {font} $ {font Nimbus Mono L: size = 9} $ uptime
$ {Voffset -5} $ {offset 110} $ {cpubar cpu6 0, 200} $ {voffset 2} $ {color1}
$ {Font Nimbus Mono L: size = 8 style = bold} $ {color2} $ {alignc} $ {exec date +% B \% Y | sed 's / ^. \ | [Az] / \ U & / g' }
$ {Offset 156} $ {color} $ {exec DarkGray DAY = $ (date +% e) cal | sed '1 d '| sed' s / ^ / / g '| sed' s / "$ DAY" ' / $ {color2} '"$ DAY"' $ {color1} / 1 '}

# # Bat
$ {Color} $ {0778ec offset 100} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 150} $ {voffset -10} $ {font Neuropol: size = 20} $ {battery_percent BAT1}% $ {font Nimbus Mono L: size = 8 style = bold} Battery
$ {Offset 160} $ {voffset -5} $ {cpubar cpu6 0, 150} $ {voffset 2} $ {color1}
$ {$ {Offset 160 }..:: acpiacadapter}:: ..
BAT1} $ {battery_time

# # Cpu
$ {Color} $ {0778ec offset 150} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 200} $ {font Neuropol: size = 20}} CPU1 $ {cpu% $ {font Nimbus Mono L: size = 8 style = bold} Cpu
$ {Offset 200} $ {font Neuropol: size = 20} CPU2 $ {cpu}% $ {font Nimbus Mono L: size = 8 style = bold} Cpu
$ {Offset 200} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 200} $ {CpuT execi 20 sensors | grep "105" | cut-d "+"-f2 | cut-c1-4} ° C
$ {Offset 200} $ {CpuT execi 20 sensors | grep "100" | cut-d "+"-f2 | cut-c1-4} ° C

Hdd # #
$ {Color} $ {0778ec offset 100} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 170} $ {font Neuropol: size = 20} $ memperc% $ {font Nimbus Mono L: size = 8 style = bold} Ram
$ {Offset 170} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 170} $ {fs_free HD /} / $ {fs_size /}
$ {Offset 170} $ {THD hddtemp / dev / sda} C

# How conky
  total_run_times 0 # Time in seconds, 0 = always on
  For background no # conky runs in the background, no = for testing

# System settings
  cpu_avg_samples 1 # Number of samples to calculate the average CPU utilization
  net_avg_samples 2 # # of samples to calculate the average CPU utilization

# Memory
  double_buffer yes # Do not blink
  no_buffers yes # Subtract the buffers of the memory used
  text_buffer_size 1024 # cache size for text

# Display
  out_to_console no # Displays text to standard output
  update_interval 1 # refresh rate of the window (s)

# Conky window
  Alignment alignment top_left #
 # ---
  minimum_size 500 # Minimum size (px) width / height
  maximum_width 500 # Maximum width (px)
 # ---
  gap_x -1 # Difference with the left edge / right
  # 270 gap_y gap with the edge up / down
 # ---
  draw_shades no # Show shadows
  draw_outline no # Show the outline of window
  draw_borders no # show contours around blocks of text
  border_width 1 # Width of the outline
  # 1 border_inner_margin width margins
 # ---
  own_window yes # Using its own window
  own_window_type override # Window type, normal / override / desktop
  own_window_transparent yes # Nickname transparency

# Formatting
  yes # Use Xft use_xft (aliased fonts etc)
  # Use Xft xftalpha .1
  override_utf8_locale yes # Force UTF8
  uppercase no # All text uppercase
  use_spacer right # Adds spaces after certain objects (with fixed fonts)
 # ---
  xftfont saxMono: size = 9 # Default Font
 # ---
  default_bar_size 82 3 # default bar (length height)
  Size # 3 stippled_borders dots

# Colors
  default_color FFFFFF # Default color
  default_shade_color # 333333 color shade
  default_outline_color black # color contours
 # ---
  Silver color1 # D6D6D6
  # light blue color2 40CEFF
  color3 A3ADB0 # Grey

 # ---
  short_units yes # Units short
  pad_percents # 2 Unit to 2 decimal places

# Support for LUA (CORRECT WITH YOUR PATH!)
  lua_load ~ / .conky/lua/clock2.lua
  lua_draw_hook_pre clock_rings

TEXT
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.300} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
Net # #
$ {Offset 10} $ {voffset -10} $ {font Neuropol: size = 20} $ {execi conkyEmail 60 - ServerType = POP - servername = pop3.live.com - username =******* * - password =******* - ssl} $ {font Nimbus Mono L: size = 8 style = bold} Msn Email
$ {Offset 20} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 10} $ {color2} $ if_up wlan0 WiFi Online $ else $ endif $ color3 WiFi Offline
$ {Offset 10} $ {color2} $ if_up ppp0 Tim Online $ else $ endif $ color3 Tim Offline $ color3
$ {Offset 15} $ {WiFi wireless_link_qual_perc wlan0}%

# # FRT
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.200} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
$ {Offset 15} $ {Dw if_up ppp0} $ {font Neuropol: size = 20} $ {downspeed ppp0} $ else $ {font Nimbus Mono L: size = 8 style = bold} $ {font Dw Neuropol: size = 20 downspeed wlan0} $ {} $ endif $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 15} $ {if_up ppp0} $ {font Neuropol Up: size = 20} $ {upspeed ppp0} $ else $ {font Nimbus Mono L: size = 8 style = bold} $ {font Neuropol UP: size = 20 upspeed wlan0} $ {} $ endif $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 20} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 15} $ {if_up ppp0} $ {tDown totaldown ppp0} $ else {$ tdw totaldown wlan0} $ endif
# Usb #
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.150} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
$ {Offset 40} USB Device
$ {Offset 15} $ {if_existing / dev/sdc1} $ {exec df-h | grep "sdc" | cut-c52-70} $ {exec df-h | grep "sdc" | cut-c40-44} $ {else} ..: No Device :..${ endif}
$ {Offset 105} $ {if_existing / dev/sdd1} $ {exec df-h | grep "shower" | cut-c52-70} $ {exec df-h | grep "shower" | cut-c40-44} $ {else} $ {endif}
$ {Offset 15} $ {if_existing / dev/sde1} $ {exec df-h | grep "sde" | cut-c52-70} $ {exec df-h | grep "sde" | cut-c40-44} $ {else} $ {endif}
$ {Offset 15} $ {if_existing / dev/sdb1} $ {exec df-h | grep "sdb" | cut-c52-70} $ {exec df-h | grep "sdb" | cut-c40-44} $ {else} $ {endif}
# Music
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.300} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
Exaile if_running $ {} $ {voffset -8} $ {offset 55} $ {voffset -2} $ {font Neuropol: size = 20} $ {exec conkyExaile - datatype = PT} $ {voffset -5} $ {font PizzaDude Bullets: size = 10} $ {offset -65 BBBBB} $ {color} $ {exec 0778ec conkyExaile-n - datatype = RT - ratingchar = D} $ color
$ {Offset 55} $ {$ {} color3 cpubar cpu6 0, 190} $ {voffset 2} $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = TI}}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = AR}}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = AL}}
$ {Else} ..:: Exaile not running:: ..




{$ End}
```

---

### Post by Frogs Hair on 2011-09-14
Hi and welcome

I have a Conky lua configuration the describes this problem . If you are using rings and the start of the rings is not delayed it causes a segmentation fault . below is the text , it might be helpful . 

```
--[[
Clock Rings by Linux Mint (2011) reEdited by despot77

This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/clock_rings.lua
    lua_draw_hook_pre clock_rings
    
Changelog:
+ v1.0 -- Original release (30.09.2009)
   v1.1p -- Jpope edit londonali1010 (05.10.2009)
*v Mint-lua -- reEdit despot77 (18.02.2011)
]]

settings_table = {
    
    {
        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF3300,
        fg_alpha=0.8,
        x=163, y=280,
        radius=25,
        thickness=25,
        start_angle=-90,
        end_angle=180
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF3300,
        fg_alpha=0.8,
        x=163, y=360,
        radius=25,
        thickness=25,
        start_angle=-90,
        end_angle=180
    },
    {
        name='swapperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF3300,
        fg_alpha=0.8,
        x=163, y=440,
        radius=25,
        thickness=25,
        start_angle=-90,
        end_angle=180
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF3300,
        fg_alpha=0.8,
        x=163, y=520,
        radius=25,
        thickness=25,
        start_angle=-90,
        end_angle=180
    },
        {
        name='downspeedf',
        arg='eth0',
        max=210,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF3300,
        fg_alpha=0.8,
        x=165, y=600,
        radius=30,
        thickness=12,
        start_angle=-90,
        end_angle=180
    },
        {
        name='upspeedf',
        arg='eth0',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xff3300,
        fg_alpha=0.8,
        x=165, y=600,
        radius=16,
        thickness=12,
        start_angle=-90,
        end_angle=180
    },
}

-- Use these settings to define the origin and extent of your clock.

clock_r=65

-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.

clock_x=100
clock_y=150

show_seconds=true

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

function draw_clock_hands(cr,xc,yc)
    local secs,mins,hours,secs_arc,mins_arc,hours_arc
    local xh,yh,xm,ym,xs,ys
    
    secs=os.date("%S")    
    mins=os.date("%M")
    hours=os.date("%I")
        
    secs_arc=(2*math.pi/60)*secs
    mins_arc=(2*math.pi/60)*mins+secs_arc/60
    hours_arc=(2*math.pi/12)*hours+mins_arc/12
         
end

function conky_clock_rings()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end
    
    -- Check that Conky has been running for at least 5s

    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
    
    draw_clock_hands(cr,clock_x,clock_y)
end
```

---

### Post by weschilders on 2011-09-14
Ok i adjusted the path in my script to match where i put my lua file... i think i did it right... but it keeps telling me I have a segmentation fault... where exactly does the num_update go? i dont think i have one in the conkyrc script... i dont have a clue what i am doing... but could someone explain a little more cause Im trying pretty hard here to figure this out... here is my new code...

```
# How conky
  total_run_times 0 # Time in seconds, 0 = always on
  background no # conky runs in the background, no = for testing

# System settings
  cpu_avg_samples 1 # Number of samples to calculate the average CPU utilization
  net_avg_samples 2 # # of samples to calculate the average CPU utilization

# Memory
  double_buffer yes # Do not blink
  no_buffers yes # Subtract the buffers of the memory used
  text_buffer_size 1024 # cache size for text

# Display
  out_to_console no # Displays text to standard output
  update_interval 1 # refresh rate of the window (s)

# Conky window
  alignment top_right #
 # ---
  minimum_size 350 # Minimum size (px) width / height
  maximum_width 350 # Maximum width (px)
 # ---
  gap_x -1 # Difference with the left edge / right
  # 60 gap_y gap with the edge up / down
 # ---
  draw_shades no # Show shadows
  draw_outline no # Show the outline of window
  draw_borders no # show contours around blocks of text
  border_width 1 # Width of the outline
  # 1 border_inner_margin width margins
 # ---
  own_window yes # Using its own window
  own_window_type override # Window type, normal / override / desktop
  own_window_transparent yes # Nickname transparency

# Formatting
  # Use Xft use_xft (aliased fonts etc)
  # Use Xft xftalpha .1
  override_utf8_locale yes # Force UTF8
  uppercase no # All text uppercase
  use_spacer right # Adds spaces after certain objects (with fixed fonts)
 # ---
  xftfont saxMono: size = 9 # Default Font
 # ---
  default_bar_size 82 3 # default bar (length height)
  # 3 stippled_borders dots

# Colors
  default_color FFFFFF # Default color
  default_shade_color # 333333 color shade
  default_outline_color black # color contours
 # ---
  color1 # D6D6D6
  # light blue color2 40CEFF
  color3 A3ADB0 # Grey

 # ---
  short_units yes # Units short
  pad_percents # 2 Unit to 2 decimal places

# Support for LUA (CORRECT WITH YOUR PATH!)
  lua_load ~/scripts/rings.lua
  lua_draw_hook_pre clock_rings

TEXT
$ {Color} $ {0778ec offset 56} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3

$ {Voffset -27} $ {offset 110} $ {font Neuropol: size = 20} $ {time% H:% M} $ {font} $ {font Nimbus Mono L: size = 9} $ uptime
$ {Voffset -5} $ {offset 110} $ {cpubar cpu6 0, 200} $ {voffset 2} $ {color1}
$ {Font Nimbus Mono L: size = 8 style = bold} $ {color2} $ {alignc} $ {exec date +% B \% Y | sed 's / ^. \ | [Az] / \ U & / g' }
$ {Offset 156} $ {color} $ {exec DarkGray DAY = $ (date +% e) cal | sed '1 d '| sed' s / ^ / / g '| sed' s / "$ DAY" ' / $ {color2} '"$ DAY"' $ {color1} / 1 '}

# # Bat
$ {Color} $ {0778ec offset 100} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 150} $ {voffset -10} $ {font Neuropol: size = 20} $ {battery_percent BAT1}% $ {font Nimbus Mono L: size = 8 style = bold} Battery
$ {Offset 160} $ {voffset -5} $ {cpubar cpu6 0, 150} $ {voffset 2} $ {color1}
$ {$ {Offset 160 }..:: acpiacadapter}:: ..
BAT1} $ {battery_time

# # Cpu
$ {Color} $ {0778ec offset 150} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 200} $ {font Neuropol: size = 20}} CPU1 $ {cpu% $ {font Nimbus Mono L: size = 8 style = bold} Cpu
$ {Offset 200} $ {font Neuropol: size = 20} CPU2 $ {cpu}% $ {font Nimbus Mono L: size = 8 style = bold} Cpu
$ {Offset 200} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 200} $ {CpuT execi 20 sensors | grep "105" | cut-d "+"-f2 | cut-c1-4} ° C
$ {Offset 200} $ {CpuT execi 20 sensors | grep "100" | cut-d "+"-f2 | cut-c1-4} ° C

Hdd # #
$ {Color} $ {0778ec offset 100} $ {voffset 3} $ {cpugraph cpu6 17.1} $ {voffset -3} $ {hr 2} $} {color3
$ {Offset 170} $ {font Neuropol: size = 20} $ memperc% $ {font Nimbus Mono L: size = 8 style = bold} Ram
$ {Offset 170} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 170} $ {fs_free HD /} / $ {fs_size /}
$ {Offset 170} $ {THD hddtemp / dev / sda} C

# How conky
  total_run_times 0 # Time in seconds, 0 = always on
  For background no # conky runs in the background, no = for testing

# System settings
  cpu_avg_samples 1 # Number of samples to calculate the average CPU utilization
  net_avg_samples 2 # # of samples to calculate the average CPU utilization

# Memory
  double_buffer yes # Do not blink
  no_buffers yes # Subtract the buffers of the memory used
  text_buffer_size 1024 # cache size for text

# Display
  out_to_console no # Displays text to standard output
  update_interval 1 # refresh rate of the window (s)

# Conky window
  Alignment alignment top_left #
 # ---
  minimum_size 500 # Minimum size (px) width / height
  maximum_width 500 # Maximum width (px)
 # ---
  gap_x -1 # Difference with the left edge / right
  # 270 gap_y gap with the edge up / down
 # ---
  draw_shades no # Show shadows
  draw_outline no # Show the outline of window
  draw_borders no # show contours around blocks of text
  border_width 1 # Width of the outline
  # 1 border_inner_margin width margins
 # ---
  own_window yes # Using its own window
  own_window_type override # Window type, normal / override / desktop
  own_window_transparent yes # Nickname transparency

# Formatting
  yes # Use Xft use_xft (aliased fonts etc)
  # Use Xft xftalpha .1
  override_utf8_locale yes # Force UTF8
  uppercase no # All text uppercase
  use_spacer right # Adds spaces after certain objects (with fixed fonts)
 # ---
  xftfont saxMono: size = 9 # Default Font
 # ---
  default_bar_size 82 3 # default bar (length height)
  Size # 3 stippled_borders dots

# Colors
  default_color FFFFFF # Default color
  default_shade_color # 333333 color shade
  default_outline_color black # color contours
 # ---
  Silver color1 # D6D6D6
  # light blue color2 40CEFF
  color3 A3ADB0 # Grey

 # ---
  short_units yes # Units short
  pad_percents # 2 Unit to 2 decimal places

# Support for LUA (CORRECT WITH YOUR PATH!)
  lua_load ~/scripts/rings.lua
  lua_draw_hook_pre clock_rings

TEXT
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.300} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
Net # #
$ {Offset 10} $ {voffset -10} $ {font Neuropol: size = 20} $ {execi conkyEmail 60 - ServerType = POP - servername = pop3.live.com - username =******* * - password =******* - ssl} $ {font Nimbus Mono L: size = 8 style = bold} Msn Email
$ {Offset 20} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 10} $ {color2} $ if_up wlan0 WiFi Online $ else $ endif $ color3 WiFi Offline
$ {Offset 10} $ {color2} $ if_up ppp0 Tim Online $ else $ endif $ color3 Tim Offline $ color3
$ {Offset 15} $ {WiFi wireless_link_qual_perc wlan0}%

# # FRT
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.200} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
$ {Offset 15} $ {Dw if_up ppp0} $ {font Neuropol: size = 20} $ {downspeed ppp0} $ else $ {font Nimbus Mono L: size = 8 style = bold} $ {font Dw Neuropol: size = 20 downspeed wlan0} $ {} $ endif $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 15} $ {if_up ppp0} $ {font Neuropol Up: size = 20} $ {upspeed ppp0} $ else $ {font Nimbus Mono L: size = 8 style = bold} $ {font Neuropol UP: size = 20 upspeed wlan0} $ {} $ endif $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 20} $ {voffset -5} $ {cpubar cpu6 0, 110} $ {voffset 2} $ {color1}
$ {Offset 15} $ {if_up ppp0} $ {tDown totaldown ppp0} $ else {$ tdw totaldown wlan0} $ endif
# Usb #
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.150} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
$ {Offset 40} USB Device
$ {Offset 15} $ {if_existing / dev/sdc1} $ {exec df-h | grep "sdc" | cut-c52-70} $ {exec df-h | grep "sdc" | cut-c40-44} $ {else} ..: No Device :..${ endif}
$ {Offset 105} $ {if_existing / dev/sdd1} $ {exec df-h | grep "shower" | cut-c52-70} $ {exec df-h | grep "shower" | cut-c40-44} $ {else} $ {endif}
$ {Offset 15} $ {if_existing / dev/sde1} $ {exec df-h | grep "sde" | cut-c52-70} $ {exec df-h | grep "sde" | cut-c40-44} $ {else} $ {endif}
$ {Offset 15} $ {if_existing / dev/sdb1} $ {exec df-h | grep "sdb" | cut-c52-70} $ {exec df-h | grep "sdb" | cut-c40-44} $ {else} $ {endif}
# Music
$ {Color} $ {voffset 0778ec 3} $ {cpugraph cpu6 1.300} $ {voffset 1} $ {cpugraph cpu6 17.1} $} {color3
Exaile if_running $ {} $ {voffset -8} $ {offset 55} $ {voffset -2} $ {font Neuropol: size = 20} $ {exec conkyExaile - datatype = PT} $ {voffset -5} $ {font PizzaDude Bullets: size = 10} $ {offset -65 BBBBB} $ {color} $ {exec 0778ec conkyExaile-n - datatype = RT - ratingchar = D} $ color
$ {Offset 55} $ {$ {} color3 cpubar cpu6 0, 190} $ {voffset 2} $ {font Nimbus Mono L: size = 8 style = bold}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = TI}}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = AR}}
$ {Offset 55} $ {exec {scroll conkyExaile $ 36 - datatype = AL}}
$ {Else} ..:: Exaile not running:: ..




{$ End}
```

what all should i change and how should i change it? I know it is a pretty big request but it would be greatly appreciated... i attached a picture of what it is supposed to look like if it helps...

---

### Post by ManualSparrow on 2011-09-17
Starting in the first line you are trying to monitor CPU6. I doubt you have 6 CPUs (you probably have 2 or 4). Change everything that mentions cpu6 to cpu0. 

You are also probably missing some fonts and the conky email checker script your config file is referencing.

I would recommend trying a simpler script and adding features as you start to understand the syntax better. 

[http://ubuntuforums.org/showthread.php?t=1752912&page=2](http://ubuntuforums.org/showthread.php?t=1752912&page=2)

Read through this and you should get a pretty good idea of how to get everything running.

---

