---
title: "Conky weather: Temp gauge has 1 odd letter in it..."
date: 2009-09-03
forum: Desktop Environments
---

### Post by Motorhead Kaze on 2009-09-03
Hope that "desktop environs" is the place for a Conky question...

Hi! I just installed a conky on my desktop, and pretty happy with the results. The only problem is that it says Osaka is 29A°C but I am pretty sure it isn't "A degrees Celsius". The "A" in there has an accent mark over it too. I looked at the script for a long time but cannot figure out what is up. I am assuming that this is in the conkyForecast.config file, but not sure, so please don't mind me while I post that, and then the conkymain (conkyrc) script after it. Any suggestions on how to fix the font weirdness?

Thanks

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = JAXX0071
XOAP_PARTNER_ID = 1136396730
XOAP_LICENCE_KEY = 8a8043f277b8db61
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

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
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

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
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT


${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Time ${font}
${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}

${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Osaka ${font}
${offset 240}${font Weather:size=36}${execi 1800 conkyForecast --location=JAXX0071 --datatype=WF}$font 
${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font 
${offset 240}${color3}Wind: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=WS}
${offset 240}${color3}Humidity: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=HM}
${offset 240}${color3}Precipitation: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=PC}
${offset 240}${color3}Sunrise: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=SR}
${offset 240}Sunset: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=SS}$color

${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Seattle ${font}
${offset 240}${font Weather:size=36}${execi 1800 conkyForecast --location=USWA0395 --datatype=WF}$font 
${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font 
${offset 240}${color3}Wind: ${execi 1800 conkyForecast --location=USWA0395 --datatype=WS}
${offset 240}${color3}Humidity: ${execi 1800 conkyForecast --location=USWA0395 --datatype=HM}
${offset 240}${color3}Precipitation: ${execi 1800 conkyForecast --location=USWA0395 --datatype=PC}
${offset 240}${color3}Sunrise: ${execi 1800 conkyForecast --location=USWA0395 --datatype=SR}
${offset 240}Sunset: ${execi 1800 conkyForecast --location=USWA0395 --datatype=SS}$color

${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}System ${font}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}HIGHEST CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}HIGHEST MEM: 
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

${offset 240}${color slate grey}NET:
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Music ${font} 
${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}

