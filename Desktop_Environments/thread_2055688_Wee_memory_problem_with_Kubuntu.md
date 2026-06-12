---
title: "Wee memory problem with Kubuntu"
date: 2012-09-09
forum: Desktop Environments
---

### Post by M_Mynaardt on 2012-09-09
Hi there!

I'm just trying out Kubuntu on a portable install.  It took me a bit of time to get Conky having a transparent background in Kubuntu.

Going by information I found here and there, I got Conky's background transparent working by installing the graphics app "feh" and then used that in my **.conkyrc** file this way:
```
${texeci 600 feh --bg-scale '/usr/share/wallpapers/kde-default.png'}
```

So far, so good.  ***But*** ... once I had that working nicely, I saw the use of RAM (via my Conky display) went up from about 30% to 45%.  And kept climbing higher; it never seems to decline even when I've closed apps that brought the RAM up in the first place.

Would anyone know if I did something wrong in my **.conkyrc** file to cause this extra RAM and CPU use to be happening?  Or might there be some other setting I've overlooked that could be keeping the use of RAM and CPU staying high?

Thanks in advance!

---

### Post by 2F4U on 2012-09-10
Isn't the task manager showing which applications are using the most memory? Another option would be to revert the changes to conky and see if that is the cause of the issue.

---

### Post by Epodx64 on 2012-09-10
open a terminal and run 
top
That will show you everything

---

### Post by bra|10n on 2012-09-10
> **M_Mynaardt said:**
> 
Would anyone know if I did something wrong in my **.conkyrc** file to cause this extra RAM and CPU use to be happening?  Or might there be some other setting I've overlooked that could be keeping the use of RAM and CPU staying high?

Thanks in advance!

Feh is a somewhat dated method for achieving transparency in conky. 
Transparency can now be achieved simply by adding the following lines;
```
own_window_type normal
own_window_argb_visual yes 
own_window_transparent yes
```Also without seeing the contents of your conkyrc file it is near impossible to provide an answer to your question.

Feel free to post it here...

---

### Post by M_Mynaardt on 2012-09-10
> **2F4U said:**
> Isn't the task manager showing which applications are using the most memory? Another option would be to revert the changes to conky and see if that is the cause of the issue.

There were 126 processes running.  Very few of them registering measurable RAM USE.  Xorg was changing between 5% to 13%, Conky sometimes hit 1%, but then went below that again.  And Kysysguard used round about 3%.

I also saw 8 instances of **kio_http:** - is that normal?

---

### Post by M_Mynaardt on 2012-09-10
> **Epodx64 said:**
> open a terminal and run 
top
That will show you everything

Is there anything in particular I should be looking for?  Xorg, as I saw in the system monitor, was the big memory hog; hovering aroudn 10-13% now.  Everything was 1% or less.

---

### Post by M_Mynaardt on 2012-09-10
> **bra|10n said:**
> Feh is a somewhat dated method for achieving transparency in conky. 
Transparency can now be achieved simply by adding the following lines;
```
own_window_type normal
own_window_argb_visual yes 
own_window_transparent yes
```Also without seeing the contents of your conkyrc file it is near impossible to provide an answer to your question.

Feel free to post it here...

I tried that change; removing the line withe feh, and inserting the argb_visual line.  It was transparent.  But a lot of the colours were all wrong and the animations on the memory and cpu gauges I like to use were really sluggish and downright bad.

Here is a copy of my .conkyrc file.  Hopefully there's something there someone can make sense of more than me.

