---
title: "Conky Disk Usage Display Error"
date: 2010-04-10
forum: Desktop Environments
---

### Post by bootbat on 2010-04-10
Hello Friends,

I was re-configuring my .conkyrc file today and am facing issues displaying the correct disk usage. Here is the file:

[HTML]
# set to yes if you want Conky to be forked in the background
background no
# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-35-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
#on_bottom yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
#xftalpha 0.15

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or overide
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8 no

# border margins
window.border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 28

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
use_spacer right no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
text_buffer_size 2048

TEXT
${time %A %d %B %Y}${color}${font}, ${time %H:%M}${font}
${color}System Information
${hr}
 
${font}${voffset -10}${color}${exec lsb_release -d | sed 's/.*:\s*//'}${font}
${color green}${exec whoami} ${color}@ ${color green}$nodename$color
$sysname $kernel ($machine)
${font}${color lightgrey}Internal Temp:${color light grey} ${acpitemp}°C
# ${font}${color lightgrey}CPU Temp:$alignr ${color light grey} ${ibm_temps 0}°C
# ${font}${color lightgrey}GPU Temp:$alignr ${color light grey} ${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c50-51}°C
# ${font}${color lightgrey}Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,160 BAT0}
# ${color lightgrey}$alignc Uptime:$color $uptime
${hr}
${color}Uptime:$color $uptime ${color}- Load:$color $loadavg
${color}CPU Usage:${color} $cpu% ${cpubar}
${color}${cpugraph 88aadd 88aaee}
${hr}
${color}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color}Processes:$color $processes  ${color}Running:$color $running_processes
${hr}
${color}Networking:
 Down:${color} ${downspeed eth0} k/s${color} ${offset 80}Up:${color} ${upspeed eth0} k/s
${color}${downspeedgraph eth0 32,150 88aadd 88aaee} ${color}${upspeedgraph eth0 32,150 88aadd 88aaee}
${hr}
${color}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar /home}
${hr}
${color}Name              PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${hr}
[COLOR="Red"]${color}Disk Usage:
${color}Drive: %Free                          Amount Used
${color}linux: ${fs_free_perc /dev/sdb1}%   ${color orange}${fs_bar 6 /dev/sdb1}
${color}xp:    ${fs_free_perc /dev/sda1}%   ${color blue}${fs_bar 6 /dev/sda1}[/COLOR][/HTML]


It does not display the correct usage information (It says that 99% of both Linux and XP disks are available) and the bars do not show up anything. I tried tweaking some but am now short of ideas. Running the following command gives the actual usage:

[HTML]:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             36843208  30540868   4430772  88% /
/dev/sda1             39110208  26286372  12823836  68% /media/FA3CBDBD3CBD756[/HTML]


Not sure where I am going wrong. Any pointers will be appreciated.

---

### Post by leef on 2010-04-10
[HTML]Have you tried removing the [COLOR="Red"] and [/COLOR] parts?[/HTML]

---

### Post by bootbat on 2010-04-11
Thanks for your response. I was just trying to highlight the relevant entries within those quotes while posting. The actual file does not have those quotes.

---

### Post by stinkeye on 2010-04-11
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             36843208  30540868   4430772  88% [COLOR="Red"]/[/COLOR]
/dev/sda1             39110208  26286372  12823836  68% [COLOR="#ff0000"]/media/FA3CBDBD3CBD756[/COLOR]

