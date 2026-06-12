---
title: "Screenlet to display Unix Time"
date: 2014-05-17
forum: Desktop Environments
---

### Post by DigitalGrinch on 2014-05-17
I would like to display continual Unix time on my desktop, while keeping the default clock with standard 24-hour time. 

I was trying to do this is a screenlet, something floating, always on top, that was a clock counting Unix time, but I am not able to find what I am looking for

Does anyone know where I can find this?

I am not locked into a screenlet, if there was a way to display two clocks up top that would be ok too. I am **_not_** looking to add multiple clocks up top as described here:
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-display-time-from-multiple-cities-in-ubuntu/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-display-time-from-multiple-cities-in-ubuntu/)
I would want both clocks displaying and counting simultaneously, without the need to click something to show the additional clock as described on that page

I am also _**not**_ looking to change my default clock to Unix time. 

I need that standard clock to stay where it is, with the 24-hour time it displays now.

---

### Post by grumblebum2 on 2014-05-17
Conky will do it. You could set it in the panel or on the desktop(above or below other windows).
```
sudo apt-get install conky-all
```

This is the config to show in the panel.
Wasn't sure if you meant UTC time or actual unix time.
You can configure what you want in the last line of the config anyway. See man conky.
The conky $time variable uses the same format as the command date.
```
date --help
```

Save to **~/.conkyrc**
Running "conky" will load this config. 
Edit the **gap_x** value to move the position horizontally. 
```
####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont Sans:size=10
xftalpha 0.8
text_buffer_size 1024

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background no

####
## Update interval in seconds.
#
update_interval 1.0

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_colour 532C0E
own_window_title panelconky
own_window_type panel
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,above
default_color ffffff
own_window_argb_visual yes
own_window_argb_value 0

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no
default_shade_color 000000

####
## Draw outlines?
#
draw_outline no
#default_outline_color 000000

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment tm

####
## Minimum size of text area.
#
minimum_size 100 21
maximum_width 100

####
## Gap between text and screen borders.
#
gap_x -400
gap_y 0

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 1
border_outer_margin 1
border_width 1

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 FF4040
color5 FBE6B7 #text colour
color6 Gray
color7 AntiqueWhite4
color8 F9A41E
#color9 red
color9 6A90EF #icon


TEXT
${voffset 4}UTC ${utime %a %R}
```

---

### Post by DigitalGrinch on 2014-05-18
Thank you for the helpful response. This looks like what I am looking for. I would like the additional clock shown in the Menu Bar. I am not fully grasping the conky config though. I woule like Unix time, which in date format would look something like

```
date +%s
```

Where do I set this in .conkyrc? Is the TEXT at the bottom? If so I'm guessing I'd want something like
```
TEXT
$Unix Time ${date -%s}
```

not sure though

I would set own_window to no to disable the floater(Will not need it with the clock in menu bar). Does the menu bar happen automatically or is there a directive in the conf for that as well?

I see the gap_x and gap_y you mentioned. Will adjusting gap_x move the clock in the menu bar as well?

I am going to install this now and see if I can answer some of these questions myself

Again, thanks for the helpful response

---

### Post by grumblebum2 on 2014-05-18
Change the last line to....
```
${voffset 4}Unix ${time %s}
```

Also change these lines...
```
minimum_size **100** 21
maximum_width **100**
```
to 
```
minimum_size **120** 21
maximum_width **120**
```
for a greater width.

In the conkyrc, below "TEXT" are the objects/variable or what is displayed.
Above "TEXT" are the conky window and display settings.

Conky uses its own variables ....see the conky manual page...
```
man conky
```

You can run commands in conky by prefixing with exec or execi (adds an update interval in secs)
You want to avoid exec if possible  because they use a lot more resources than the inbuilt variables.
eg these would give the same output in conky....
[LIST]
[*]${time %s}
[*]${exec date +%s} 
[*]${execi 5 date +%s}
[/LIST]
but the first using the conky "time" variable uses the least resources.

---

### Post by DigitalGrinch on 2014-05-18
own_window needs to be set to 'yes' or it does not display.
gap_x does move it along the menubar

I have something displaying on menu bar, but not the correct time. I do not need any title so I am using

TEXT
${date +%s}

but that is showing that literally instead of the output of the command. I have tried a few variations here trying to get it to display. I googled 'conky "unix time"' but not finding the answer I am looking for. What do I need to set there to display Unix Time?

After the time is displaying correctly my next steps are aesthetics, making it blend in. Do you know the values I would need to set for own_window_color to have the background match the menu bar? I use the standard light grey text on dark grey menubar, I have not customized anything there. I see default_color is set to white(FFFFF), but I am not sure what the values are for the menu bars' light grey text or dark grey background.

---

### Post by DigitalGrinch on 2014-05-18
I was typing reply while you replied. Thanks, I am able to see Unix time now :D

Any tips on making it blend in to menu bar? right now the background is the same pattern as my desktop background image

---

### Post by grumblebum2 on 2014-05-18
> **DigitalGrinch said:**
> I was typing reply while you replied. Thanks, I am able to see Unix time now :D

Any tips on making it blend in to menu bar? right now the background is the same pattern as my desktop background image

You using compiz/unity?

---

