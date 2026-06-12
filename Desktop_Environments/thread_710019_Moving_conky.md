---
title: "Moving conky"
date: 2008-02-28
forum: Desktop Environments
---

### Post by linux phreak on 2008-02-28
I installed conky today and it is stuck in the bottom left corner.How can i move it to the top right ?.I searched the forum but was not able to find the answer.The trouble is i am not able to find the file conky.rc anywhere.Please help.Thanks

---

### Post by loudnlownoma on 2008-02-28
The config file for conky is actually named .conkyrc     If you installed it with the default install, this should be in your home folder, but files and folders there with a "." in front will be hidden.  Hitting View > Show hidden files should add a bunch more into the view, including the .conkyrc file to edit

---

### Post by linux phreak on 2008-02-28
I installed from terminal.But even if i enable the hidden files in home it is not present

---

### Post by loudnlownoma on 2008-02-28
I can't remember if I had to create it or it made a default one - it's been a little while.  If you try creating a new one with a template found around here, does that show up right?

It looks like you may have to make it...  the following thread has some great instructions and help with the config file, including a good starting template in the first post, where I based mine from as well.

[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

---

### Post by linux phreak on 2008-02-28
I made an empty file named conkyrc and pasted the config in the thread given by you.It is now showing in the top right.But the top panel is overlapping some portions.How can i move it a little down.?

---

### Post by loudnlownoma on 2008-02-28
I think I had the same problem.  One of the last sections before the on-screen text starts in mine has:

```

# Gap between borders of screen and text
gap_x 10
gap_y 25

```

These settings work for me, but you can adjust them to space it out however you want.

---

### Post by linux phreak on 2008-02-28
Thank you.But it is not moving Although i changed the values to 25.Do i need to restart the system?Also can i make it run at statup?

---

### Post by loudnlownoma on 2008-02-28
I think that was the one I used to move it.  Here's a copy of my full config right now:

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
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 25

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignc}${color orange}Dan's Desktop - Ubuntu 7.10 Gutsy
${alignc}${color orange}Uptime: $uptime$color

${color orange}CPU / CORE 2 Q6600${hr 2}$color
${color white}${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}$color
${color blue}$cpubar$color
${color white}Core 1 Usage: ${alignc} ${cpu cpu1}%$color ${color blue}${cpubar cpu1}$color
${color white}Core 2 Usage: ${alignc} ${cpu cpu2}%$color ${color blue}${cpubar cpu2}$color
${color white}Core 3 Usage: ${alignc} ${cpu cpu3}%$color ${color blue}${cpubar cpu3}$color
${color white}Core 4 Usage: ${alignc} ${cpu cpu4}%$color ${color blue}${cpubar cpu4}$color
${cpugraph 000000 00ff00}
${color orange}MEMORY${hr 2}$color
${color white}RAM: $mem/$memmax - $memperc% $color${alignr}${color blue}${membar 5,110}$color
${color white}Swap: $swap/$swapmax - $swapperc% $color${alignr}${color blue}${swapbar 5,110}$color

${color white}Home:   ${fs_used /} / ${fs_size /}$color${alignr}${color blue}${fs_bar 6,110 /}$color
${color white}Vista: ${fs_used /media/HP} / ${fs_size /media/HP}$color${alignr}${color blue}${fs_bar 6,110 /media/HP}$color
${color white}Shared:   ${fs_used /media/NEW VOLUME} / ${fs_size /media/NEW VOLUME}$color${alignr}${color blue}${fs_bar 6,110 /media/NEW VOLUME}$color

${color orange}CPU / MEMORY USAGE${hr 2}$color
${color white}NAME                PID      CPU%      MEM%
$hr$color
${color green}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}$color
${color white}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
$hr$color
${color green}${top_mem name 1} ${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}$color
${color white}${top_mem name 2} ${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3} ${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}$color

${color orange}INTERNET (${addr ppp0}) ${hr 2}$color
${color white}Down: ${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s$color
${downspeedgraph ppp0 25,140 000000 00ff00} ${alignr}${upspeedgraph ppp0 
25,140 000000 00ff00}$color
${color white}Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}$color

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
${color white}Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s$color
${downspeedgraph eth0 25,140 000000 00ff00} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
${color white}Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}$color

${color orange}LOGGING ${hr 2}$color
${color white}${execi 30 tail -n3 /var/log/messages | fold -w50}$color