Try using the highlighted parts(where it's mounted)
eg```
${color}xp:    ${fs_free_perc /media/FA3CBDBD3CBD756}
```

---

### Post by georgemc on 2010-04-11
This might help.

I am using the directory names and not the device names in .conkyrc.  When I substitute the directoy names with device names then conky does not display properly or crashes.  I suspect file access issues.  Any way, my root partition is on /dev/sda1.

My original .conkyrc entries:

```

${color orange}Disk Free Space ${hr 2}$color
Root: ${goto 65} ${fs_free_perc[COLOR=Red] /[/COLOR]}% ${goto 100}${fs_bar 6 /}$color
Home: ${goto 65} ${fs_free_perc [COLOR=Black]/home[/COLOR]}% ${goto 100}${fs_bar 6 /home}$color

```Works and displays percentages properly.

Now when I do this:

```

${color orange}Disk Free Space ${hr 2}$color
Root: ${goto 65} ${fs_free_perc [COLOR=Red]/dev/sda1[/COLOR]}% ${goto 100}${fs_bar 6 /}$color
Home: ${goto 65} ${fs_free_perc [COLOR=Black]/home[/COLOR]}% ${goto 100}${fs_bar 6  /home}$color

```Then the percentages on my "root" directory/partition was displayed as 99%.

Hope this helps.

George

---

### Post by ajgreeny on 2010-04-11
> **stinkeye said:**
> Try using the highlighted parts(where it's mounted)
eg```
${color}xp:    ${fs_free_perc /media/FA3CBDBD3CBD756}
```

Is that usually needed in the conkyrc?   Here's the appropriate part of mine, which looks almost the same as the OP's, and it works with no problem at all.
```
${color #7CAFCE}sda1
${color #7CAFCE} Root ${color white}${fs_used_perc /}% ${color #7CAFCE}${fs_bar /}
$alignr ${color white}${fs_used /}/${fs_size /}
${color #7CAFCE}sda2
${color #7CAFCE} Home ${color white}${fs_used_perc /home}% ${color #7CAFCE}${fs_bar /home}
$alignr ${color white}${fs_used /home}/${fs_size /home}
```
Why should the UUID be needed in conkyrc?

---

### Post by stinkeye on 2010-04-11
> **ajgreeny said:**
> Is that usually needed in the conkyrc?   Here's the appropriate part of mine, which looks almost the same as the OP's, and it works with no problem at all.
```
${color #7CAFCE}sda1
${color #7CAFCE} Root ${color white}${fs_used_perc /}% ${color #7CAFCE}${fs_bar /}
$alignr ${color white}${fs_used /}/${fs_size /}
${color #7CAFCE}sda2
${color #7CAFCE} Home ${color white}${fs_used_perc /home}% ${color #7CAFCE}${fs_bar /home}
$alignr ${color white}${fs_used /home}/${fs_size /home}
```
Why should the UUID be needed in conkyrc?
It's not needed. 
You are only showing your home and root directories,
whereas bootbat is also showing his xp partition.
Which, because he hasn't labeled it, shows up as /media/FA3CBDBD3CBD756

When I df in terminal
```
$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdc1             30961664   4185648  25203256  15% /
udev                   1030816       352   1030464   1% /dev
none                   1030816       176   1030640   1% /dev/shm
none                   1030816       288   1030528   1% /var/run
none                   1030816         0   1030816   0% /var/lock
none                   1030816         0   1030816   0% /lib/init/rw
/dev/sda5            118997832  44337792  68515984  40% /media/UBUP
/dev/sdc3             44924308  21450164  21192112  51% /home
/dev/sr0               7375496   7375496         0 100% /media/cdrom0
/dev/sda1            123218516  71134308  52084208  58% [COLOR="#ff0000"]/media/XP[/COLOR]
```

---

### Post by bootbat on 2010-04-13
Thank you all for your assistance.

Changing /dev/sda1 to /media/FA3CBDBD3CBD756 did not bring the desired result. It instead started showing the %Free figure to 99% but also showed the usage bar as 99%!! Under terminal, it said that the file/directory was not available. I am confused:-)

Any other ideas will be appreciated:-)

Thanks

---

### Post by stinkeye on 2010-04-13
> **bootbat said:**
> Thank you all for your assistance.

Changing /dev/sda1 to /media/FA3CBDBD3CBD756 did not bring the desired result. It instead started showing the %Free figure to 99% but also showed the usage bar as 99%!! Under terminal, it said that the file/directory was not available. I am confused:-)

Any other ideas will be appreciated:-)

Thanks
Is your XP partition mounted?
What does it show up as in your nautilus places sidebar?
Click on it and use whatever shows up in your location bar.
If that doesn't work it might be the permissions used when mounting,
which I'm not confident in giving advice about.

---

### Post by bootbat on 2010-04-14
Thank you &#65279;stinkeye,

I am sorry to have caused this confusion. My bad....The drive is actaully 

[PHP]/media/FA3CBDBD3CBD756B[/PHP]

and not

[PHP]/media/FA3CBDBD3CBD756[/PHP].

I changed it and it started working fine. It shows the correct usage now. I wonder how I could have missed it all along. Apologise for my mistake and thank you for guiding me all along. I just have a small stupid question that you perhaps can answer. How to label this drive appropriately? 

BTW I have closed the thread as solved already. Thanks again!!

---

### Post by stinkeye on 2010-04-14
Use this guide which requires you to install ntfsprogs
[**_[COLOR="DarkRed"]https://help.ubuntu.com/community/RenameUSBDrive#NTFS[/COLOR]_**]("https://help.ubuntu.com/community/RenameUSBDrive#NTFS")
Click on NTFS in the contents at the top right.
```
sudo apt-get install ntfsprogs
```

Your XP partition may have to be unmounted to make changes.

From what you posted before:
To check your current label
```
sudo ntfslabel /dev/sda1
```


To change your label on sda1 to XP
```
sudo ntfslabel /dev/sda1 XP
```

---

### Post by bootbat on 2010-04-17
Hi Stinkeye,

I followed your instructions and was able to get the label changed. I wanted to drop a quick note and thank you for all your assistance in resolving the issue. I appreciate it and hopefully someday I will have some experience to assist in one of yours:-)

---