### Post by DigitalGrinch on 2014-05-18
> **grumblebum2 said:**
> You using compiz/unity?

yes and yes

I found a page on design.ubuntu.org that lists warm grey and cool grey along with the text color of 333333
My text in conky is now the more muted color, but the background is still showing desktop image

---

### Post by DigitalGrinch on 2014-05-18
> **DigitalGrinch said:**
> yes and yes

I found a page on design.ubuntu.org that lists warm grey and cool grey along with the text color of 333333
My text in conky is now the more muted color, but the background is still showing desktop image

yes and no

def running compiz but running gnome 3

"GNOME 3.4.2"

---

### Post by grumblebum2 on 2014-05-18
The main settings  you may want to change are in this section...
```
own_window yes
own_window_colour 532C0E   [COLOR="#FF0000"]##window background color [/COLOR]
own_window_title panelconky
own_window_type panel
own_window_transparent yes    [COLOR="#FF0000"]## you could set this to no and "own_window_argb_visual no"  to show a background using "own_window_colour" [/COLOR]  
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,above
default_color ffffff   [COLOR="#FF0000"]##text color[/COLOR]
own_window_argb_visual yes    [COLOR="#FF0000"]##try no if you have display problems[/COLOR]
own_window_argb_value 0
```

The settings in the conkyrc I posted display fine for me using compiz with nvidia drivers.
If you want to add conky to startup use the -p (secs)option to pause conky starting until compiz is loaded.
eg
```
conky -p 20
```

Running 
```
zenity --color-selection
```
will give you a color picker if you want to set a backgroud the same color as the panel.

---

### Post by DigitalGrinch on 2014-05-18
RTFM'ing showed me 'own_window_transparent no' is what i needed
the values I got from design.ubuntu.org do not match however. I could try playing around with them, but if you know where these values are listed that would be easier.
I do not have GIMP installed on this system, but if I have to I could install that just to use its color picker, as I think that it would tell me the value

---

### Post by grumblebum2 on 2014-05-18
> **DigitalGrinch said:**
> RTFM'ing showed me 'own_window_transparent no' is what i needed
the values I got from design.ubuntu.org do not match however. I could try playing around with them, but if you know where these values are listed that would be easier.
I do not have GIMP installed on this system, but if I have to I could install that just to use its color picker, as I think that it would tell me the value
See previous post ...you may have missed some editing.

---

### Post by DigitalGrinch on 2014-05-18
If anyone else needs them, they are

535419
dfdbd2

I opened a screenshot in photoshop(running in vbox VM) and used it's eye dropper

---

### Post by DigitalGrinch on 2014-05-18
I am now ready to set background to yes, and setup an auto-launch for conky

Thank you very much! This was exactly the solution I was looking for. Appreciate your help in working with me to get it just right

---

### Post by grumblebum2 on 2014-05-18
No problem.
Best conky help here...
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2278")

---

### Post by DigitalGrinch on 2014-05-18
Posted. :)

---

### Post by grumblebum2 on 2014-05-18
I need to know what you use Unix time for?
According to "date --help" its seconds since 1970-01-01.
:confused:

---

### Post by DigitalGrinch on 2014-05-23
> **grumblebum2 said:**
> I need to know what you use Unix time for?
According to "date --help" its seconds since 1970-01-01.
:confused:

It is not "useful" by standards at which we judge usefulness, because not many *other* people use it, so we can not say "I'll meet you at 1400893632"

Being a lover of Unix, it is something I follow, admire. I like to say it encompasses all the time that matters, because before Unix, nothing mattered ;)

I missed the last 'milestone' for it, when it reached 1400000000, so I wanted this continual clock so I do not miss the next one. I needed this clock to be along side my standard 24-hr clock, which is the useful time to use.

I have been running Ubuntu on my main desktop for a few years now and love it. I am at my core a Unix man, I love OpenBSD. I chose Ubuntu because it supported newer hardware and has a great support network(this forum included), where OpenBSD runs great on old hardware but they are too slow to support modern hardware. Theo, I'm lookin' at you ;) (Theo is the founder of OpenBSD)

---

### Post by grumblebum2 on 2014-05-23
> **DigitalGrinch said:**
> It is not "useful" by standards at which we judge usefulness, because not many *other* people use it, so we can not say "I'll meet you at 1400893632"

Being a lover of Unix, it is something I follow, admire. I like to say it encompasses all the time that matters, because before Unix, nothing mattered ;)

I missed the last 'milestone' for it, when it reached 1400000000, so I wanted this continual clock so I do not miss the next one. I needed this clock to be along side my standard 24-hr clock, which is the useful time to use.

I have been running Ubuntu on my main desktop for a few years now and love it. I am at my core a Unix man, I love OpenBSD. I chose Ubuntu because it supported newer hardware and has a great support network(this forum included), where OpenBSD runs great on old hardware but they are too slow to support modern hardware. Theo, I'm lookin' at you ;) (Theo is the founder of OpenBSD)
Don't forget to mark **Fri Jul 14 02:40:00 UTC 2017** on your calendar 
for the 1500000000th seciversary extravaganza. :P
[http://www.epochconverter.com/epoch/clock.php](http://www.epochconverter.com/epoch/clock.php)

---

