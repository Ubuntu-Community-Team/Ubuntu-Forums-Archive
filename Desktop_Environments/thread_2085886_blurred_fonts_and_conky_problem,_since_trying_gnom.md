---
title: "blurred fonts and conky problem, since trying gnome desktop session"
date: 2012-11-19
forum: Desktop Environments
---

### Post by pacharanero on 2012-11-19
I've done a fairly lengthy trawl of ubuntu forums and google etc but so far unable to quite grasp this one, hence asking for a bit of help.

I am using 64-bit Xubuntu 12.04 on a HP Pavilion DM4 14" laptop. no clever setups or hardware. I have a fairly plain conky setup which lists basic text system info (no graphics, but it does use transparency)

I had no problems at all until logging in using the Gnome desktop environment yesterday. I was trying out the other desktop environments available (before deciding xfce is definitely best!) I went through "Gnome", Gnome-classic", the plain "Xfce" option and then back to "Xubuntu" session.

**Since doing so there has been a minor but irritating difference in:**

a) the way fonts are rendered on screen - blurry/fuzzy - this is most apparent when there is strong contrast between text and background colour.

b) conky is malfunctioning such that areas that are refreshed (eg list of active processes) keep over-writing with the previous data so it is garbage. When I first went back to Xubuntu session, all the transparency effects were off, but it was a simple matter to re-enable them using the Window-Manager-Tweaks settings page. However I'm left with the other problems which won't go. [see screenshot]

I'm pretty sure this has something to do with the subpixel rendering and/or compositing, and presumably Gnome installed something or changed a setting that I can't see or don't know about in Xfce.

The problem seems to start at a defined point in the logon sequence, just after then desktop starts and then conky loads (starts off non-transparent and then goes transparent when the compositor start up, which I presume is normal behaviour, but its just after this point it goes blurry & double-overwrites). Before this point both the text and Conky look normal.

**What i HAVE tried:**

*checked screen resolution and refresh etc. screen is running at native resolution and setting appear normal. changing them made no difference.

*fiddled with the fonts settings in Xfce settings - the various options for hinting and subpixel RGB order etc make a small amount of difference but it's still not possible to get a setting that looks right.

*looking at the Xfce settings editor there seemed to be a few other options I could edit there, although I didn't understand all of them and couldn't seem to find much information about them. In particular I wondered what the "string" setting of: xsettings/Xft/lcdfilter should be, and whether this was the problem (although I couldn't see how this would cause "ghosting" on conky. Here's my Xft settings, from running ```
xfconf-query -c xsettings -l -v
``` in terminal.

```
/Xft/Antialias                  1
/Xft/DPI                        90
/Xft/Hinting                    1
/Xft/HintStyle                  hintslight
/Xft/Lcdfilter                  lcdnone
/Xft/RGBA                       rgb
```[B]Any help or pointers gratefully recieved. There should be a screen grab of the blurring on Conky, and my .conkyrc file (well the relevant bit) is below:

Thanks,

pacharanero
[/B]
```
# set to yes if you want Conky to be forked in the background
background yes
imlib_cache_size 0
# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Ubuntu :size=9
xftfont Ubuntu :size=9
# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

mpd_port 6600

# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type override
own_window_argb_visual yes
own_window_argb_value 0
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes

# Minimum size of text area
#minimum_size 220 5

# Maximum width
maximum_width 300

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
border_margin 5

# border width
# border_width 1

# Default colors and also border colors
default_color aaaaaa

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none dd

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
default_bar_size 300 7

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen
```

---

### Post by Toz on 2012-11-19
With respect to b), do you have more than one instance of conky running? Open a terminal window and run the following:
```
ps -ef | grep conky | grep -v grep
```
If it returns more than one instance of conky, try killing one of the processes.

With respect to a), are all fonts experiencing this problem or just conky fonts?

---

### Post by pacharanero on 2012-11-20
thanks Toz.

```
ps -ef | grep conky | grep -v grep
```did indeed confirm that there were 2 instances of conky running. how odd.

anyway, I killed one off and all seems well on the conky front

The font thing seems to have got better now I have managed to find out what the options are for  xsettings/xft/lcdfilter  -  I changed "lcdnone" to "lcdlegacy" and it seems lots better. the other option, which I have not tried yet, is "lcdlight"

as long as it doesn't revert next time I reboot, then hopefully will be able to mark as solved.

M

---

### Post by pacharanero on 2012-11-25
[follow-up]

Trying a Gnome session seems to have messed up a range of minor configuration files including:

font rendering settings: xfdesktop/xft/lcdfilter set to "lcdnone" when it should be "lcddefault", "lcdlight" or "lcdlegacy" for my monitor

printing settings: the CUPS server setting "Publish shared printers connected to this sytem" was disabled, meaning I couldn't print to my network printer, but it took ages to trace the problem.


That'll teach me for trying Gnome. :-)

/pacharanero

---

