---
title: "Conky, LUA issue..."
date: 2009-11-01
forum: Desktop Environments
---

### Post by vkcaspervk on 2009-11-01
I am trying to make my own script in lua that will convert degrees Celsius to degrees Fahrenheit. The Info is pulled from hwmon. These are my scripts so far...

conkyrc
```

lua_load ~/.conky/armadillo/armadillo.lua

alignment top_right
background yes
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
double_buffer yes
draw_outline no 
draw_borders no 
draw_graph_borders yes 
stippled_borders 0
border_margin 0 
border_width 0
double_buffer yes

cpu_avg_samples 2
out_to_console no
out_to_stderr no
update_interval 5.0


TEXT
${color orange}Computer Info ${hr}
${color grey}$nodename - $sysname
${color grey}Ubuntu 9.10 $kernel
Conky Version $version
${color orange}System ${hr}
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}CPU:$color ${hwmon 0 temp 2}°C ${color grey}CPU Fan:$color ${hwmon 0 fan 1}
${color grey}Fans:
${color lightgrey}  Case 1:$color ${hwmon 0 fan 2} rpm
${color lightgrey}  Case 2:$color ${hwmon 0 fan 3} rpm
${color grey}Case Temp:$color ${hwmon 0 temp 2}°C

$hr
**${color grey}Case Temp:$color ${lua_parse get_fahrenheit ${hwmon 0 temp 2}****}°F**
$hr
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color grey}Users Logged in:$color $user_number
$hr
${color grey}File systems:
 ${color lightgrey}/ $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
 ${color lightgrey}/home $color${fs_used /home}/${fs_size /home} ${fs_bar 6 /home}
$hr
${color grey}Networking:
${color lightgrey}Inbound: $color${downspeed eth1} per second
#${downspeedgraph eth1 30,200 0000ff ff0000 .01}
${color lightgrey}Outbound: $color${upspeed eth1} per second
#${upspeedgraph eth1 30,200 0000ff ff0000 .01}
$hr
${color blue}Services:
${color lightgrey}SSH Clients: $color${tcp_portmon 22 22 count}
${color lightgrey}WWW Clients: $color${tcp_portmon 80 80 count}
$hr
${color grey}nVidia Video Card:
${color lightgrey}Freq: $color${nvidia gpufreq} Mhz
${color lightgrey}Ambient Temp: $color${nvidia ambient} 
${color lightgrey}Core Temp: $color${nvidia temp} 
${color lightgrey}Max Temp: $color${nvidia threshold} 
Process Info ${hr 2}
${color grey}Name              PID   CPU%   MEM%
${color orange} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color lightgrey} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
${color lightgrey} ${top name 6} ${top pid 6} ${top cpu 6} ${top mem 6}
${color lightgrey} ${top name 7} ${top pid 7} ${top cpu 7} ${top mem 7}
${color lightgrey} ${top name 8} ${top pid 8} ${top cpu 8} ${top mem 8}
${color lightgrey} ${top name 9} ${top pid 9} ${top cpu 9} ${top mem 9}
${color lightgrey} ${top name 10} ${top pid 10} ${top cpu 10} ${top mem 10}

```The LUA
```

function conky_get_fahrenheit(x)
    print("lua function conky_get_farrenheit x=" .. x)
    print("lua function conky_get_fahrenheit(" .. x .. ") returned: " .. string.format('%0.0f', 1.8 * x + 32))
        return string.format('%0.0f', 1.8 * x + 32)
end

```As you can see I'm trying to pass a result from one to the next, I have seen it done in other scripts exactly the same way, even on the ConkyWiki... Tho the arg being passed to get_farrenheit is "${hwmon" Conky is not parsing the variable...

Console output...
> lua function conky_get_farrenheit x=${hwmon
Conky: llua_do_call: function conky_get_fahrenheit execution failed: /home/casper/.conky/armadillo/armadillo.lua:6: attempt to perform arithmetic on local 'x' (a string value)
Now I know the LUA works because if I replace the ${hwmon 0 temp 2} with a number is returns fine... 

There is a script on the wiki that uses the same principle,
[http://wiki.conky.be/index.php/Conky_and_Lua](http://wiki.conky.be/index.php/Conky_and_Lua)
**${lua_read_parse top_mem_colour  ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}}**
I have tried this script and it gives me the same type of errors. 

Ubuntu 9.10 Just upgraded to new version
Conky is up to date full install.
Even install LUA 5.1

Its prolly something simple im missing. It has to be... I just cant figure out why its passing ${hwmon as a arg and not converting it to the result first as in all the other scripts.

Any Idea's? Cause I think my brain is beginning to leaking out of my left ear... And my fingers hurt from googling...

---

### Post by vkcaspervk on 2009-11-03
Bump, Anyone?

---

