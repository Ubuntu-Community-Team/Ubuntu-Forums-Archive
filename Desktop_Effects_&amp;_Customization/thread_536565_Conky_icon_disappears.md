---
title: "Conky icon disappears"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by ravimannan2002 on 2007-08-27
Conky covers the icons on my desktop. I checked  for help online, and from what I've read, I need to have my .conkyrc to have:

own_window yes
double_buffer yes
own_window yes
own_window_type override # if I change to desktop, conky disappears

And so that's what I have, but the icons still dont stay above conky.
Any ideas on how to make sure the icons stay on top of conky, rather than disappearing behind it?
Thanks in advance!

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
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
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 000000} ${alignr}${upspeedgraph eth1
25,140 000000 000000}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
```

---

### Post by ravimannan2002 on 2007-08-29
help? I'm using ubuntu 7.04, compiz-fusion and gnome .... ](*,)

---

### Post by ravimannan2002 on 2007-09-01
shameless bump. i'm desperate....

---

### Post by PurposeOfReason on 2007-09-01
This is a really bad solution but it works. Add some icons to your desktop that you don't want, stretch them to the width of conky and fill the area behind conky with them. Conky will now cover those ones and new onces will be created below them, not under conky.

---

### Post by ravimannan2002 on 2007-09-01
Thanks for the reply, but that didnt help. Conky still covers the icons.  Many people have got this to work.  My .conkyrc file looks the same as theirs, as far as I can tell.  I can't figure out what the problem is.....

---

### Post by SOULRiDER on 2007-09-02
Conky doesnt have tru transparency, it has pseudo transparency just like the transparency in your terminal (if youre not running compiz). AFAIK theres no way to 'fix' this.

---

### Post by ravimannan2002 on 2007-09-02
> **SOULRiDER said:**
> Conky doesnt have tru transparency, it has pseudo transparency just like the transparency in your terminal (if youre not running compiz). AFAIK theres no way to 'fix' this.

Thanks, I guess I should give up then....

---

### Post by shirilover on 2007-09-03
> **ravimannan2002 said:**
> Conky covers the icons on my desktop. I checked  for help online, and from what I've read, I need to have my .conkyrc to have:

own_window yes
double_buffer yes
own_window yes
own_window_type override # if I change to desktop, conky disappears

And so that's what I have, but the icons still dont stay above conky.
Any ideas on how to make sure the icons stay on top of conky, rather than disappearing behind it?
Thanks in advance!


Changing the value of gap_x will move the conky text area to the right.
Also, if you have nothing on the right side of your desktop, you can change the alignment to top_right or bottom_right.

---

### Post by ravimannan2002 on 2007-09-03
> **shirilover said:**
> Changing the value of gap_x will move the conky text area to the right.
Also, if you have nothing on the right side of your desktop, you can change the alignment to top_right or bottom_right.

Thanks for the input. I moved conky to the bottom right. The problem isnt so bad now. I still wish there was a solution for this....

---

### Post by shirilover on 2007-09-04
gap_x and gap_y are used to move the conky text area away from the alignment point.

I currently have icons on the right side and used alignment top_right.
I have also used a value for gap_x of 180 which moves the conky text area 180 pixels to the left and avoided covering my icons.

So, you try different values of gap_x until you find one to your liking; although, it does require you to kill and restart conky each time.

---

### Post by cconger on 2008-06-01
I know this is several months late.  But I found this post because I was having a similar issue.  I found that disabiling the own_window_hints sticky is what prevented conky from covering icons when it wasn't in front of them.  I hope you found a solution elsewhere but this is for everyone else who finds this post as I did.

---

### Post by tromort on 2008-07-15
> **cconger said:**
> I know this is several months late.  But I found this post because I was having a similar issue.  I found that disabiling the own_window_hints sticky is what prevented conky from covering icons when it wasn't in front of them.  I hope you found a solution elsewhere but this is for everyone else who finds this post as I did.

w00t that worked for me! thanks!

---

### Post by Technoviking on 2008-08-04
Disabling own_window_hints sticky did not change things for me. Any other ideas?

---

