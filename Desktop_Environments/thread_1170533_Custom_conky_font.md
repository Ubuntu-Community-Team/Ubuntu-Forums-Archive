---
title: "Custom conky font"
date: 2009-05-26
forum: Desktop Environments
---

### Post by steelsparky on 2009-05-26
Hello, I've searched and searched and can't find an answer to this problem. I'm sure its quite easy but I am new to linux. 

I've finally configured conky to my likings, however, I would like to have a custom font. I've added the font, refreshed the cache and cannot get it to display.... please tell me what I'm doing wrong here...



I have this in fonts..
#Xft font when Xft is enabled
xftfont atomico:size 8

And I've messed around with the "#" although not too sure what it does for me...

please help!

---

### Post by MysticGold04 on 2009-05-26
> **steelsparky said:**
> Hello, I've searched and searched and can't find an answer to this problem. I'm sure its quite easy but I am new to linux. 

I've finally configured conky to my likings, however, I would like to have a custom font. I've added the font, refreshed the cache and cannot get it to display.... please tell me what I'm doing wrong here...



I have this in fonts..
#Xft font when Xft is enabled
xftfont atomico:size 8

And I've messed around with the "#" although not too sure what it does for me...

please help!

try this:

```

xftfont atomico:size=8

```

the # symbol is used to clarify a comment, and conky will ignore lines with the # symbol, except for the configuration below the TEXT heading.

---

### Post by steelsparky on 2009-05-26
> **MysticGold04 said:**
> try this:

```

xftfont atomico:size=8

```the # symbol is used to clarify a comment, and conky will ignore lines with the # symbol, except for the configuration below the TEXT heading.


Thanks for the reply. I actually did have the '=' in there and still the same thing...here's my .conkryc

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel

#Use Xft?
use_xft yes


xftfont atomico:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 260

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 45
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