${color orange}FORTUNE ${hr 2}$color
${color white}${execi 120 fortune -s | fold -w50}$color

```


As for startup, I made a script named conky.sh or something similar, and use the following code(although you may need to try different sleep times, as each computer will load faster or slower, and stuff like Compiz will cause problems if it loads after conky sometimes):

```

#!/bin/bash
sleep 60 && conky;

```

Then, make the script executable (with the chmod command) and then add it to your startup items - System > Preferences > Sessions - then choose add and select the conky.sh

---

### Post by loudnlownoma on 2008-02-28
And a screenshot....

---

### Post by linux phreak on 2008-02-28
Thanks alot man.Conky is fully configured right now.But the startup is a bit too advanced for me.Can you simplify it.Also i donot have any compiz fusion installed.Thanks again

---

### Post by loudnlownoma on 2008-02-28
No prob, happy to help.  Basically, go to terminal and type:

```

sudo gedit .conky_start.sh

```

In the new file, enter the two lines I had above:

```

#!/bin/bash
sleep 20 && conky;

```

This will make conky start 20 seconds after login I believe, and should be fine.  If you have any conflicts or get borders around it or anything, try increasing the number to let it wait longer.  After this is in, save and exit that, then run:

```

sudo chmod a+x .conky_start.sh

```

This makes the script executable, so that your startup can run the script and start conky.

Then just add the script to the list of start up items:

System > Preferences > Sessions - then choose add and select the .conky_start.sh

---

### Post by uberlube on 2008-02-28
also if you want it to be in the top right press alt+F2 and enter:

conky -a top_right

---

### Post by linux phreak on 2008-02-28
The problem is that i am running xubuntu and i am unable to find 'add' option in the sessions menu.I made the start up script as instructed by you and the final problem is where to put the script to in xubuntu.

---

### Post by loudnlownoma on 2008-02-28
> **uberlube said:**
> also if you want it to be in the top right press alt+F2 and enter:

conky -a top_right

Won't that just run it the one time in that position?  If you don't type that each time, it would run in the config's stated position.  So if you don't alternate back and forth and pretty much leave it in one spot all the time, it would be easier just to have it in the config file and placed where you want.  Although I'm still a noobie myself, so I could be wrong.

---

### Post by loudnlownoma on 2008-02-28
> **linux phreak said:**
> The problem is that i am running xubuntu and i am unable to find 'add' option in the sessions menu.I made the start up script as instructed by you and the final problem is where to put the script to in xubuntu.

Ahhh...that one I'm not positive on.  Only messed with Ubuntu and Kubuntu myself, so I'm not sure exactly how that's setup in Xubuntu.  :(

---

### Post by loudnlownoma on 2008-02-28
I also found [this link](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) after a quick search on the forums, but can't attest to it working personally, as I have used Gnome's session manager for all mine.

---

### Post by linux phreak on 2008-02-28
No problem.You have helped me through the difficult part.So should i create a new thread on adding things to start up in xubuntu.

---

### Post by linux phreak on 2008-02-28
Here is a screenshot of what i made with help from you
[[IMG]http://img205.imageshack.us/img205/1931/screenshotjq1.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotjq1.png)

---

### Post by loudnlownoma on 2008-02-28
> **linux phreak said:**
> No problem.You have helped me through the difficult part.So should i create a new thread on adding things to start up in xubuntu.

May not be a bad idea.  tried a few different searches and that link was about the best I could find, most everything else was just the same instructions I provided earlier, which obviously won't work.  :(  But that is a good attitude, at least the hard part is done...lol.  And looking good in that screenshot!  Just be careful, I've found myself going to change one or two things just to mix it up and next thing I know I have spent a couple hours reconfiguring it.  Conky can be very addicting!  lol

---

### Post by linux phreak on 2008-02-28
yes conky can be addictive and i can also use it as a showoff tool to friends who use windows.Thanks loudnlownoma. I must  take lunch break.Bye,

---

### Post by loudnlownoma on 2008-02-29
Glad I could help!  :)   I found it to be a good way to show just one of the ways Ubuntu is awesome!  Compiz is cool and all, but I have a bunch of friends that were more intrigued by the power of Conky and what it can do with so little impact on your hardware with it's options, and the ease of configuring it to be exactly what you want, and was surpised how many people have been more drawn in with that than some of the flash offered by Compiz or other programs.  Definitely a good tool and glad I could help get yours working right for ya!

---

