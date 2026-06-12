---
title: "Does anyone want to take a shot at this 'conkyrc' script for me? &quot;Lucid themed Conky&quot;"
date: 2010-05-07
forum: Desktop Environments
---

### Post by Rasa1111 on 2010-05-07
hi all, 

  I think I have my Lucid box really close to how I want it..
especially after I saw the Lucid themed conky in the May wallpaper thread.. 
 it is here..  [http://www.omgubuntu.co.uk/2010/05/easy-to-use-lucid-themed-conky-bar.html](http://www.omgubuntu.co.uk/2010/05/easy-to-use-lucid-themed-conky-bar.html)

 anyway.... 
I got it working, and I love how it looks and what it does... 

But it was made for a 1280x wide background.. and my monitors res. is 1024. 

 I have dabbled in my first [weak] conky script experience..
just trying to edit it....

and for the most part... I have got it to do what I wanted.. 
"fit my screen".  
well fit it does, and perfectly now.. [well not quite, but almost]
and it doesnt stretch to the bottom but thats ok. 

 However,  no matter what I do now in the script...
I cant get the time to move over to the proper place.
it stays over to the right, past the screens boundary so I cant see it. 

I thought I almost had it, but apparently not. lol

Here is the image by koleoptero, of what it *should* look like..
[http://farm5.static.flickr.com/4060/4583340135_9d53086832_o.png](http://farm5.static.flickr.com/4060/4583340135_9d53086832_o.png)

and the attached image of how mine currently looks@ bottom.

Ive never played with conky scripts in my life..
 and I have played with this for at least the last 3 hours and still cant get it quite right..

I was wondering,  If I provide the original script...
Could one of you conky pros help me get it right?

This is the unedited script....  
Would anyone bored enough,  or with a few free minutes and a loving heart care to help a n00b is is willing and eager to learn how to get this right? lol

 I have even been looking over conky tutorials...
but I still am not grasping what I need to do with this script to get it right for my screen. 

 I am poor, but I can pay you in good karma if that's cool? lol

> # Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1440 0

# Conky positioning.
alignment bottom_left
gap_x 0
gap_y 30

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1280x180}
${voffset 20}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${goto 1024}Time and Date:${font}${color}
${voffset 6}${goto 256}System (/):${goto 380}${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 768}CPU: ${goto 868}${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18} ºC${goto 1024}${time %H:%M}  ${time %d/%m/%Y}
${goto 15}Kernel: ${goto 100}${kernel}${goto 380}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 768}Hard Disk: ${goto 868}${execi 4 sensors | grep -A 0 'temp1' | cut -c15-18} ºC${goto 1024}${time %A}, ${time %d} ${time %B} ${time %Y}
${goto 15}CPU: ${goto 100}${cpubar cpu1 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${goto 380}${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup eth0}
${goto 15}RAM: ${goto 100}${membar 10,100}${font Droid Sans:style=Bold:size=9}  $memperc%${font}${goto 380}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown eth0}
${goto 15}SWAP:${goto 100}${swapbar 10,100}${font Droid Sans:style=Bold:size=9}  $swapperc%${font}${goto 512}Local IP: ${goto 612}${addr eth0}
${goto 15}Uptime: ${goto 100}${uptime}${goto 512}Public IP: ${goto 612}${execi 10800 ~/.scripts/ip.sh}
anyone reading or willing to take a shot at this for me...
your insight would be truly appreciated...
and I will retain whatever taught for future use, I promise.  lol :KS

 Many thanks in advance. <3

edit: ohh, before I started editing it, the ubuntu logo to the right wasnt even visible.
 Now see how Ive gotten "Time and Date" to show to the right...
[not visible before my editing attempts either]

but the actual clock and date are still way off the screen..
[I also wouldnt mind getting rid of the 'temperature'] if possible? 
but if not, the clock fixed would be super. lol :)

So..  I need the time moved over to the left to be visible...
that is the big thing... 
and removing the CPU and HDD temp isnt much of a big deal... but would be cool. 
I would be more than happy with just the time and date in the right place though. 
?

---

### Post by kerry_s on 2010-05-07
very time consuming, i want a cookie! :lolflag:

the basics are there, i had to change the font, links to scripts & eth0, to get it to run. so you'll have to fix those, but the size should be right, my screens 1024x768.