```
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# performance settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
cpu_avg_samples 4
no_buffers no
double_buffer yes
override_utf8_locale no
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# overall position of window
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
alignment top_right
gap_x 30
gap_y 40
minimum_size 320 100
# minimum_size (width),(height)
maximum_width 320
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# other window settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
background no
own_window yes
# ----------
# use these three lines instead of the feh:
own_window_type normal
# own_window_argb_visual yes
own_window_transparent yes
# ----------
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 101040
border_inner_margin 0
border_width 5
draw_borders no
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# text settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
font ubuntu:size=12
max_text_width 0
draw_shades yes
draw_outline yes
uppercase no
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# graph settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
draw_graph_borders yes
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# colour settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
default_color 7299fc
# A shade of blue found in KDE filter icons
color0 00fe79
# green for good battery charge
color1 ff0033
# red for low battery charge
color2 fc9a6c
# orange colour for file system bar
color3 fefe79
# yellow colour for swap space bar
color4 5aed5a
# green colour for RAM display
color5 e094e1
# purple CPU display 
color6 3dfbf5
# teal 
#
##############################################
#  Output
##############################################
TEXT
${texeci 600 feh --bg-scale '/usr/share/wallpapers/kde-default.png'}
${font urw chancery l:size=32}${alignc}Kubuntu${font}
${voffset 10}Time  ${hr 2}${color6}
${font ubuntu mono}${voffset 05}${offset 20}System Up Time$alignr${offset -100}$uptime_short
${voffset 05}${offset 20}Current Time$alignr${offset -100}${time %R}${font}${color}
${voffset 10}Battery  ${hr 2}${font}
${voffset 05}${offset 20}${font ubuntu mono}${if_match $battery_percent > 15}${color0}${else}${color1}${endif}$battery$alignr}${if_match $battery_percent != 100}$battery_time${else}  fully charged${endif}
${voffset 05}${offset 40}${battery_bar 12}${color}${font}
# display battery bar; light green for okay, red for running low
${voffset 10}Hard Drive  ${hr 2}${font}
${voffset 05}${offset 20}${color2}${font ubuntu mono}File System $fs_used_perc%$alignr${color #fc9a6c}($fs_used / $fs_size)
${voffset 05}${offset 40}${fs_bar 12}
${voffset 05}${offset 20}${color3}Swap Space $swapperc%$alignr($swap / $swapmax)
${voffset 05}${offset 40}${swapbar 12}${color}
${voffset 10}${font}Performance  ${hr 2}
${voffset 05}${offset 20}${color4}${font ubuntu mono}Memory $memperc%
${offset 40}${memgraph 20,190 008000 00ff00 -t}$alignr${voffset -15}${memgauge 35,70}
${offset 20}${color5}CPU ${cpu}%
${offset 40}${cpugraph 20,190 800080 ff00ff -t}$alignr${voffset -15}${cpugauge 35,70}${color}${font}
${hr 2}
```

I've also attached a screenshot (reduced a bit in size)

(thanks in advance)

---

### Post by bra|10n on 2012-09-10
> **M_Mynaardt said:**
> I tried that change; removing the line withe feh, and inserting the argb_visual line.  It was transparent.  But a lot of the colours were all wrong and the animations on the memory and cpu gauges I like to use were really sluggish and downright bad.

own_window_argb_visual will only enable transparency. It is not responsible for colour settings etc, so the issues you had were caused by something else I'm afraid.

In all honesty your conkyrc is a mess. But first things first...

To establish if conky is responsible for your increase in cpu and ram usage, quit conky by running the following in a terminal;
```
killall conky
```Run top in a konsole and note the usage without conky running.
Now start conky via a konsole by running the following;
```
conky -c /PATH/TO/YOUR/conkyrc
```Run top in a konsole again and compare the usage with/without conky...

Now that you are satisfied conky is the culprit here, I'd suggest the following;

1. Not using the Feh option but the own_window_argb_visual method I mentioned to achieve transparency.
2. Changing **$uptime_short** to **${uptime_short}**.
3. Removing Battery state lines altogether. The same thing sits in your system tray.
4. Removing all instances of **${font ubuntu mono}** and corresponding **${font}** entries from below "TEXT" and changing the line **font ubuntu:size=12 **above TEXT to **xftfont Ubuntu Mono:size=12**.
5. **cpu_avg_samples 4** to **cpu_avg_samples 1**.
6. Remove **border_inner_margin 0** altogether.
7. **draw_outline yes** to **draw_outline no**.
8. Delete all **${voffset 10}** instances and replace with a blank line.
9. Use **${goto }** in place of **${offset }**, particularly where you have 2 offsets in use on the same line.

Do this by backing up your conkyrc first, so that you can revert to your original conkyrc if you wish.
HTH

References:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by M_Mynaardt on 2012-09-11
> **bra|10n said:**
> own_window_argb_visual will only enable transparency. It is not responsible for colour settings etc, so the issues you had were caused by something else I'm afraid.

In all honesty your conkyrc is a mess. But first things first...

To establish if conky is responsible for your increase in cpu and ram usage, quit conky by running the following in a terminal;
```
killall conky
```Run top in a konsole and note the usage without conky running.
Now start conky via a konsole by running the following;
```
conky -c /PATH/TO/YOUR/conkyrc
```Run top in a konsole again and compare the usage with/without conky...
[... snip, snip, snip ...] 


I was out and and only just tried looking at this again.  I did the **killall** to Conky.  And when I ran **top**, the memory in use continued to climb.  It was over 63% memory used when I finally shut things down.  So maybe Conky's not to blame after all.

I didn't see any process there listed that took up more than 7% of the memory.  And that was Xorg, but that one kept on popping in and out of the list.  It also told me that there were 130 plus tasks running.  The great majority of which were sleeping.

So, is there some setting that should be able to reduce the amount of memory Kubuntu is using on my laptop?  It just seems kind of odd that the amount of memory in use should continue to climb, whether I'm running apps or not.

And might it have something to do with the computer I'm trying it on being a bit of an ageing old machine?  It's a Toshiba Satellite A-100 and I'm trying out Kubuntu on an external USB HDD.

I usually use Xubuntu on my desktop PC and Lubuntu on my laptop.  So, I'm just trying to learn a bit of KDE while I'm on sick leave.

Thanks!

---

