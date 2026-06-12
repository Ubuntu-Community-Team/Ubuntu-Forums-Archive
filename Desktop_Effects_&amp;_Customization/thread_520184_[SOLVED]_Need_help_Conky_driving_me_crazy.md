---
title: "[SOLVED] Need help Conky driving me crazy"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by waldorsockbat on 2007-08-07
I have been working to get Conky to load at start up for 2 days now with no luck. I have got it to load 3 time so far. 1 with a delay of 10 next log in it vanished same for delays of 5 and 0.I have tried delays of 0 to 70. I am running Compiz/Fusion,AWN,Affinity and Emerald themes all of which load up and work flawlessly with nvidia driver installed by envy. I have read every Conky thread I can find and tried everything inthem with no luck. Below are my conky config and .conky_start.sh. Any help anyone can give will be greatly appreciated 

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

 Create own window instead of using desktop (required in nautilus)
own_window no

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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

.Conky_start.sh

#!/bin/bash
sleep 5 && conky

---

### Post by Happy_Man on 2007-08-07
Are you using GNOME? If so, change the first line from "own_window no" to "own_window yes". Perhaps that will work.

---

### Post by waldorsockbat on 2007-08-07
If I set it to yes the conky window stays on top of all open windows.

---

### Post by waldorsockbat on 2007-08-08
no ideas?

---

### Post by haricharan on 2007-08-08
try
```
use_xft yes
``` lemme attach my conky script too...maybe u can check with it....

---

### Post by waldorsockbat on 2007-08-08
Well it worked 1 time just like every other thing I have tried,as soon as I log out and log back in conky is gone again.That is the part that is driving me nuts, why does it only work until I log out and back in? I can make any change ,as in delete 1 word and type that same word in the same spot, save,log out ,log in and boom its there  until I log out again and then it doesnt load at startup..

But enough rambleing,thanks for the suggestion if you have any others I will be in your debt.

---

### Post by gavin72 on 2007-08-08
Try the following parameters in your conkyrc file :

```
#Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

Try and increase your delay to more than 5 seconds, as you need your window manager to have already loaded before conky starts.

Also you are missing a # before 
```

Create own window instead of using desktop (required in nautilus)
```
in your file.

---

### Post by waldorsockbat on 2007-08-08
OK now I have a whie box with garbled  text in it but at least it loads every time now. I  will post a screen shot later today when I get home from work.

---

### Post by waldorsockbat on 2007-08-08
Ok here is a screen shot of garbled conky

---

### Post by gavin72 on 2007-08-08
Your conkyrc looks really messed up.
Why don't you work from my file and modify with your needs.

You can find it , at my post on this page :

[http://ubuntuforums.org/showthread.php?t=281865&page=47](http://ubuntuforums.org/showthread.php?t=281865&page=47)

---

### Post by HarshReality on 2007-08-08
Hee is one for you.. since I added email checking it flags and then closes (doesnt even make it to an open state) but if I remove email it opens right up... can we do some sort of conditional statement if no net dont load the email....

I did notice the remark about delay, I dont see a setting for a timer of sorts so I could set it for @ 30 seconds after X loads completely...


[http://harrea.100webspace.net/Shot-1.png]("http://harrea.100webspace.net/Shot-1.png")

---

### Post by gavin72 on 2007-08-08
To get the delay, you need to make a separate shell file that will execute when you login.
Here's how:

Open Nautilus and create a new file with a .sh extension in your home directory (.conky_start.sh)

Right-Click that file and select the Properties Tab, and then check the box that says allow execution as program.

Open up the file in your favorite text-editor and paste the following :

```
#!/bin/bash
sleep 5 && conky
```

Replace 5 with however many seconds you need.

Then System->Preferences->Sessions

Startup Programs -> New

And put in the name of the file you created (.conkey_start.sh) as the command line.

Hope this helps.

---

### Post by HarshReality on 2007-08-08
I did try that and the whole of it stalled... ironically though when I removed the email area it pops up with no problem without a shell script ;)

---

### Post by waldorsockbat on 2007-08-08
It works now. After a reboot everything is fine, thanks for the help guys.
The reason I deleted the own window line was after install the conky window was just that a window that stayed on top of all others,why its not that way now I will leave to the much smarter than I here. Now I have hd temp working and just apt-get sensors to get cpu temp working, I came across a post in all the searches I did on how to get video card temp working also but I don't remember where it was. If anyone knows and would drop a link I would be grateful

---

### Post by drvista on 2007-09-14
To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

gedit .conky_start.sh

copy the code below and past into the file. Save and close

#!/bin/bash
sleep 10 && conky;

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Not using beryl so I changed it to sleep 2 && conky; Make sure the script is executable:

chmod a+x .conky_start.sh

Now, add it to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/>your user name/.conky_start.sh

---