```

# Locale, fonts and font sizes.
use_xft yes
xftfont Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 10
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1000 0

# Conky positioning.
alignment bottom_left
#gap_x 0
#gap_y 0

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1000x180}
${voffset 20}${font Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${font}${color}
${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 768}CPU: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 768}Hard Disk: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}CPU: ${cpubar cpu1 10,100}${font Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup wlan0}
${goto 15}RAM: ${membar 10,100}${font Sans:style=Bold:size=9}  $memperc%${font}${goto 256}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown wlan0}${goto 768}${font Sans:style=Bold:size=12}${color0}Time and Date:${font}${color}
${goto 15}SWAP: ${swapbar 10,100}${font Sans:style=Bold:size=9}  $swapperc%${font}${goto 512}Local IP: ${goto 612}${addr wlan0}${goto 768}${time %H:%M}  ${time %d/%m/%Y}
${goto 15}Uptime: ${uptime}${goto 512}Public IP: ${goto 612}${execi 10800 echo "N/A"}${goto 768}${time %A}, ${time %d} ${time %B} ${time %Y}


```

---

### Post by Rasa1111 on 2010-05-07
:D haha wow, niice! 
niice job,  thank you! 
how bout' a bunch? lol
[IMG]http://www.smileycookie.com/images/cookies.jpg[/IMG]


 Youre right, the placement of everything is great now, Im impressed! lol

 now for the 'bad news' that i feel bad for having.. lol :(
 > i had to change the font, links to scripts & eth0, to get it to  run. so you'll have to fix those,

  I dont think the font is any matter, that is cool with me, 
but this is really the first time Ive ever even looked at a conky script...
and the only reason I was able to change 
anything in the first place [resolution] was because 
I saw  the "1280x180", and i knew that is the size it was written for,
 so I took a chance at changing it and it 'worked'.. 
:/ lol

I truly am lost on how I would fix those things you mentioned. 
font~?links to scripts?~ and eth0. 

 Im looking at both the original script ,and your script..
 trying to find the differences that I would need to revert back to everything but the size and placement...  but my eyes are not catching it... lol...  
maybe Im tired or something...
or just too simple yet... lol

tomorrow [ok today] is another day... 
i have a feeling it might be *the* day it will get fixed...lol
i will look more after i get back from dreamland...

 thanks soo much, 
I really appreciate your time and work!
really niice, :D Praises * <3

---

### Post by kerry_s on 2010-05-07
for eth0, just use the edit-> replace in the text editor.
find what: wlan0
replace with: eth0

i replaced:
~/.scripts/ip.sh
with 
echo "N/A"

i replaced:
sensors | grep -A 0 'temp1' | cut -c15-18
with
cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'

---

### Post by bra|10n on 2010-05-07
> **Rasa1111 said:**
> 

tomorrow [ok today] is another day... 
i have a feeling it might be *the* day it will get fixed...lol
i will look more after i get back from dreamland...


Hi Rasa,
You surely don't realise how significant this quote will become after conky has finished with you! ;)

A little resource link that I think will come in handy for you...
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Rasa1111 on 2010-05-07
> **kerry_s said:**
> for eth0, just use the edit-> replace in the text editor.
find what: wlan0
replace with: eth0

i replaced:
~/.scripts/ip.sh
with 
echo "N/A"

i replaced:
sensors | grep -A 0 'temp1' | cut -c15-18
with
cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'


:guitar: Yes!  Thank you!! 
It took me a minute to understand that whole "find and replace with" function..
but that was super helpful!  haha, wow, you are awesome kerry! :KS+10
 Many many thanks!
 Check it out me new screenshot..  woot! 

@bra|10n~  haha, thank you! 
I believe it... :lol:

 great link, thanks!
I remember looking at it awhile ago and being intrigued by all the screenshots and long, weird scripts that made them happen. lol :lolflag:

 very cool, Thanks soo much!!

---

### Post by kerry_s on 2010-05-07
it's very close, your temps are missing & there's overlap(see pic)

```
${goto 768}CPU: ${goto 868}${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}
```

i would say change "goto 768" to "goto 770" on both lines, that should help.

use the edit->replace

---

### Post by Rasa1111 on 2010-05-07
> **kerry_s said:**
> it's very close, your temps are missing & there's overlap(see pic)

```
${goto 768}CPU: ${goto 868}${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}
```i would say change "goto 768" to "goto 770" on both lines, that should help.

use the edit->replace


ohh kerry... 
you keep amazing me.. lol <3

 I wondered how to fix that lil overlap! lol

I changed it from 768 to 770, and it still overlapped a bit,
so I moved up by 2's Until i got to 776~ which gave me this~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155868&stc=1&d=1273234317[/IMG]

 amazing! haha
 thanks a million!
lots of good Karma to you friend. <3

---

### Post by kerry_s on 2010-05-07
> **Rasa1111 said:**
> ohh kerry... 
you keep amazing me.. lol <3

 I wondered how to fix that lil overlap! lol

I changed it from 768 to 770, and it still overlapped a bit,
so I moved up by 2's Until i got to 776~ which gave me this~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155868&stc=1&d=1273234317[/IMG]

 amazing! haha
 thanks a million!
lots of good Karma to you friend. <3

how come there's no temps though? do you have that sensors program installed? i think it's "lm-sensors".

---

### Post by Rasa1111 on 2010-05-07
> **kerry_s said:**
> how come there's no temps though? do you have that sensors program installed? i think it's "lm-sensors".

 I am not sure? 
The other day I tried to get them working,
and just looked in synaptic... and I do seem to have installed lm-sensors~
but still no temps. lol

  synaptic screen attached. 

 I followed some instruction I found through 'OMG Ubuntu", with some terminal commands... and at first I thought it would be fruitful... 
then after about 4 different scans for sensors of different kinds...
the last 'check' that came up said that it "should be safe" but might be risky"..
so I stopped and didnt go any further.   :(  lol

It would be cool to have them working though.  :KS

 thanks again <3

---

### Post by kerry_s on 2010-05-07
can you paste those 2 lines from your conkyrc so i can look at, please turn off the word wrap before you copy, it's easier to read on 1 line.

---

### Post by Rasa1111 on 2010-05-07
> **kerry_s said:**
> can you paste those 2 lines from your conkyrc so i can look at, please turn off the word wrap before you copy, it's easier to read on 1 line.

 Im sorry, what 2 lines? 
I am also not sure how to turn off 'word wrap'.....
I will go look...
I am not sure what 2 lines you mean though.
Sorry for being simple. lol

---

### Post by kerry_s on 2010-05-07
> **Rasa1111 said:**
> Im sorry, what 2 lines? 
I am also not sure how to turn off 'word wrap'.....
I will go look...
I am not sure what 2 lines you mean though.
Sorry for being simple. lol

sorry, the 3rd & 4th under "TEXT"

---

### Post by Rasa1111 on 2010-05-07
> **kerry_s said:**
> sorry, the 3rd & 4th under "TEXT"

ok, not sure if these lines are what you meant~ 
[PHP]512}Network:${goto 776}Temperatures:${font}${color}
${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512[/PHP]but they are the 3rd and 4th line under TEXT.
[unless I am confused... again] lol

I also tried to figure out the 'turn off word wrap' 
(im guessing that means a forum feature? I cant find it in Gedit)

I tried the 3 different buttons [to the right of the [quote] icon]..
but nothing I did made it appear as one line...
So im not sure what to do there. 
Im sorry. 

 thanks for still helping me. :)

---

### Post by kerry_s on 2010-05-08
yeah, wordwrap is in gedit, look under view or preferences, sorry i'm not using gnome, so no gedit installed, on mine it's under options in leafpad. anyways just go ahead do it your way, copy everything after "Text" to the bottom of the page & i can straighten it out in my editor.

---

### Post by Rasa1111 on 2010-05-08
> **kerry_s said:**
> yeah, wordwrap is in gedit, look under view or preferences, sorry i'm not using gnome, so no gedit installed, on mine it's under options in leafpad. anyways just go ahead do it your way, copy everything after "Text" to the bottom of the page & i can straighten it out in my editor.

cool thanks!
got it... :mrgreen:

ohh, that does make it easier to understand/read! lol :)

