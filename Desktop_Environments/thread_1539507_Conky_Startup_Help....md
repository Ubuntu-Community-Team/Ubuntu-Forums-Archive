---
title: "Conky Startup Help..."
date: 2010-07-26
forum: Desktop Environments
---

### Post by KdotJ on 2010-07-26
Hey people, 
I'm new to using conky, I only found out about it yesterday lol. 
Anyways, I have a script that a put together from bits and bobs of others I've seen around. When I start it via the terminal it all works fine. However, when I add /usr/bin/conky to my startup applications, I get a problem.

Conky loads up on log in, but it's inside it's own window, which appears to be raised off the desktop. And other windows (for example, nautilus) go underneath this conky window.

I am using compiz, 
Can anyone help me out?

Much appreciated

---

### Post by cllewis91592 on 2010-07-26
hey im new to conky too i was having some problems too. if you could share your code that you used i would like to see how other people use it.  thanks ;)

---

### Post by KdotJ on 2010-07-26
sure, here is my conky script:

> 
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
#border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 30
gap_y 30

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 250}${color slate grey}Date: ${alignr}${color }${time %e %B %G}
${offset 250}${color slate grey}Time: ${alignr}${color }${time %H:%M}
${offset 250}${color slate grey}UpTime: ${alignr}${color }$uptime
${offset 250}${color slate grey}Core 1:${alignr}${color } ${cpu cpu1}%
${offset 250}${color slate grey}Core 2:${alignr}${color } ${cpu cpu2}% 
${offset 250}${color slate grey}Core Temp:${alignr}${color } ${acpitemp}C
${offset 250}${cpugraph 20,130 000000 ffffff}
${offset 250}${color slate grey}Processes:${alignr}${color }$processes  
${offset 250}${color slate grey}Running:${alignr}${color }$running_processes

