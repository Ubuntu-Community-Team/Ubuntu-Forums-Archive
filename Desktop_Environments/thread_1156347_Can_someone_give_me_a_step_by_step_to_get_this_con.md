---
title: "Can someone give me a step by step to get this conky set up working"
date: 2009-05-11
forum: Desktop Environments
---

### Post by qjmoss on 2009-05-11
Hey, I need help with Conky...

I have never messed with conky with my two years of being a Ubuntu "member"

I really... don't know the first step to this..

I've already done

```
sudo apt-get install conky
```

And i've downloaded all of the files that are on this page.

```
http://conky.linux-hardcore.com/?page_id=764
```


The crinosconky.7z that i've downloaded is located on my desktop.


If someone could please give me a step by step to get this working..

I would be more than happy ;)


Thank you all so much for your time :)

---

### Post by Sarai the Geek on 2009-05-11
Well, I can't open the .7z archive type, and I assume that you won't be able to either so you'll have to pick out a different conky configuration, or email the owner and ask them to provide that one in a different archive format.

However, I will show you how to get a basic conky configuration up and running, and it's pretty easy to go from there. 
First, you need to create the configuration page, which dictates what information is displayed and how it is formatted.

```
gedit ~/.conkyrc
```

Copy and paste a premade config of your choice: here's a basic one I stole from Conky's website. 

```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1000 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 450
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(


# stuff after 'TEXT' will be formatted on screen

TEXT



${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}









${color slate grey}/var/log/messages:
${color}${exec tail -n20 /var/log/messages}

```

Save the page and then run the program by typing "conky" in a terminal. If you run into problems with flickering, disappearing desktop icons, etc, read [this. ]("http://saraithegeek.wordpress.com/2009/04/15/how-to-fix-conky-flickering-borders-and-drop-shadows/")

As far as editing it and making it your own goes, it's pretty straightforward. Everything before the TEXT marker is formatting and meta information, whereas after the text pretty much everything gets displayed. There are a few exceptions, ${font FOO: size=FOO2} changes the font and ${color HEXCODE} changes colors, both of those should be used with closing tags- ${font} and ${color} respectively. You can also use ${alignr} and ${alignc} for alignment. 
For a full list of variables (information that can be displayed) check [here]("http://conky.sourceforge.net/variables.html"). There are also a bunch of scripts out there that extend functionality. 

Let me know if you have more questions! :)

---

### Post by Dawei87 on 2009-05-11
just wanted to point out you can open .7z archives in linux, in ubuntu you must install this package through the repos: p7zip-full. makes it a lot easier when downloading stuff from deviantart.com, as it seems to be a popular archive there.

---

### Post by Sarai the Geek on 2009-05-12
> **Dawei87 said:**
> just wanted to point out you can open .7z archives in linux, in ubuntu you must install this package through the repos: p7zip-full. makes it a lot easier when downloading stuff from deviantart.com, as it seems to be a popular archive there.

Sweet, thanks!

---