here she is..

```
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1030x151}
${voffset 20}${font Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 776}Temperatures:${font}${color}
${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}CPU: ${cpubar cpu1 10,100}${font Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup eth0}
${goto 15}RAM: ${membar 10,100}${font Sans:style=Bold:size=9}  $memperc%${font}${goto 256}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown eth0}${goto 776}${font Sans:style=Bold:size=12}${color0}Time and Date:${font}${color}
${goto 15}SWAP: ${swapbar 10,100}${font Sans:style=Bold:size=9}  $swapperc%${font}${goto 512}Local IP: ${goto 612}${addr eth0}${goto 776}${time %H:%M}  ${time %m/%d/%Y}
${goto 15}Uptime: ${uptime}${goto 512}Public IP: ${goto 612}${execi 10800 ~/.scripts/ip.sh}${goto 776}${time %A}, ${time %d} ${time %B} ${time %Y}
```

thanks!! :KS

---

### Post by kerry_s on 2010-05-08
okay, you got what i put, so change those to lines:

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 

```

to these ones:

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU: ${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk: ${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}

```

sorry, thats my fault i don't have sensors installed, so i used a different command to read it straight from acpi file.

---

### Post by Rasa1111 on 2010-05-08
> **kerry_s said:**
> okay, you got what i put, so change those to lines:

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk: ${execi 4 cat /proc/acpi/thermal_zone/THRM/temperature | sed -e 's/temperature://'} 