TEXT
${font atomico:size=8}${time %I:%M %P}${font}
${color #0077ff}Battery $color${battery_percent BAT0}% ${battery_time BAT0} ${color #0077ff}${battery_bar BAT0}

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color #0077ff}Proces:${color lightgrey} $processes  ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $memperc% ${alignr}${color #0077ff}${membar 5,120}

${color #0077ff}Hard Disks:
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color #0077ff} SD ${color lightgrey}${fs_used /media/disk}/${fs_size /media/disk}${alignr}${color #0077ff}${fs_bar 5,120 /media/disk}

${color #0077ff}Network: $color${wireless_essid ra0}${alignr}${color #0077ff}IP: ${color lightgrey}${addr ra0}
${color #0077ff}Speed: $color${wireless_bitrate ra0}${alignr}${color #0077ff}Signal: $color${wireless_link_qual_perc ra0}%
${color #0077ff}Down:${color lightgrey} ${downspeed ra0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed ra0} k/s
${color #0077ff}${downspeedgraph ra0 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph ra0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown ra0}           $alignr${color lightgrey}${totalup ra0}

${color #0077ff}Weather:
${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=CN --refetch}

${color #0077ff}Day: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=DW}
${color #0077ff}Conditions: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=CC}
${font ConkyWeather:size=36}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=WF}${font}
${color #0077ff}Temp: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=HT -i}
${color #0077ff}Wind: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=WS -i}
${color #0077ff}Wind Direction: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=WD}
${color #0077ff}Humidity: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USOH1075 --datatype=HM}
```

---

### Post by Sarai the Geek on 2009-05-26
What type of font is it (truetype, etc) and what folder did you install it in?
Are you sure the font name is spelled and capitalised correctly?

If you want to upload and attach that font, I'll install it on my system and play around with it...

---

### Post by steelsparky on 2009-05-26
> **Sarai the Geek said:**
> What type of font is it (truetype, etc) and what folder did you install it in?
Are you sure the font name is spelled and capitalised correctly?

If you want to upload and attach that font, I'll install it on my system and play around with it...

I think it's a truetype, it is a ttf. I have it located in /usr/share/fonts/truetype/custom

here's the zip

Thanks!

---

### Post by Sarai the Geek on 2009-05-26
> **steelsparky said:**
> I think it's a truetype, it is a ttf. I have it located in /usr/share/fonts/truetype/custom

here's the zip

Thanks!

Ah hah... Try putting it in /usr/share/fonts/truetype/ instead, should work then- don't forget to refresh the cache, and you'll probably need to restart conky.
I gotta run, didn't have time to test it myself. If the above doesn't work, try capitalising the font name- Automico or whatever it is...

---

### Post by MysticGold04 on 2009-05-26
Here's the skinny on adding new fonts to the system.  Double check to make sure that you've followed these directions to make sure your font is available to the system.. You can check in openoffice or AbiWord or any other editor you have that allows the use of truetype fonts to verify availability. 

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by steelsparky on 2009-05-26
> **Sarai the Geek said:**
> Ah hah... Try putting it in /usr/share/fonts/truetype/ instead, should work then- don't forget to refresh the cache, and you'll probably need to restart conky.
I gotta run, didn't have time to test it myself. If the above doesn't work, try capitalising the font name- Automico or whatever it is...

I tried everything you suggested and it still doesn't work. When I change it in my script to Arial, it does change. I've even created a ~/.fonts in home folder and placed it there, after refresh still no change. It's really starting to get somewhat annoying. Thanks for your time.

---

### Post by steelsparky on 2009-05-26
> **MysticGold04 said:**
> Here's the skinny on adding new fonts to the system.  Double check to make sure that you've followed these directions to make sure your font is available to the system.. You can check in openoffice or AbiWord or any other editor you have that allows the use of truetype fonts to verify availability. 

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Thanks, I can use any new font I add in open office, so that why I'm so confused. I also added the font to all users and still nothing. I'm still scratching my head..

---

### Post by Sarai the Geek on 2009-05-26
I've had a chance to sit down and play with the font a bit, and I think there's a problem with the font. On my computer, at least, it shows the font name with an accent over the first o that varies depending on what program it's displayed in. In my appearance preferences window, it shows the font name as ATÔMICO whereas in OO Writer it shows as ATÖMICO. I've tried both of these names in conky, along with a few variations and nothing seems to work. Any chance you could pick another font?

---

### Post by steelsparky on 2009-05-26
> **Sarai the Geek said:**
> I've had a chance to sit down and play with the font a bit, and I think there's a problem with the font. On my computer, at least, it shows the font name with an accent over the first o that varies depending on what program it's displayed in. In my appearance preferences window, it shows the font name as ATÔMICO whereas in OO Writer it shows as ATÖMICO. I've tried both of these names in conky, along with a few variations and nothing seems to work. Any chance you could pick another font?


Yeah, I noticed that too and played around with it also. I download 2 other fonts from different sources and its the same story. Any specific font providers I should be looking at?

---

### Post by Sarai the Geek on 2009-05-26
> **steelsparky said:**
> Yeah, I noticed that too and played around with it also. I download 2 other fonts from different sources and its the same story. Any specific font providers I should be looking at?
I like fonts from Fonts for Peas-
[http://www.kevinandamanda.com/fonts/freescrapbookfonts/](http://www.kevinandamanda.com/fonts/freescrapbookfonts/)
and
[http://kevinandamanda.com/fonts/fontsforpeas/](http://kevinandamanda.com/fonts/fontsforpeas/)

They might be a little girlish and fancy for your tastes, but they have always worked right off the bat and aren't missing any major punctuation marks like fonts from some other places (try making your conky look good when the font doesn't contain slashes!). 
For my conky layout, I just use [Gentium ]("http://www.sil.org/%7Egaultney/Gentium/")for the base font then fancy stuff to add accent depending on the overall theme I'm going for.

You should also browse through the [Conky Showcase thread]("http://ubuntuforums.org/showthread.php?t=281865") here to see what other people are using in their layouts, if it works for them chances are good it will work for you too!

---