${offset 250}${color slate grey}Highest CPU:
${offset 250}${color #ddaa00} ${top name 1}${alignr}${top_mem cpu 1}
${offset 250}${color lightgrey} ${top name 2}${alignr}${top cpu 2}
${offset 250}${color lightgrey} ${top name 3}${alignr}${top cpu 3}
${offset 250}${color lightgrey} ${top name 4}${alignr}${top cpu 4}

${offset 250}${color slate grey}Highest MEMORY:
${offset 250}${color #ddaa00} ${top_mem name 1}${alignr}${top_mem mem 1}
${offset 250}${color lightgrey} ${top_mem name 2}${alignr}${top_mem mem 2}
${offset 250}${color lightgrey} ${top_mem name 3}${alignr}${top_mem mem 3}
${offset 250}${color lightgrey} ${top_mem name 4}${alignr}${top_mem mem 4}

${offset 250}${color slate grey}MEMORY:${alignr}${color }$memperc%
${offset 250}${membar 3,130}

${offset 250}${color slate grey}DISK:${alignr}${color }${fs_free /} free
${offset 250}${fs_bar 3,130 /}

${offset 250}${color slate grey}NET: 
${offset 250}${color}Down:${alignr}${color }${downspeed wlan0}k/s${color}
${offset 250}${downspeedgraph wlan0 20,130 000000 ffffff}

---

### Post by davec64 on 2010-07-26
I think the bit you need to change is:

```
own_window_type override
```

to:
```
own_window_type normal
```

I would also use:

```
own_window_transparent yes
```

To see what all the options are, have a look here:
[http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

:)

---

### Post by KdotJ on 2010-07-26
> **davec64 said:**
> I think the bit you need to change is:

```
own_window_type override
```

to:
```
own_window_type normal
```

I would also use:

```
own_window_transparent yes
```

To see what all the options are, have a look here:
[http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

:)

Thanks for the reply, I have however already tried changing override to normal, still getting the same problem. I also already have "transparent yes" in there. I will have a good look at the link you gave me, thanks again

---

### Post by Sub101 on 2010-07-26
You need to delay the startup of conky. I use a simple script;

```
#!/bin/bash

sleep 20
conky


```

Add that script to startup applications rather than conky itself.

---

### Post by KdotJ on 2010-07-26
> **Sub101 said:**
> You need to delay the startup of conky. I use a simple script;

```
#!/bin/bash

sleep 20
conky


```

Add that script to startup applications rather than conky itself.

Thanks, I did just that and now it runs at start up properly. However, now I have a new problem (as is always the case haha). Now the display flickers every 10 seconds or so, even though I have double buffer on.... any ideas?

---

### Post by stinkeye on 2010-07-27
Because you have only set a minimum size for your conky window, the flickering is conky resizing as the lenght of some output changes.
You need to set a max width```
minimum_size 200 5
maximum_width 200
```

Also, why do you have ${offset 250} before every single line?

To get your temperature reading to work you need to install lm-sensors
[**_[COLOR="DarkRed"]http://conky.linux-hardcore.com/beginners/programs/using-sensors/[/COLOR]_**]("http://conky.linux-hardcore.com/beginners/programs/using-sensors/")



Try this with a few of my amendments 
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Terminus:size=8
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 5
maximum_width 200

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
#border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 30
gap_y 30

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes

TEXT

${color slate grey}Date: ${alignr}${color }${time %e %B %G}
${color slate grey}Time: ${alignr}${color }${time %H:%M}
${color slate grey}UpTime: ${alignr}${color }$uptime
${color slate grey}Core 1:${alignr}${color } ${cpu cpu1}%
${color slate grey}Core 2:${alignr}${color } ${cpu cpu2}%
${color slate grey}Core Temp:${alignr}${color } ${acpitemp}C
${cpugraph 20,200 000000 ffffff}
${color slate grey}Processes:${alignr}${color }$processes 
${color slate grey}Running:${alignr}${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${alignr}${top_mem cpu 1}
${color lightgrey} ${top name 2}${alignr}${top cpu 2}
${color lightgrey} ${top name 3}${alignr}${top cpu 3}
${color lightgrey} ${top name 4}${alignr}${top cpu 4}

${color slate grey}Highest MEMORY:
${color #ddaa00} ${top_mem name 1}${alignr}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${alignr}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${alignr}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${alignr}${top_mem mem 4}

${color slate grey}MEMORY:${alignr}${color }$memperc%
${membar 3,200}

${color slate grey}DISK:${alignr}${color }${fs_free /} free
${fs_bar 3,200 /}

${color slate grey}NET: 
${color}Down:${alignr}${color }${downspeed wlan0}k/s${color}
${downspeedgraph wlan0 20,200 000000 ffffff}
```


[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")


Also, as your using compiz you can use this script for startup which won't start conky
until compiz has loaded.
**[SIZE="4"]You need to enable the Dbus plugin in ccsm > utility.[/SIZE]**


Save as startconky (or whatever you like), make it executable
and link to it in startup applications.
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c [COLOR="Magenta"]~/conky/democonky[/COLOR] >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```

[COLOR="#ff00ff"]**Change to the path for your conky config.**[/COLOR]
The benefit of this script is you don't have to guess at the delay and gets conky up and running as soon as possible.

---

### Post by KdotJ on 2010-07-27
> **stinkeye said:**
> 
Also, why do you have ${offset 250} before every single line?


Lol, this is due to me copying other scripts I have seen here on the forum. Did think this was a bit strange but meh, so thanks for the heads up.

> **stinkeye said:**
> 
To get your temperature reading to work you need to install lm-sensors


Thanks, it seems I already have this and my temperature works good

> **stinkeye said:**
> 
Also, as your using compiz you can use this script for startup which won't start conky
until compiz has loaded.
**[SIZE="4"]You need to enable the Dbus plugin in ccsm > utility.[/SIZE]**


Save as startconky (or whatever you like), make it executable
and link to it in startup applications.
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c [COLOR="Magenta"]~/conky/democonky[/COLOR] >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```

[COLOR="#ff00ff"]**Change to the path for your conky config.**[/COLOR]
The benefit of this script is you don't have to guess at the delay and gets conky up and running as soon as possible.

Thats great! thanks for the start up script and for the amended conkyrc script. I'll give them all a try once I get home to my box. And thanks for the link to the how-to thread, much appreciated. 

Thanks all for the input

---

### Post by tabernash on 2010-08-01
I hope this thread isn't dead yet.

I am a recent convert to Ubuntu. I have to say it's quite nice and, for me, user friendly. Conky is set up and works exactly like it should. However, I am having a SMALL issue with the delay for Conky. I have tried various scripts and none seem to work. I believe that my major issue is directing the script (I would prefer to use the delay script for '.startconky' above)to the correct location. Currently I am trying to use this:

---------------------------------------------------------------------------------------------------


#! /bin/bash
until [ "$done" = "true" ]
do
    if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
    then
        DISPLAY=:0.0 conky -c ~/home/lappy/conkyrc >/dev/null 2>&1 &
                
                
        done="true";
    else
        echo "CONKY IS WAITING"
        done="false"
        sleep 5;
    fi
done
exit 0

---------------------------------------------------------------------------------------------------


Notice that my conkycr file is in my home directory. My conky file is in my /usr/bin/conky. Like I said, Conky works fine if I launch it manually, but I have heard that if you are going to run something more than once, you should write a script. ;-) I have added my .startconky to startup and the file is executable.

It's probably very simple that I am missing, as my 'Ubuntu-Fu' is weak. I admit to being a n00b at it.

In the meantime, here is my Conky config for anyone that would like to use it. I would recommend changing the line about the CPU being an AMD XP-M.

---------------------------------------------------------------------------------------------------


# UBUNTU-CONKY !THIS IS THE RIGHT ONE TO USE!
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
# 
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 2.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT

 
${color orange}CPU ${hr 2}$color
AMD Athlon XP-M XP2500+ 1.86Ghz
${freq}MHz   Load: ${loadavg}   Temp: $acpitemp C
$cpubar
${cpugraph ff0000 0000ff}
${color #ddaa00}$stippled_hr
${color orange}${font DejaVu Sans:bold:size=9}${exec whoami}@$nodename${font} ${hr 2}$color
Ubuntu Linux 10.04 LTS
Kernel: $kernel
Uptime: $uptime
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}
${color #989898}Power: ${color }${battery BAT1} $alignr ${battery_time BAT1}          
${color #ddaa00}$stippled_hr 
${color orange}MEMORY / DISK ${hr 2}$color
RAM: $mem / $memmax  $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
${color #ddaa00}$stippled_hr
${color orange}WIRED NETWORK: (${addr eth0}) ${hr 2}$color
Down:${color #8844ee} ${downspeed eth0} k/s ${offset 70}Up:${color #22ccff} ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 ff0000 0000ff} ${alignr} ${upspeedgraph eth0 25,140 0000ff ff0000}$color

${color orange}WIRED NETWORK INFO: ${hr 2}$color
$alignc${color #ddaa00}  Up${color}/${color #ddaa00}Total: ${color }${upspeedf eth0} kb/s    ${totalup eth0}
$alignc${color #ddaa00}Down${color}/${color #ddaa00}Total: ${color }${downspeedf eth0} kb/s    ${totaldown eth0}
     ${color #989898}LAN IP: ${color} ${addr eth0}   |   ${color #989898}Public IP: ${color }${execi 7200 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
${color #ddaa00}$stippled_hr 
${color orange}WIRELESS NETWORK: (${addr wlan0}) ${hr 2}$color
Down:${color #8844ee} ${downspeed wlan0} k/s ${offset 70}Up:${color #22ccff} ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 ff0000 0000ff} ${alignr} ${upspeedgraph wlan0 25,140 0000ff ff0000}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}WIRELESS NETWORK INFO: ${hr 2}$color
$alignc${color #ddaa00}  Up${color}/${color #ddaa00}Total: ${color }${upspeedf wlan0} kb/s    ${totalup wlan0}
$alignc${color #ddaa00}Down${color}/${color #ddaa00}Total: ${color }${downspeedf wlan0} kb/s    ${totaldown wlan0}
${color #989898}Wireless Strength: ${color}  ${wireless_link_bar 5,100 wlan0}   ${wireless_link_qual wlan0}%
${color #989898}Wireless SSID/Bitrate: ${color} $alignc${wireless_essid wlan0}    ${wireless_bitrate wlan0}
${color #989898}Wireless Mode: ${wireless_mode wlan0}
         ${color #989898}LAN IP: ${color} ${addr wlan0}   |   ${color #989898}Public IP: ${color }${execi 7200 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
${color #ddaa00}$stippled_hr 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
${color #BCBCBC}TEMPERATURE: ${color } $acpitemp C
${color #BCBCBC}BATTERY: ${color } ${battery BAT1}
${color #BCBCBC}AC ADAPTER: ${color } $acpiacadapter 

-----------------------------------------------------------------------------------------------------


Thanks for any help!

---

### Post by stinkeye on 2010-08-01
> conky -c ~/home/lappy/conkyrc 

The path to your conky config should be ~/conkyrc
which is the same as /home/lappy/conkyrc

The tilde character "~" is short for /home/your_username
In your case /home/lappy

So the path you've set for your conky is **/home/lappy/home/lappy/conkyrc**



To check that you have the right path to your conky in the script run in the terminal
```
conky -c ~/conkyrc
```

All this script is doing is delaying the start of conky until compiz has loaded.
Conky can sometimes not display properly when started too early.

[COLOR="Red"]**Edit**[/COLOR] I changed the path,sorry,made a mistake.

---

### Post by tabernash on 2010-08-01
Thanks for the quick reply!

I figured it was something stupid. I have made the change and am going to reboot now.

I'll let you know as soon as I get back up.

*crosses fingers

;-)

---

### Post by tabernash on 2010-08-01
Well, no love there. :(

Here is my new .startconky file:

------------------------------------------------------------------------------------------------

#! /bin/bash
until [ "$done" = "true" ]
do
    if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
    then
        DISPLAY=:0.0 conky -c ~/lappy/conkyrc >/dev/null 2>&1 &
                
                
        done="true";
    else
        echo "CONKY IS WAITING"
        done="false"
        sleep 5;
    fi
done
exit 0

------------------------------------------------------------------------------------

Under properties, it shows as a script file - so it is set as executable. I have been trying to get this delay to work since yesterday and it is driving me mad. I really appreciate any help you can give. Like I said, the Conky part works perfectly. I can launch it from either the terminal or by using a launcher. It's this delay that is killing me.

I have my Compiz set as you suggested up thread.

Any other ideas? I have tried a simple bash:

------------------------------------------------------------------------------------

[COLOR=black][COLOR=#C05600][/COLOR][/COLOR]#!/bin/bash
sleep 20 && conky;


------------------------------------------------------------


Something a bit more elaborate


----------------------------------------------------------------------------------

[COLOR=#666666]*#!/bin/sh*[/COLOR]
[COLOR=#666666]*#start Conky with a 20 second delay*[/COLOR]
[COLOR=Black][COLOR=#C20CB9]**sleep**[/COLOR] [COLOR=#000000]20[/COLOR][/COLOR]
[COLOR=Black]conky [COLOR=#660033]-c[/COLOR] ~[COLOR=#000000]**/**[/COLOR]lappy[COLOR=#000000]**/**[/COLOR].conkyrc[COLOR=#666666]**[/COLOR]
[COLOR=#7A0874]**exit**[/COLOR][/COLOR]----------------------------------------------------------------------------------


I have tried longer and shorter sleep times too. I am at my wit's end. Now it is a mission that I MUST complete! You know how stuff like that goes. ;-)



Again, I appreciate your help.
[COLOR=#C05600][/COLOR]
[COLOR=#C05600]
[/COLOR]

---

### Post by stinkeye on 2010-08-01
See my edit I had the path wrong.
remember to put the exact path.
If your conky is saved as .conkyrc you have to include the dot.
A preceeding dot means the file will be hidden. Ctrl+h to see hidden files in your file browser.

If you open your file browser to your conky file and right click and copy 
you can paste the path into a text editor.

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> See my edit I had the path wrong.
remember to put the exact path.
If your conky is saved as .conkyrc you have to include the dot.

If you open your file browser to your conky file and right click and copy 
you can paste the path into a text editor.


Right now I have this (I did have to add the dot):

DISPLAY=:0.0 conky -c ~/.conkyrc >/dev/null 2>&1 &

File browser gives this: /home/lappy/.conkyrc as a location.

I have changes the .startconky file to that and am restarting.

I'll be back in a sec.

AGAIN, I really appreciate your help here.

Good on ya mate!

---

### Post by stinkeye on 2010-08-01
Some info while I'm waiting.
When you type  conky into the terminal it will look for a config file at ~/.conkyrc

If there is no ~/.conkyrc file it will load a default config that comes with it from /etc/conky/conky.conf

So if your config is saved as .conkyrc (rememeber the dot) you do not need
to use the path.
The -c flag tells conky to load a particular config.

So if you save your config as .conkyrc in your home folder you need only run it with the command **conky**.


eg your .startconky file would be this
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 [COLOR="Magenta"]conky[/COLOR] >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```

---

### Post by tabernash on 2010-08-01
Still no love. :(

Maybe I am just supposed to launch Conky by hand. Maybe my lappy is too cool to run scripts! ;-) I mean, everything else is running fine. It's just this one LITTLE thing.

I really do appreciate your help here.

Any other ideas?

---

### Post by stinkeye on 2010-08-01
Open a terminal and enter conky.
Does your conky show?

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> Open a terminal and enter conky.
Does your conky show?


Yes, with a few arguments. (IP redacted). Conky ALSO loads fine when I use the launcher.

lappy@lappy-laptop:~$ conky
Conky: /home/lappy/.conkyrc: 49: no such configuration: 'border_margin'
Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (24000a9) is subwindow of root window (11a)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
--2010-08-01 21:49:35--  [http://whatismyip.org/](http://whatismyip.org/)
Resolving whatismyip.org... xxx.xxx.xxx.xxx
Connecting to whatismyip.org|xxx.xxx.xxx.xxx|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `STDOUT'

    [ <=>                                   ] 14          --.-K/s   in 0.004s  

2010-08-01 21:49:38 (3.47 KB/s) - written to stdout [14]

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
--2010-08-01 21:49:44--  [http://whatismyip.org/](http://whatismyip.org/)
Resolving whatismyip.org... xxx.xxx.xxx.xxx
Connecting to whatismyip.org|xxx.xxx.xxx|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `STDOUT'

    [ <=>                                   ] 14          --.-K/s   in 0s      

2010-08-01 21:49:44 (462 KB/s) - written to stdout [14]

sh: fortune: not found
Conky: can't open /sys/class/power_supply/AC/uevent: No such file or directory
Conky: statfs '/media/sda1': No such file or directory

---

### Post by stinkeye on 2010-08-01
Okay now save the above script (in post 16) as .startconky in your home folder.
Right click on the file    properties > permissions 
and tick execute.

Then open startup applications 
click add
name...startconky
click the browse button and click on .startconky (ctrl+h to show hidden files)
click add

log out , login and pray.

---

### Post by stinkeye on 2010-08-01
Coffee, mmmm.

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> ....

log out , login and pray.

Still no Conky love. I think that the guy that answers prayers is busy elsewhere tonight. ;-)

This has baffled me since yesterday. I have NO idea why it won't work with the delay. I can set a launcher up in the upper panel and it works just fine, I can launch it from the Applications>System Tools drop down and it will work also.

I do NOT have a second entry in startup for Conky - I removed that yesterday when I first started this endeavor and noticed that Conky would NOT start when I logged on.

I may just have to launch it manually for now. It would be cool to have it launch when I log in (after the delay, of course). When I find why this isn't working, I will post the fix here.

Thank you again for your help, you have been more than kind. If I could give you 'kudos' for it, I would.

Before I let you completely go, do you have any other ideas? I don't want to take up all your time on my non-critical issue.

---

### Post by stinkeye on 2010-08-01
Nah,I'm all out.
The only thing is the "~" shortcut does not work from startup applications.
Make sure you use the full path **/home/lappy/.startconky** in the command box.
Here's a tutorial that may help you.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

Good luck.


PS you can also check that your start up script is working by entering```
/home/lappy/.startconky
``` in the terminal

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> Nah,I'm all out.
The only thing is the "~" shortcut does not work from startup applications.
Make sure you use the full path **/home/lappy/.startconky** in the command box.
Here's a tutorial that may help you.
[**_[COLOR=DarkRed]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

Good luck.


PS you can also check that your start up script is working by entering```
/home/lappy/.startconky
``` in the terminal


I get this:

lappy@lappy-laptop:~$ /home/lappy/.startconky
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.compiz was not provided by any .service files
CONKY IS WAITING
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.compiz was not provided by any .service files
CONKY IS WAITING
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.compiz was not provided by any .service files
CONKY IS WAITING


etc....


Any thoughts?

---

### Post by stinkeye on 2010-08-01
Have you enabled the dbus plugin in compiz config settings manager. In utilities.

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> Have you enabled the dbus plugin in compiz config settings manager. In utilities.

Yes. I checked that when I read the first part of this thread.

---

### Post by stinkeye on 2010-08-01
Is compiz running.
Do you have the spinning cube or wobbly windows?

An easy way to check what window manager is running is by installing wmctrl
In the terminal
```
sudo apt-get install wmctrl
```

once installed enter ```
wmctrl -m
```


and you should  see
```
Name: compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

```

---

### Post by tabernash on 2010-08-01
> **stinkeye said:**
> Is compiz running.

Yes.


And guess what?




Now it works!

I re-did the entire making a file (and making it executable) in the **terminal**, I was using Nautilis before (right click in home folder window, make file, rename file, make executable, paste). I then pasted the script from step #16. Perhaps making it that other way was causing the issue? [COLOR=Red]**EDIT:**[/COLOR] Perhaps I was not being 'concrete sequential' when making the file through the GUI?

Either way, it now works.

I want to thank you for ALL your help. I mean that.



Now off to see what else I can break. ;-)


Once again, thank you for helping this n00b out.

+1 for you!

---

### Post by stinkeye on 2010-08-01
No problem.
It's the linux way.
Break ...fix... learn...break...

---