```to these ones:

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU: ${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk: ${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18}

```sorry, thats my fault i don't have sensors installed, so i used a different command to read it straight from acpi file.

no apologies. :)
I did it and the temps still wouldnt appear. 
I really dont think I have censors installed either. 
everything Ive done comes back and says no censors, or something very close to it. lol

is there a simple way to remove that whole "temperature" section altogether?
Ive tried a few things the past couple days but never get it quite right, and always gotta revert. :lol:

thanks soo much, 
this is a good example of why the linux/ubuntu community is soo amazing.. 
people like you. 
thanks again! :)

---

### Post by kerry_s on 2010-05-08
alright lets check, 
press-> **alt+f2**
type-> **hardinfo**

click sensors & see if you have anything there
if somethings there then we just got to get at it.

should look like this

---

### Post by Rasa1111 on 2010-05-08
> Could not open location 'file:///home/ahmose/hardinfo
Error stating file '/home/ahmose/hardinfo': No such file or directoryhmmm...
guess I dont have that either? lol

---

### Post by kerry_s on 2010-05-08
wth? did you press **alt+f2** ?
it should give you a run dialog.

---

### Post by Rasa1111 on 2010-05-08
oh yeah.. sorry.., I get that when I hit alt f2, 
but when i type hardinfo into it, the error comes back.
I dunno..?

---

### Post by kerry_s on 2010-05-08
weird, try it in terminal, just type "hardinfo" & hit enter.
i'm pretty sure it's part of the standard install.

---

### Post by Rasa1111 on 2010-05-08
ohh i see, 
it was something i needed to install/a program.. duh.
but yea, it wasnt installed, so i did just install it..

and yep.. it doesnt show anything... 
lol... i dont know.. O_o 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155996&stc=1&d=1273305598[/IMG]

---

### Post by kerry_s on 2010-05-08
bummer. i think it would just be best to remove the command so nothing is run.

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU:
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk:

```

---

### Post by Rasa1111 on 2010-05-08
> **kerry_s said:**
> bummer. i think it would just be best to remove the command so nothing is run.

```

${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 776}CPU:
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 776}Hard Disk:

```

cool, thanks. :)

---

### Post by Rasa1111 on 2010-05-08
Ok, I finally got the "Temperature:" removed. lol :)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156085&stc=1&d=1273347930[/IMG]

 all I need now [not really ,but would be cool] is to move the "Time and Date:" up a tad, maybe to be aligned with Network:?

easy enough? or a pita? lol :)
<3

---

### Post by kerry_s on 2010-05-08
> **Rasa1111 said:**
> Ok, I finally got the "Temperature:" removed. lol :)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156085&stc=1&d=1273347930[/IMG]

 all I need now [not really ,but would be cool] is to move the "Time and Date:" up a tad, maybe to be aligned with Network:?

easy enough? or a pita? lol :)
<3


you'll get it, just remember to turn off the word wrap so you can see each line in order. put the time & date where temperature was, then just cut & paste the dates on the end of the 2 lines under the temperature line.

---

### Post by Rasa1111 on 2010-05-08
woot! :)

 I changed the time from 24 hour to 12 hour to.
and a couple other lil things. 
 I am missing my up/down speeds now though... hmm
lol

 Ive also been trying for the last hour [maybe more] to change color/bold of the actual Time and day/month. 
But every time it seems to change the color of everything on its 'level' and below it. :lol:

I actually understand [more so] how it is setup and works now..
but still cant figure this lil thing out yet... lol

 Thanks allot, Ive learned a bunch from you. :KS

---

### Post by kerry_s on 2010-05-08
you just need to enclose(? can't think right word) the font.

```
**${font Sans:style=Bold:size=9}**  the part you want  **${font}**
```

---

### Post by Rasa1111 on 2010-05-09
> **kerry_s said:**
> you just need to enclose(? can't think right word) the font.

```
**${font Sans:style=Bold:size=9}**  the part you want  **${font}**
```


cool, got it. :) thanks. 

Ive been trying to get my Upload/Download bars/graphs to show back up for the last couple hours but nothing is working. lol
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156148&stc=1&d=1273386403[/IMG]
other than that it is great!

 this stuff is actually kinda fun.. though confusing as he||. 
lol,  the more I stare at it the more it makes sense though. 

Thanks for the lessons. :P

---

### Post by kerry_s on 2010-05-09
your welcome, you can take a look at the man page, it might help you understand or confuse you more.
in terminal-> **man conky**

try this:
```
Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}
Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}
```

---

### Post by Rasa1111 on 2010-05-09
> **kerry_s said:**
> your welcome, you can take a look at the man page, it might help you understand or confuse you more.
in terminal-> **man conky**

try this:
```
Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}
Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}
```


awesome , thank you :mrgreen:

Ive got my 'Kernal" and "System" back also..
that i used from the original script. 

Question~ underneath CPU: and RAM: 
there is usually the "Uptime: and SWAP"..
I did have the first row lined up under the "Ubuntu" text..
without the large gap bewteen them..
 but the more I edit things..
the more things move to weird places.. lol

So, Uptime and SWAP are now 'too low' along with the rest of the first row... so I purposely deleted the SWAP after that, as it kept disappearing anyway... [and im not sure what SWAP actually is] lol,  but the Uptime also started disappearing and 'moving down', out of the 'frame'. 

How can I move just the first row back up?
Kernal:
CPU:
RAM:
SWAP:
Uptime:

*confused*

here is the bottom part of the script if that will help?
(I know its kind of a 'mess' i think.. 
especially far over to the right... *hides face*. lol, but it seems to work, I dont know.:confused: 
any idear? lol 
```
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1030x147}
${voffset 20}${font Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 776}${font}${color}${font Sans:style=Bold:size=12}${color0}   Time and Date:${font}${color}
${voffset 6}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 768}
${goto 15}Kernel: ${kernel}${goto 256}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 768}          ${font Sans:style=Bold:size=13}${color ffffff} ${time %I:%M %p }${font}${color} 
${goto 15}CPU: ${cpubar cpu1 10,100}${font Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup eth0}                                     ${time %A ~ %b %d}                                                                   
${goto 15}RAM: ${membar 10,100}${font Sans:style=Bold:size=9}  $memperc%${font}${goto 256}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown eth0}${goto 776}       
${goto 15} Uptime: ${uptime}${goto 512}
```

if not, i can leave it like this, 
i am happy with it. :)
like i said... im not sure what SWAP even is [havent asked google yet]
and i can live without knowing my 'uptime' i guess. lol
Just knowing it's 'unfinished' still though, bugs me a little. :lol:
[IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]
<3

---

### Post by kerry_s on 2010-05-09
with conky you got to watch spaces, it adds that in. put your mouse at the beginning of the line & hit the "end" key, it should jump to the end of the line, if there's empty space backspace to remove.

it looks like your making it narrower then the text(1030x147) which is causing the drop offs. you can try making the font smaller to fit in the space or make the space fit.

in case you don't know you can make the changes while conky is running, when you save it will show in the next refresh, so you can adjust right away.

---

### Post by Rasa1111 on 2010-05-09
nice, thanks. 
yeah thats how Ive been doing it, just edit the script and hit save and watch what it looks like upon refresh. lol

 Ok, I think ive reached the limits of my 'can-do' for the present. lol
Here is what Ive gotten....

 Thanks again for all your help, 
i really have learned allot! 
[well, compared to what i knew a few days ago, allot!] lol :P

I will give you a break for awhile, 
and I will start getting involved with some of the conky threads themselves. lol

  You rock, kerry! :KS  <3

---

### Post by kerry_s on 2010-05-10
that looks pretty frickin good to me, nice job!

---

### Post by Rasa1111 on 2010-05-10
> **kerry_s said:**
> that looks pretty frickin good to me, nice job!

aw thanks!! :mrgreen: 
i appreciate it!

however.. you might not say the same if you saw the actual script... :lol:
it really is all over the place! haha

check it out..
especially *way* over to the right.. :lol:
but somehow.. it works? lol I dunno.

```
# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1030x147}  
${voffset 20}${font Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 776}${font}${color}${font Sans:style=Bold:size=12}${color0}   Time and Date:${font}${color}
${voffset 6} 10.04 ,Kernel: ${kernel}${goto 256}${goto 256}System (/):${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 768}           ${font Sans:style=Bold:size=13}${color ffffff} ${time %I:%M %p }${font}${color}
${goto 15}            Lucid Lynx                                ${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 768}          ${time %A ~ %b %d}
${goto 15}CPU: ${cpubar cpu1 10,100}${font Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup eth0}                                                                                                                               
${goto 15}RAM: ${membar 10,100}${font Sans:style=Bold:size=9}  $memperc%${font}${goto 256}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown eth0}${goto 776}     ~Uptime: ${uptime} 
```

<3

---

