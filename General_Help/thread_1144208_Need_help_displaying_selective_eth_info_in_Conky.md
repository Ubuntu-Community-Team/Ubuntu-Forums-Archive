---
title: "Need help displaying selective eth info in Conky"
date: 2009-04-30
forum: General Help
---

### Post by MikeBrown on 2009-04-30
The title does sound misleading, I know. I apologize for that. 

Here is my question:

I have conky on my desktop and use it to display the typical information: Eth up/down speed, a cpu graph, IP, etc. 

What I want to do is display only the eth that is sending/receiving information (only the one that is being used) so it auto-detects whether I'm on wireless or plugged in to a router and displays information accordingly. 

I have attached my workaround for the time being which actually has one for wireless and one for wired, but I would like to drop the extra bars and not have to "gedit .conkyrc" if I switch from wireless to "hard wiring" (plugging in) yet still display the IP, up/down speed and transfer information. 

I also have included my conky script for help (or whatever you need) 

Any help would be much appreciated! Thanks! 

Conky Script:
```


# THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5
Maximum_width 300

# Maximum size of buffer for user text, i.e. below TEXT line.default is 16384 bytes
max_user_text 90000

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #FF0000}$nodename$color      ${color #828282}$sysname $kernel on 
$machine$color
   ${color #FF0000}Batt:$color   ${battery}

${color #0000FF}PROCESSING$color
   ${color #FF0000}CPU usage
   ${color #FF0000}${cpugraph 0000FF FF0000}
                           
${color #0000FF}DATA USAGE$color
   ${color #FF0000}RAM:$color     ${color #FF0000}$memperc%         ${color 
#FF0000}${membar 5}${color}

${color #0000FF}HDD USAGE$color
   ${color #FF0000}/:$color       ${color #FF0000}${fs_used_perc /}% used    $fs_used   ${color 
#FF0000}${fs_bar 6 /}$color

${color #0000FF}NETWORK$color
   ${color #FF0000}IP on eth0 $alignr ${addr eth0}
   ${color #FF0000}Down: ${downspeed eth0}k/s            ${color #FF0000}Up: ${upspeed eth0}k/s
   ${color #FF0000}${downspeedgraph eth0 25,135 0000FF FF0000} $alignr$color  ${color #FF0000}${upspeedgraph eth0 25,135 0000FF FF0000}$color
   ${color #FF0000}Total Down:  ${totaldown eth0}    ${color #FF0000}Total Up: ${totalup eth0}
   
   ${color #FF0000}IP on eth1 $alignr ${addr eth1}
   ${color #FF0000}Down: ${downspeed eth1}k/s            ${color #FF0000}Up: ${upspeed eth1}k/s
   ${color #FF0000}${downspeedgraph eth1 25,135 0000FF FF0000} $alignr$color  ${color #FF0000}${upspeedgraph eth1 25,135 0000FF FF0000}$color
   ${color #FF0000}Total Down:  ${totaldown eth1}    ${color #FF0000}Total Up: ${totalup eth1}   
${color #0000FF}CALENDAR$color
   ${color #FF0000}${head /home/exeter/gcal.txt 50 50 }$color

${color #0000FF}TODO$color
${color #FF0000}${execi 30 cat head /home/exeter/todo.txt 50 50 | fold -w80 }

${color #0000FF}RFR Shopping List$color
${color #FF0000}${execi 30 cat head ~/rfrshopping.txt | fold -w80 }

${color #0000FF}New Mx adds$color
${color #FF0000}${execi 30 cat head ~/newmx.txt | fold -w80 }

${color #0000FF}Want$color
${color #FF0000}${execi 30 cat head ~/want.txt | fold -w80 }
```

---

### Post by bostonaholic on 2009-04-30
I have done this on my home machine.  I'll take a look at my .conkrc file when I get home after work.

It does exactly as you want.  It'll show up/down and ip specifics and will change if you change from wired->wireless or visa versa.

---

### Post by MikeBrown on 2009-04-30
Sweet, thanks alot!

---

### Post by MikeBrown on 2009-05-04
[In order to preserve the freshness date of this post, I have BUMPed...]

Any help would be appreciated! Thanks!

---