```

---

### Post by Alfons81 on 2009-09-03
Hi,

I'm using a dual core processor but I guess that the path to get the processor temperature will be similar. Mines are those ones: 

/proc/acpi/thermal_zone/TZ00/temperature

/proc/acpi/thermal_zone/TZ01/temperature

I also saw people who have it like this:

/proc/acpi/thermal_zone/THRM/temperature

Then check the path to see where is your located your processor information. Then run this:

$ cat path_of_your/processor/temperature

it will show you the actual temperature, if you want to add it to Conky, and refresh this information any x seconds, you have to use on .conkyrc a similar line to the follow:

${execi 10 cat /proc/acpi/thermal_zone/TZ01/temperature | grep '[0-9][0-9]' -o} C

or

cat /proc/acpi/thermal_zone/THRM/temperature | grep -o “[0-9]* C”

I hope for your processor will be the same

---

### Post by j7%&lt;RmUg on 2009-09-03
> **Alfons81 said:**
> Hi,

I'm using a dual core processor but I guess that the path to get the processor temperature will be similar. Mines are those ones: 

/proc/acpi/thermal_zone/TZ00/temperature

/proc/acpi/thermal_zone/TZ01/temperature

I also saw people who have it like this:

/proc/acpi/thermal_zone/THRM/temperature

Then check the path to see where is your located your processor information. Then run this:

$ cat path_of_your/processor/temperature

it will show you the actual temperature, if you want to add it to Conky, and refresh this information any x seconds, you have to use on .conkyrc a similar line to the follow:

${execi 10 cat /proc/acpi/thermal_zone/TZ01/temperature | grep '[0-9][0-9]' -o} C

or

cat /proc/acpi/thermal_zone/THRM/temperature | grep -o &#8220;[0-9]* C&#8221;

I hope for your processor will be the same

He is not looking for cpu temp...

I have had a look at both files and although im not a conky expert i cant see anything wrong with either file, maybe you could post a screenshot of conky on your desktop?

---

### Post by SlugSlug on 2009-09-03
I remember I had that prob once.. it was solved with something like 
override_utf8_locale no
near the top of the config


--  just noticed you already have that in.

---

### Post by Giant Speck on 2009-09-03
Perhaps there's an error within conkyforcast.py itself?

---

### Post by Motorhead Kaze on 2009-09-03
Howdy. Sorry if I confused anyone, I am indeed talking about the temperature of the city itself. 

Giant Speck: I opened that file and laughed at the comment by Kaivalagi, "conkyForecast.py is a (not so) simple (anymore) python script to gather details of the current weather for use in conky." Amen to that...I haven't any idea what this says. "Altered pickle file naming?" There's the problem...there's a pickle in my file!

Here is a screenshot of my current conky, and it shows that mysterious "A" in my outdoor temp. Maybe it is a font issue?  

A little bit more info in case it reflects on your questions:
- The temperature reads with an extra "A" between the digits and degree mark.
- The "A" was there even before I added the symbol that shows the weather condition (using the font named "weather").
- The "A" was there even when I only had one weather report.

If anyone noticed in my script which I posted before, I am using two weather reports here (one for Osaka, one for Seattle) but I actually only have one conkyForecast.config file. I tried making 2, but it messed things up, so I left it with just one file. It does appear that the info for both Seattle and Osaka is different here, so it must be ok. Not helpful that currently Osaka and Seattle are both the same temp, so I cannot check that part.

In general though, this is a pretty darn educational experience. I really don't need my CPU temp. or my highest memory drain listed on my desktop, or the date for that matter. But it is a lot of fun to try out things like this.

I will reread your suggestions and look at my code again. If you come up with anything, please let me know!

Thanks

---

### Post by Alfons81 on 2009-09-03
Hi,

Excuse me I'm a bit sleepy, You were refering to wheather temperature...and I read very fast your explanation and then took a look at your conky file, I thought you where asking for processors information.:lolflag:

I'm curious, Can you see processor temperature with the end of this line?:

${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C


About your domand, I don't know because I'm not using conky weather.

---

### Post by Bruce M. on 2009-09-03
> **Motorhead Kaze said:**
> Howdy. Sorry if I confused anyone, I am indeed talking about the temperature of the city itself.

Hi Motorhead Kaze,

Cant believe you posted this here under Desktop Environments, when [ConkyForecast has it's own support thread.]("http://http://ubuntuforums.org/showthread.php?t=869328")

However, the answer to your question is a simple one. Edit this line above TEXT:
```
override_utf8_locale no
```
to:
```
override_utf8_locale yes
```

Also with this in your ~/.conkyforecast.config:

```
LOCALE = JAXX0071
```
I'm surprised it works at all.
That LOCALE is NOT for your city code, it's for your "language" code (blank is the default for English).

Mine for example reads:
```
LOCALE = es  #Spanish
```

Check```
/usr/share/conkyforecast/locale
```for a list of available languages.

Have a nice day.
Bruce

---

### Post by Motorhead Kaze on 2009-09-03
Bruce thank you! I am repairing all this with a biiiig grin. Learning rules!

1. I recognize your penguin! Your conky script is what I used to get this going in the first place. I really appreciate your time in writing a tutorial, and for helping me fix my mistakes now.

2. I clearly misunderstood the whole locale thing. It is fixed now.

Now I realize that I have one remaining problem. It is 26C here in Osaka, but back in Seattle it is colder...but my conky reads them as the same. I was supposed to add something more than just a bit more code in "conkymain" wasn't I? I cannot think of where though. Any ideas? Wind speed and all that is fine, just the temperature is not correct...

Thank you to all of you who replied. I appreciate your time.

Here is all I did to get 2 cities posted:
```
${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Osaka ${font}
${offset 240}${color3}${font Weather:size=36}${execi 1800 conkyForecast --location=JAXX0071 --datatype=WF}$font 
${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font 
${offset 240}${color3}Wind: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=WS}
${offset 240}${color3}Humidity: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=HM}
${offset 240}${color3}Precipitation: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=PC}
${offset 240}${color3}Sunrise: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=SR}
${offset 240}Sunset: ${execi 1800 conkyForecast --location=JAXX0071 --datatype=SS}$color

${offset 240}${color slate grey}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Seattle ${font}
${offset 240}${color3}${font Weather:size=36}${execi 1800 conkyForecast --location=USWA0395 --datatype=WF}$font 
${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font 
${offset 240}${color3}Wind: ${execi 1800 conkyForecast --location=USWA0395 --datatype=WS}
${offset 240}${color3}Humidity: ${execi 1800 conkyForecast --location=USWA0395 --datatype=HM}
${offset 240}${color3}Precipitation: ${execi 1800 conkyForecast --location=USWA0395 --datatype=PC}
${offset 240}${color3}Sunrise: ${execi 1800 conkyForecast --location=USWA0395 --datatype=SR}
${offset 240}Sunset: ${execi 1800 conkyForecast --location=USWA0395 --datatype=SS}$color
```

What did I miss...

---

### Post by Giant Speck on 2009-09-03
> **Motorhead Kaze said:**
> What did I miss...

This line:  

${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font

You forgot to replace Osaka's location code with Seattle's.

---

### Post by Bruce M. on 2009-09-04
> **Giant Speck said:**
> This line:  

${offset 240}${font Arial:bold:size=10}${color #ddaa00}${execi 1800 conkyForecast --location=JAXX0071 --datatype=HT}$font

You forgot to replace Osaka's location code with Seattle's.

Yup that's it!

---

### Post by Motorhead Kaze on 2009-09-05
Hello. Just wanted to say thanks. I always think that the world would be so much more fun if people helped random strangers like they do in Ubuntu.

Funny how after staring at this script for hours and hours that it begins to make sense, even though I have never seen this stuff before. Perl is it? Fun. 

Anyway, thanks!

---

