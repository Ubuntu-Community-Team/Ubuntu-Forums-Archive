---
title: "Conky issues"
date: 2009-06-23
forum: General Help
---

### Post by Niksko on 2009-06-23
I have two conky windows running at a time. For some reason ever since I have upgraded to Jaunty a few issues have developed that were not present back on Intrepid.
1) Conky just disappears after a while. No error, just disappears. And the output from the terminal shows no error either. Which leads on to...
2) Strange terminal output that doesn't seem to go away. It looks like this:
```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 12478  100 12478    0     0  13189      0 --:--:-- --:--:-- --:--:-- 29260
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 12478  100 12478    0     0  11544      0  0:00:01  0:00:01 --:--:-- 25845

```
This is present and updates every so often while it is running, but even more strangely, if it exits of it's own accord or I kill it it ctrl-c, it still seems to persist, popping up no matter what I'm doing until I close the terminal.
3) There is now a black border around my conky windows, which was not present before.

I suspect the first two problems are related, but the last is probably a separate issue.

Here are my two conkyrc files:
```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes
# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 3
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type desktop

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 150 5
maximum_width 900

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
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
gap_x 10
gap_y 500
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes
# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player none

text_buffer_size 2048
TEXT
${color #dddddd}
${scroll 16 $nodename - $sysname $kernel on $machine | }
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${font FFF Tus:size=12}Weather in Moorabbin:
${font Sans:size=10}${execi 60 /home/niksko/bin/bomweather | fold -s -w60}
${font Sans:size=12}Twitter replies;
${font Sans:size=10}${execi 120 /home/niksko/bin/twittersearch @niksko | head -n 5}

```

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
xftalpha 0.8

on_bottom yes

mail_spool $MAIL

# Update interval in seconds
update_interval 3

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type desktop

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 150 5
maximum_width 900

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
gap_x 10
gap_y 10
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player none

text_buffer_size 2048
TEXT
${color #dddddd}
${font Sans:size=22}${alignr}${time %A, %d %B %Y}${font Sans:size=8}
${font FFF Tusj:size=100}${alignr}${time %I:%M %p}${font Sans:size=10}
```

And the relevant scripts:
/home/niksko/bin/bomweather:
```

#! /bin/bash
curl -s --connect-timeout 30 -u bomw0007:aviation "http://www.bom.gov.au/products/reg/area30_tafmet.shtml" | egrep '(METAR|SPECI) YMMB'
exit 0
```

and /home/niksko/bin/twittersearch
```
#! /bin/bash
# Description: Script to search for tweets. Requires curl installed.
# Author: Dave MacLeod
# Date: 12 Jan 2009

# check that one, and only one, parameter has been passed
if [[ $1 == "" ]] ; then
        echo "Needs a parameter to search for"
        exit 1
fi
if [[ $2 != "" ]] ; then
        echo "Needs only one parameter"
        exit 1
fi

# perform the search, get rid of html tags, include lines with the search term, and a colon, exclude spurious text, convert quotes and ampersands and remove excess spaces
curl http://search.twitter.com/search?q=$1 | \
        sed -e 's_<[^>]*>__g' | \
        grep $1 | \
        grep ':' | \
        grep -v 'middot' | \
        grep -v 'Reply' | \
        grep -v 'Summize' | \
        sed -e 's_&quot;_"_g' | \
        sed -e 's_&amp;_and_g' | \
        sed -e 's_  __g'

exit 0

```

Oh, and attached is a screen of the black border I'm talking about. Sorry about the length of the post.

Thanks

-Nik

-PS: Conky crashed just as I took the screen shot.

---

### Post by VCoolio on 2009-06-23
The black border is a dropshadow. If you run compiz you can disable that in the window decoration plugin; in the 'shadow windows' entry fill in !conky or !(class=Conky) , something like that, just try it out. The exclamation mark indicates an exception.

The other issues I don't know for sure, summarize your question in the big conky thread in the café section and point to this thread. There are some bright conky users there all the time. Two options though. You do have in both configs a double entry for own_window_transparent, first no and then yes. Delete on of them. And you have own_window_type desktop, now try changing that to normal. Also in compiz, general settings, uncheck the 'hide skip taskbar applications' option. Otherwise it minimizes all apps when you click the 'show desktop' button and since conky is not in your taskbar it will be lost while still running.

---

### Post by Niksko on 2009-06-23
I followed all your instructions.

First off, I got rid of the dropshadow, so that's good.

Secondly, the random text is not much of a problem. I just have to close the terminal and open a new one if I want to do some work unimpeded.

Lastly, a new problem seems to have arisen. Both conky windows were up, but then one of them disappeared. Just as I began to write this it came back all of it's own accord.

The plot thickens. I'll try linking this in the main conky thread.

Thanks

-Nik

---

### Post by psychoelf on 2009-08-08
Have you had any luck?  I've been searching on this for a few months and have had no luck.  My conky just randomly disappears also.  Usually if I open a window or program over it.  Then it will eventually randomly come back.

FYI  I'm running ATI 2600HD Mobility with latest catalyst drivers and NO compiz at all.

If you want my conkyrc let me know!

---