### Post by bostonaholic on 2009-05-04
Sorry dude, I've been so busy.  Here ya go (just the network portion of my .conkyrc.  Let me know if you have any quesions.

```
${color gold}NETWORK ${hr 2}
${alignc}${color red}${if_existing /sys/class/net/eth0/operstate up}WIRED${else}${if_existing /sys/class/net/wlan0/operstate up}Wi-Fi$endif$endif
${offset 5}${color cornflowerblue}Hostname${color}${alignr}$nodename
${offset 5}${color cornflowerblue}User${color}${alignr}${execi 1000 whoami}
${offset 5}${color cornflowerblue}Public IP${alignr}${color}${execi 1000 wget -O - http://whatismyip.org/ | tail}
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Private IP$color$alignr${addr eth0}$else${if_existing /sys/class/net/wlan0/operstate up}Private IP$color$alignr ${addr wlan0}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Down: $color${downspeed eth0} k/s${color cornflowerblue}{$alignr}Total: $color${totaldown eth0}$else${if_existing /sys/class/net/wlan0/operstate up}MAC $color$alignr ${wireless_ap wlan0}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${downspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/wlan0/operstate up}${wireless_essid wlan0}${alignr}${wireless_bitrate wlan0} ${wireless_link_qual_perc wlan0}%$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Up: $color${upspeed eth0} k/s${color cornflowerblue}${alignr}Total: $color${totalup eth0}$else${if_existing /sys/class/net/wlan0/operstate up}Down: $color${downspeed wlan0} k/s${color cornflowerblue}$alignr Total: $color${totaldown wlan0}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${upspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/wlan0/operstate up}${downspeedgraph wlan0 000000 ffffff}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/wlan0/operstate up}Up: $color${upspeed wlan0} k/s${color cornflowerblue}${alignr}Total: $color${totalup wlan0}
${offset 5}${upspeedgraph wlan0 000000 ffffff}$endif
```

---

### Post by MikeBrown on 2009-05-04
Hey it's not a problem, I know stuff comes up. 

I do have a question though, the code you gave me only shows the following things: 

Hostname 
IP 
and user. 

No graphs are showing up at all. I cut and pasted directly over my original code so that none of it would be causing an error. I did notice that you have folder paths that are unfamiliar to me, could that be a reason that none of the graphs are showing? 

I did check, all the folder paths and such do exist on my machine except for the wlan0.

---

### Post by bostonaholic on 2009-05-04
> **MikeBrown said:**
> Hey it's not a problem, I know stuff comes up. 

I do have a question though, the code you gave me only shows the following things: 

Hostname 
IP 
and user. 

No graphs are showing up at all. I cut and pasted directly over my original code so that none of it would be causing an error. I did notice that you have folder paths that are unfamiliar to me, could that be a reason that none of the graphs are showing? 

I did check, all the folder paths and such do exist on my machine except for the wlan0.

Sorry, I forgot to mention, you will have to change the folder paths to reflect which points to your wireless connection and which points to your "plugged-in" connection.  In my */sys/class/net/* I acutally have 4 directories:

```
mboston@mboston01:/sys/class/net
> ls
eth0  eth1  lo  pan0

```

You'll want to check inside each of those directories for a file called 'operstate'.  You can view this file in your favorite text editor.  It will contain the state of that current connection.  For instance... when I am connected to the wire

```
mboston@mboston01:/sys/class/net
> more eth0/operstate 
up

```
which means the wireless connection is "down"
```
mboston@mboston01:/sys/class/net
> more wlan0/operstate 
down

```
When connected to wireless, the contents of these two files will be switched, *eth0/operstate* will say 'down' and *wlan0/operstate* will say 'up'

All that script does is check which file says 'up' and displays the appropriate date/graph.

Help any?

---

### Post by bostonaholic on 2009-05-04
Looking back at your original post, your .conkyrc file, you were using eth0 and eth1.  So I would then assume you should use */sys/class/net/eth0*/operstate and */sys/class/net/eth1*/operstate for your wired and wireless connections, respectively.

---

### Post by MikeBrown on 2009-05-04
I am not able to edit anything at the moment as I'm using a different computer, but I will check and let you know! Thanks alot!

---

### Post by MikeBrown on 2009-05-04
I did check for the file in each directory, and yes it does show up. I also searched and found that I also have the eth0 eth1 lo and pan0 folders. 

I tried to open up the operstate file but it gives me a "no such device" error.

Would it also be important to note that I copy and pasted your original code straight into my conky? 

I assumed that it was written in way that is pretty common. I have the same file structure in my system, but it could be that I need to change the paths. 

I am still playing with it, but nothing is giving me a positive result.

---

### Post by bostonaholic on 2009-05-04
> **MikeBrown said:**
> I did check for the file in each directory, and yes it does show up. I also searched and found that I also have the eth0 eth1 lo and pan0 folders. 

I tried to open up the operstate file but it gives me a "no such device" error.

Would it also be important to note that I copy and pasted your original code straight into my conky? 

I assumed that it was written in way that is pretty common. I have the same file structure in my system, but it could be that I need to change the paths. 

I am still playing with it, but nothing is giving me a positive result.

Basically you should replace every instance of *wlan0* with *eth1*.  That is if I'm correct in my assumption that when you're connected to LAN */sys/class/net/eth0/*operstate is 'up' and when you're connected to wireless */sys/class/net/eth1/*operstate is 'up'.

This should work for you if the above statement is true.
```
${color gold}NETWORK ${hr 2}
${alignc}${color red}${if_existing /sys/class/net/eth0/operstate up}WIRED${else}${if_existing /sys/class/net/eth1/operstate up}Wi-Fi$endif$endif
${offset 5}${color cornflowerblue}Hostname${color}${alignr}$nodename
${offset 5}${color cornflowerblue}User${color}${alignr}${execi 1000 whoami}
${offset 5}${color cornflowerblue}Public IP${alignr}${color}${execi 1000 wget -O - http://whatismyip.org/ | tail}
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Private IP$color$alignr${addr eth0}$else${if_existing /sys/class/net/eth1/operstate up}Private IP$color$alignr ${addr eth1}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Down: $color${downspeed eth0} k/s${color cornflowerblue}{$alignr}Total: $color${totaldown eth0}$else${if_existing /sys/class/net/eth1/operstate up}MAC $color$alignr ${wireless_ap eth1}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${downspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/eth1/operstate up}${wireless_essid eth1}${alignr}${wireless_bitrate eth1} ${wireless_link_qual_perc eth1}%$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Up: $color${upspeed eth0} k/s${color cornflowerblue}${alignr}Total: $color${totalup eth0}$else${if_existing /sys/class/net/eth1/operstate up}Down: $color${downspeed eth1} k/s${color cornflowerblue}$alignr Total: $color${totaldown eth1}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${upspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/eth1/operstate up}${downspeedgraph eth1 000000 ffffff}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth1/operstate up}Up: $color${upspeed eth1} k/s${color cornflowerblue}${alignr}Total: $color${totalup eth1}
${offset 5}${upspeedgraph eth1 000000 ffffff}$endif
```

---

### Post by MikeBrown on 2009-05-04
/facepalm 

Eureka! That worked! *happy dance* 

You rock dude! 

Tested on both wireless and "hard wired" (as I call it).

Works great! Thanks A Lot!

---

### Post by bostonaholic on 2009-05-05
> **MikeBrown said:**
> /facepalm 

Eureka! That worked! *happy dance* 

You rock dude! 

Tested on both wireless and "hard wired" (as I call it).

Works great! Thanks A Lot!

Awesome!  You're welcome.

---

### Post by MikeBrown on 2009-05-09
I have one final question: is there a way to delay the whatismyip command, because that takes a lot longer than it should and prevents conky from launching right away. 

I would like for conky to launch at start up and then load my programs THEN get the internet information. Is that possible?

---

### Post by bostonaholic on 2009-05-11
> **MikeBrown said:**
> I have one final question: is there a way to delay the whatismyip command, because that takes a lot longer than it should and prevents conky from launching right away. 

I would like for conky to launch at start up and then load my programs THEN get the internet information. Is that possible?

I had to start conky up later sometimes as well.  What you can do is in your startup script that starts conky
```
sleep 60 && conky;
```
So when conky is started, it will "sleep" (wait) 60 seconds before it runs conky.  You can adjust the '60' accordingly.

---

### Post by MikeBrown on 2009-05-11
roger, thanks again!

---

