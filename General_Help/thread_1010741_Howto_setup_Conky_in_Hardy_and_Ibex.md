---
title: "Howto: setup Conky in Hardy and Ibex"
date: 2008-12-14
forum: General Help
---

### Post by seldon77 on 2008-12-14
**FOR HARDY AND IBEX. NOTE: for old Ubuntu versions, see here: [http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")**

Conky is an powerful desktop app that posts system monitoring info onto the root window. It used to be hard to set up properly (had unlisted dependencies, special command line compile options, and requires a mod to xorg.conf to stop it from flickering, and needed devilspie to work without being annoying). It's a lot easier these days, but there are still some tricks.

[CENTER]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96421&d=1229299247[/IMG][/CENTER]

1. Make sure the universe repo is enabled, and install 'conky' from universe repo. ie:
```

	sudo apt-get --assume-yes install conky

```

2. Make a configuration file in your home directory (ie. /home/bob). This is the code that describes what you want displayed on your conky desktop.
```

gedit /home/bob/.conkyrc

```

3. Obviously, you can put whatever you want in your .conkyrc.

One of the cutest scripts at the moments is called Conky Colours (as in the screenshot above) - [http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328"), but it is a little harder than other scripts to install.

Otherwise, for a very functional conky that I've mashed up from other scripts, you could paste the following code into the file and save / exit. I've added in some cool code that will show what programs on your machine are trying to connect to the outside world (should give you some warning of spyware, etc. on your machine), as well as a summary of whats being written in your /var/log file (system error msgs, etc), and also a list of the top few programs that are chewing up your CPU and memory:

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```
If the network connections graph does not work, you will have to change all "eth0" references to "ppp0" (for modem) or "ath0" (for some other devices). 

5. Run 'conky' to see if it works without flickering. If there is flickering, add the dbe module to your /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```
anywhere near the end add:
```

Section "Module"
        Load    "dbe"
EndSection

```
if there isn't already a Module section, otherwise just add 'Load "dbe"' into your Module section.

6. **If you do not have funky desktop effects on your desktop (Compiz, etc)** - then for vanilla Ubuntu (Gnome), Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot.

[INDENT][I][COLOR="DimGray"]NOTE: **Kubuntu users ONLY** make the following changes:
Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```

Since we don't use nautilus in Kubuntu, we don't need it.

Also, to get Conky to autostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```
**For XFCE ONLY** make the following changes to .conkyrc
```
own_window yes
own_window_type override
own_window_transparent yes

```
[/COLOR][/I][/INDENT]

7. **If you do have funky desktop effects on your desktop (Compiz, etc)** place a startup script called .conky_start.sh in your home directory:
```
#!/bin/bash
sleep 60 && conky;
```
This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky and try to do funky things with it. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs).

Please add comments if anything doesn't work or if you have other ideas and I can update the instructions.

---

### Post by trazart on 2008-12-15
To remove the shadow from the conky window you can also play with your Window Decoration preferences. Change which windows should have, or should not have, shadows.

[IMG]http://bayimg.com/image/gammcaabh.jpg[/IMG]

And add the line below to your .conkyrc file.
```
own_window_title mi_conky
```

---

### Post by AardvarkSagus on 2008-12-16
I have a question myself about the transparency of the window.  On my desktop, when I start conky, everything seems to run just fine except the background is only correct for my old monitor resolution of 1024x768.  I have recently obtained a new monitor that I pushed to 1152x864 and it is a little disorienting to see this discrepancy between the two images.  Thankfully I have a fairly sparce background so this is relatively minor, but I would like it to work properly.  

Occasionally the background will correct itself to the proper resolution, but after a while I will find it back to too small again.  I tried changing backgrounds to something else and it appeared correct.  When I returned it also appeared correct, but sure enough, a few minutes later, it was messed up again.

My background image is 1280x1024, so I know it's not just an issue with an image that is too small.  Any ideas?

---

### Post by eternalnewbee on 2008-12-16
Thank you seldon77.
Very nice.

---

### Post by gcranston on 2008-12-17
by the way, make sure all your scripts have #!/bin/bash at the FIRST LINE AND ONLY THE FIRST LINE, or you'll wind up hating yourself for hours trying to figure out why it works in the ####ing terminal and not in conky...


Sorry, but I needed to vent that somewhere.

---

### Post by seldon77 on 2008-12-19
Thanks for the comments and the 'thankses'!

As always, please let me know if you run into any bugs in the instructions above or if it isn't working for you. My first conky instructions were read by 250,000 or something people so I want to get them right!

Here is some cool code that I've done up which can be added into any homebrew .conkyrc file:

1. This little item is great for figuring out if you've got spy-ware or are being DOS attacked. It will list any programs that are connecting to the outside world, and tell you how many connections they are making:

${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

2. This one will list the latest 3 system log (error, etc) messages on your machine. Great to see if some piece of software or hardware isn't working right:

${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

3. This one will show if a program is stealing too much CPU or memory or has become a zombie eating up your resources. Good also for diagnosing which program is borking itself if your computer is hanging:

${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}

you can then kill the problem program easily from the command line = "kill [insert pid number]"

---

### Post by mvalviar on 2008-12-22
Hi, I followed you instructions for the installation and used copied your config. I have a problem though. I have conky on my desktop and everytime I click  my mouse on the area where the conky display is shown it draws a select area even though I didn't drag the mouse. The box starts from the left side of the screen to the mouse pointer. Dragging my mouse on the conky area is also buggy. I also tried the conky colors config with the same result. In addition I can click and drag items on the desktop when I click on the conky area even though the items are on the left side of the desktop.

---

### Post by jesseruu on 2008-12-23
Great post mate! helped me **allot!**

---

### Post by SR_ELPIRATA on 2008-12-26
Great tutorial. I've been seeing many of these hardware/software monitors directly on the desktop and I was wondering how that was setup. Now, comparing my conky to the screenshot on top, it looks much different, though I still like it. (Edit: After another reading finally noticed that the one pictured is a different script).

One of the things I've noticed is that when I execute the command conky in the terminal, it says that cant find the Arial font. I just copied and pasted as instructions said. From what I can tell, the font is installed on my system so dont undertand the error. Would like to change to another font more similar to the one in the screenshot.

Again, lots of thanks for the tutorial :)

ELP

---

### Post by seldon77 on 2008-12-28
> **mvalviar said:**
> Hi, I followed you instructions for the installation and used copied your config. I have a problem though. I have conky on my desktop and everytime I click  my mouse on the area where the conky display is shown it draws a select area even though I didn't drag the mouse. The box starts from the left side of the screen to the mouse pointer. Dragging my mouse on the conky area is also buggy. I also tried the conky colors config with the same result. In addition I can click and drag items on the desktop when I click on the conky area even though the items are on the left side of the desktop.

from what I gather, you are saying that the conky is all up and working fine but that clicking on it behaves differently from clicking on other parts of the desktop (it draws a select rectangle??)

that is just what conky does. It would be nice if you could put icons, etc. over conky but it doesn't allow that unfortunately. It's really just like an application window, which has had the title, scroll bar, and all other decorations etc. stripped off.

---

### Post by haneya on 2008-12-29
Hi , well i followed ur post but conky not working 

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (14000a8) is subwindow of root window (8b)
Conky: window type - override
Conky: drawing to created window (0x4400003)
Conky: drawing to single buffer
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

```

Thanks

---

### Post by BLTicklemonster on 2008-12-29
I've never been able to get my font to show either.

I've tried 

fc-cache -f -v ~/.fonts
 
from the terminal to get my fonts in ~/.fonts to show, and I've edited the .conkyrc file like this:

font -*-Treamd-*-*-*-*-*-*-*-*-*-*-*-*

Yet I still see a generic font. Nothing I put in works.

I've gotten most everything else cleaned up, and now I see this when I run conky from the terminal:

bill@bill-desktop:~$ conky
Conky: can't load font '-*-Treamd-*-*-*-*-*-*-*-*-*-*-*-*'
Conky: desktop window (10000ba) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (2e00003)
Conky: drawing to double buffer


*EDIT: I set xft to true, and changed the font entry to xftfont Treadm:size=8, and sure enough, the "can't load font" message is gone, but the font I see is not Treadm. And I don't see any more cpu usage than without xft.

---

### Post by mikull on 2008-12-30
i followed this script word to word.
i get my conky started up but i see the box around it and when ever i open a new window in the full screen ,conky overlaps it(seems to be above all) yes,i have AWN and Compiz running. i have made the script file (.conky_start.sh) and placed it in /home and made it an executable as well and added this script file in the start up under sessions. the command i used to make it executable is the chmod as directed and the command i sued in the start up session manager was just conky_start.sh

what am i doing wrong?

---

### Post by FerociousTwig on 2008-12-30
Same problem as mikull except it seems to go away occasionally if I move it around the desktop...

---

### Post by mikull on 2008-12-30
wonder what is happening?!!? as of now i do a killall and restart conky.
solutions?!?! any1?

---

### Post by euclidsbrother on 2008-12-30
> **seldon77 said:**
> [http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")

cool.. i'm going to try to install it now...

Also.. is there a place I can download that hires background with the tower?

Thanks
-EB

---

### Post by seldon77 on 2009-01-07
> **FerociousTwig said:**
> Same problem as mikull except it seems to go away occasionally if I move it around the desktop...

hmmmm.... are you running the /conky_start.sh script properly - rather than just running 'conky'?

If you just run conky at bootup, then compiz can get confused and think it's a window and draw a border around it and shadows, etc.

Best to run a little script that calls the sleep command, and runs conky about 60 seconds after the desktop has all started up (as in the instructions).

Let me know whether this fixes it, or if there are still problems.

As for the font issue, it is a problem with conky. Removing the line (which causes the error) unfortunately causes other font problems. I think conky colours (from gnomelook.org) has worked out a way not to get the font error message and choose a font. Check their script. Otherwise, you don't see the error if running it via the gnome startup program so its not something I've worried about too much.


As for the background, I think it is from deviantart.com (try ~americanpsycho who does some cool backgrounds, I think that one was his). If not, search the top surreal / landscapes on deviantart. Some great stuff there.

---

### Post by seldon77 on 2009-01-07
> **haneya said:**
> Hi , well i followed ur post but conky not working 

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (14000a8) is subwindow of root window (8b)
Conky: window type - override
Conky: drawing to created window (0x4400003)
Conky: drawing to single buffer
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

```

Thanks

These errors should be minor and in the background & not stop conky from working. However, I've updated the script to remove the errors.

Thanks for the bug report.

---

### Post by Bruce M. on 2009-01-07
> **mikull said:**
> wonder what is happening?!!? as of now i do a killall and restart conky.
solutions?!?! any1?

I'm running Xubuntu 8.10-64bit and have a nice little script that will do just nicely what you want.

ssc.sh (Star/Stop Conky)
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
#sleep 3  # sleep not required for xfce on startup - 30 or more for others
conky -c ~/Conky/conkymain &
#sleep 3
conky -c ~/Conky/conkyforecast &
#sleep 3
conky -c ~/Conky/conkyemail &
#sleep 3 &&
conky -c ~/Conky/conkygcal &
#sleep 3 &&
conky -c ~/Conky/todo &
 exit
fi
```
Obviously you will have to modify it to your setup.

Because sleep is not required for Xfce I have then commented out and use it in my auto-startup routine.

I also have an icon on my panel pointing to the script so when I make changes I can see then instantly by one click (off) and a second click (on).

Now if you need a sleep function for auto-start (GNOME, Compiz etc) great, but there is nothing saying you can't reproduce the script with no sleep function to be used with the icon for when you are editing. After all, your desktop is already up and running.

Have a nice day
Bruce

---

### Post by euclidsbrother on 2009-01-07
> **seldon77 said:**
> As for the background, I think it is from deviantart.com (try ~americanpsycho who does some cool backgrounds, I think that one was his). If not, search the top surreal / landscapes on deviantart. Some great stuff there.

I couldn't find that one (searched for about an hour), but your right, there are alot of great images there.. THANKS..

-EB

---

### Post by haneya on 2009-01-07
seldon77 Hi man, 

Dude still getting the same error and conky not working what is wrong ?!

---

### Post by seldon77 on 2009-01-09
> **haneya said:**
> seldon77 Hi man, 

Dude still getting the same error and conky not working what is wrong 
?!

Hi, to answer this, first - i take it you are running conky from the command line?? Otherise, you wouldn't see these messages...

Second, the errors are not fatal errors. They are notifications & perhaps a warning only (if not set up as per the enclosed script) but not fatal errors. So, they shouldn't stop it from working.

Are you using gnome?? Also, are you waiting for ubuntu to fully start before running?? Last, is it just that conky is there but hard to see (you have a black background, or are running other things which are putting conky behind the background??)

If something else is minimizing conky or putting it behind the background, you could use "wmctrl" (a program you will have to install via synaptic) or devilspie to put the focus back onto conky.

Install wmctrl and put this:

```
${execi 30 wmctrl -a conky}
```

into your .conkyrc file somewhere as a command to keep pulling conky to the front every 30 seconds if the focus is being lost.

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by mvalviar on 2009-01-22
> **seldon77 said:**
> from what I gather, you are saying that the conky is all up and working fine but that clicking on it behaves differently from clicking on other parts of the desktop (it draws a select rectangle??)

that is just what conky does. It would be nice if you could put icons, etc. over conky but it doesn't allow that unfortunately. It's really just like an application window, which has had the title, scroll bar, and all other decorations etc. stripped off.

Hi, 

Thank you for that. I haven't visited this thread in a while. I'm a little adept with conky now but I haven't tried to write a config from scratch. I tried conky colors. It is flawless. But when I moved it to  the top-left of my screen and edited some stuff below TEXT so that it displays horizontally it started flickering. Any advice on this?

---

### Post by AngelBreath on 2009-01-22
I m trying to make it work in kubuntu 8.10 but no luck.Running conky from terminal i m taking the same messages (the minor ones) my backround becomes black and no conky at all.

 Any idea?

---

### Post by Guru Janitor on 2009-01-24
Hey guys, I can't get Conky to install correctly.  Basically, I try to install, said it already is, I try to run it, and it says it isn't installed...

I attached a screenshot of the terminal.

Anyone got an idea of whats wrong? :-?

---

### Post by kaivalagi on 2009-01-24
Can I make a suggestion?

To add to what you have in the guide, it may be worthwhile explaining how to compile conky with certain features enabled

For example I used to use xmms2 (music daemon not gui) and found this thread useful as it explained how to compile conky with xmms2 support much like the default mpd support: [http://ubuntuforums.org/showthread.php?t=706736](http://ubuntuforums.org/showthread.php?t=706736)

There are a few features you don't get by default with the apt package...that users might find helpful

---

### Post by pemur1 on 2009-01-24
Thanks so much for the "How-To". Everything worked great!

As can be seen in the screen shot, I got Conky to work, but it just looks too plain. I'd like to add a weather script and a calendar, but I'm just clueless on what I need to do. Any assistance with this will be greatly appreciated.

---

### Post by Bruce M. on 2009-01-25
> **pemur1 said:**
> Thanks so much for the "How-To". Everything worked great!

As can be seen in the screen shot, I got Conky to work, but it just looks too plain. I'd like to add a weather script and a calendar, but I'm just clueless on what I need to do. Any assistance with this will be greatly appreciated.

Hi pemur1,

You can find some great scripts here: [Kaivalagi's Python Scripts]("http://ubuntuforums.org/showthread.php?p=6097476") of which one is [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328").

What kind of calendar are you looking for?

Have a nice day.
Bruce

---

### Post by ruipalmeira on 2009-01-25
i'm getting this 

[quote="gnome-terminal"]rui@rui-desktop:~$ conky
Conky: desktop window (1c000aa) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1 [/quote]

with conky colors .conkyrc's, do you have any clue on how to solve this ??
thanks

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> Hi pemur1,

You can find some great scripts here: [Kaivalagi's Python Scripts]("http://ubuntuforums.org/showthread.php?p=6097476") of which one is [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328").

What kind of calendar are you looking for?

Have a nice day.
Bruce

Yeah, I've been checking those out. I got the weather script to work and was working on the calendar, but I couldn't get the days/dates to line up correctly. I'm gonna take another look at it when I get home. 

I am finding this thing getting somewhat addictive.:)

---

### Post by pemur1 on 2009-01-26
> **ruipalmeira said:**
> i'm getting this 



with conky colors .conkyrc's, do you have any clue on how to solve this ??
thanks

I believe you'll have to do some editing of the scripts in .conkyrc. I tried to do the same thing and ended up with a lot of errors. I didn't take the time to look at every line of script so I didn't fix it. After learning more and more about conky (Thanks to Bruce M., kaivalagi, and others), I've decided to delve into it a bit more.

---

### Post by ruipalmeira on 2009-01-26
> **pemur1 said:**
> I believe you'll have to do some editing of the scripts in .conkyrc. I tried to do the same thing and ended up with a lot of errors. I didn't take the time to look at every line of script so I didn't fix it. After learning more and more about conky (Thanks to Bruce M., kaivalagi, and others), I've decided to delve into it a bit more.

thanks, did some research and found this [Quote="friend"]

so you have to edit your .conkyrc removing these lines:
${font StyleBats:size=16}A${font} CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font} CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}

and replacing them with a new line:
${font StyleBats:size=16}A${font} CPU0: ${cpu cpu0}% ${alignr}${cpubar cpu0 8,60}

[/quote]

thank you

---

### Post by pemur1 on 2009-01-26
> **ruipalmeira said:**
> thanks, did some research and found this 

thank you

You're more than welcome!

Have you checked out this thread:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

There's some amazing things you can do with conky. :)

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> Yeah, I've been checking those out. I got the weather script to work and was working on the calendar, but I couldn't get the days/dates to line up correctly. I'm gonna take another look at it when I get home. 

I am finding this thing getting somewhat addictive.:)

OH yes, it is addictive. ;)

I posted in another thread a simple calendar for you and the fact that you **need** to use a mono font to get the day/dates to line up correctly.

The line is simple, use any mono font you have and edit the size to your liking:
```

${font LCDMono:size=9}${pre_exec cal -3 | cut -c23-44}$font
${font DejaVu Sans Mono:size=9}${pre_exec cal -3 | cut -c23-44}$font
```
There's two examples.

Have a nice day.
Bruce

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> OH yes, it is addictive. ;)

I posted in another thread a simple calendar for you and the fact that you **need** to use a mono font to get the day/dates to line up correctly.

The line is simple, use any mono font you have and edit the size to your liking:
```

${font LCDMono:size=9}${pre_exec cal -3 | cut -c23-44}$font
${font DejaVu Sans Mono:size=9}${pre_exec cal -3 | cut -c23-44}$font
```
There's two examples.

Have a nice day.
Bruce

Those are so cool! I especially like the top one. :D

If I can find a digital clock script using the same font, I think I'd be set for a while (maybe a week before I got bored) :)

---

### Post by Bruce M. on 2009-01-26
> **ruipalmeira said:**
> i'm getting this 



with conky colors .conkyrc's, do you have any clue on how to solve this ??
thanks

Hi ruipalmeira,

Can you show us your actual conky file so we can see what's what.

One thing I see is you are trying something with a CPU #2 that you don't have.
> Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1

Thanks
Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> Those are so cool! I especially like the top one. :D

If I can find a digital clock script using the same font, I think I'd be set for a while (maybe a week before I got bored) :)

Digital ... you mean one like this?

[CENTER][[IMG]http://img525.imageshack.us/img525/834/desktopgm4.th.gif[/IMG]](http://img525.imageshack.us/my.php?image=desktopgm4.gif)[/CENTER]

Why not show us your screenshot and your code?

Have a nice day.
Bruce

---

### Post by takaratiki on 2009-01-26
Hey Bruce M., noticed in your calendar that you managed to get a different color for elements within it (days of week, current day). How did you go about doing that? I'm using a pal command line calendar in conky right now but am at a loss as to how to make the different colors show. Thanks

---

### Post by malathion on 2009-01-26
Bookmarked. Thanks!

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> Digital ... you mean one like this?

[CENTER][[IMG]http://img525.imageshack.us/img525/834/desktopgm4.th.gif[/IMG]](http://img525.imageshack.us/my.php?image=desktopgm4.gif)[/CENTER]

Why not show us your screenshot and your code?

Have a nice day.
Bruce

Wow! I love that whole setup! That's just fantastic!!

I'd love to have something like that. but it'd take me forever to figure all of it out. I guess I'll stick with the basic stuff for now. At least until I get more proficient. :)

Here's my .conkyrc and a screen shot.It's not much right now. But understand I'm still a newbie with it.

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5

maximum_width 275
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
gap_y 20
 
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color

${color orange}WEATHER ${hr 2}$color
${execpi 1800 conkyForecast --location=USNC0204  --imperial --template=/usr/share/conkyforecast/example/conkyForecast.template}
```

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> Wow! I love that whole setup! That's just fantastic!!

I'd love to have something like that. but it'd take me forever to figure all of it out. I guess I'll stick with the basic stuff for now. At least until I get more proficient. :)

No, not that hard, check it out [here]("http://linux-hardcore.com/index.php?topic=1879.0"). And on the bottom of the post is my very first conky. Not nearly as good as your first one.  :)

If you need more help just ask.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-01-26
> **takaratiki said:**
> Hey Bruce M., noticed in your calendar that you managed to get a different color for elements within it (days of week, current day). How did you go about doing that? I'm using a pal command line calendar in conky right now but am at a loss as to how to make the different colors show. Thanks

Yea, using jjgomera's script and these lines: **(Thanks JJ)**

```
${font LCDMono:size=19}${color2}${pre_exec ~/Conky/scripts/calendario.sh semana}
${color 888888}${pre_exec ~/Conky/scripts/calendario.sh pasado}${color2}${pre_exec ~/Conky/scripts/calendario.sh hoy}${color 888888}${pre_exec ~/Conky/scripts/calendario.sh futuro}$font
```

and the script: **calendario.sh**

```
#! /bin/sh
# written by: jjgomera

#str=`echo '\033[01;32m29'`

# replace the 4 "cal |" with "cal -m |" to have the week start on Monday

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```

Have a nice day.
Bruce

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> No, not that hard, check it out [here]("http://linux-hardcore.com/index.php?topic=1879.0"). And on the bottom of the post is my very first conky. Not nearly as good as your first one.  :)

If you need more help just ask.

Have a nice day.
Bruce

Thanks for the vote of confidence. :D

As far as yours is concerned, what scripts would I need to change to make it look like yours only in English and my location? I probably wouldn't use the email, or agenda conkys (conkies?) though. Thanks for everything! :)

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> Thanks for the vote of confidence. :D

As far as yours is concerned, what scripts would I need to change to make it look like yours only in English and my location? I probably wouldn't use the email, or agenda conkys (conkies?) though. Thanks for everything! :)

Oh, yea, Spanish ... but only in the weather.

Look for the hidden file (since you have the weather now) ~/.conkyForecast.config ... in there (it defaults to English)

Mine looks like:

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /home/bruloo/Conky/cache
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxxxxxx
XOAP_LICENCE_KEY = xxxxxxxxxxxxxxxxx

```

make sure **LOCALE = es** reads **LOCALE = en**
and put the codes you got from weather.com in the last two lines.

myweather.template (in English)
```
${color4}${font ConkyWeather:size=55}[--datatype=WF]$font$color
${voffset -70}${goto 90}${color7}${font Zekton:size=20}[--datatype=DW --shortweekday --startday=0]:$color [--datatype=HT]
${goto 90}${voffset -10}${font Zekton:size=9}${color7}Feels Like: ${color}[--datatype=LT]$font
${goto 10}${voffset 20}${font Zekton:bold:size=11} ${color7}[--datatype=CC]$color$font
${goto 300}${voffset -90}${font ConkyWindN:size=40}${color4}[--datatype=BS]$font
${goto 380}${voffset -45}${color7}Wind: ${color3}[--datatype=WS] ${color7}(${color4}[--datatype=WA]°${color7}) ${color3}[--datatype=WD]
${voffset 0}${goto 380}${color7}Visibility:${color3} [--datatype=VI]
${voffset 0}${goto 380}${color7}Dew Point: ${color3}[--datatype=DP]$color$font
${goto 300}${voffset 10}${color7}Pressure: ${color3}[--datatype=BR] - [--datatype=BD]$color
${goto 300}${color7}Humidity: ${color3}[--datatype=HM]  ${color7}UV: ${color3}[--datatype=UI] - ${color3}[--datatype=UT]
${goto 300}$hr
${voffset 15}${color3}${font SunNMoon:size=50}n$font$color	${goto 70}${voffset -38}${color0}${font Arrows:size 20}b$font${color3}[--datatype=SR]
${goto 70}${color7}Hrs:${color3}[--datatype=DL]
${goto 70}${color0}${font Arrows:size 20}h$font${color3}[--datatype=SS]
${goto 170}${voffset -50}${color4}${font moon phases:size=40}[--datatype=MF]$font
${voffset -70}${goto 300}${color7}[--datatype=DW --shortweekday --startday=1]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=1]/[--datatype=LT --hideunits --hidedegreesymbol --startday=1]${goto 380}${color7}[--datatype=DW --shortweekday --startday=2]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=2]/[--datatype=LT --hideunits --hidedegreesymbol --startday=2]${goto 460}${color7}[--datatype=DW --shortweekday --startday=3]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=3]/[--datatype=LT --hideunits --hidedegreesymbol --startday=3]${goto 540}${color7}[--datatype=DW --shortweekday --startday=4]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=4]/[--datatype=LT --hideunits --hidedegreesymbol --startday=4]
${goto 300}${color3}${font ConkyWeather:size=30}[--datatype=WF --startday=1]${goto 380}[--datatype=WF --startday=2]${goto 460}[--datatype=WF --startday=3]${goto 540}[--datatype=WF --startday=4]$font$color
${goto 300}${color7}Sun:${color4}[--datatype=SR --startday=1]${goto 380}${color7}Sun:${color4}[--datatype=SR --startday=2]${goto 460}${color7}Sun:${color4}[--datatype=SR --startday=3]${goto 540}${color7}Sun:${color4}[--datatype=SR --startday=4]
${goto 300}${color7}   :${color4}[--datatype=SS --startday=1]${goto 380}${color7}   :${color4}[--datatype=SS --startday=2]${goto 460}${color7}   :${color4}[--datatype=SS --startday=3]${goto 540}${color7}   :${color4}[--datatype=SS --startday=4]
${font DejaVu Sans Mono:size=7}W:[--datatype=LU] -=- C:[--datatype=LF]$font${voffset -2}${goto 300}${color7}Hrs:${color4}[--datatype=DL --startday=1]${goto 380}${color7}Hrs:${color4}[--datatype=DL --startday=2]${goto 460}${color7}Hrs:${color4}[--datatype=DL --startday=3]${goto 540}${color7}Hrs:${color4}[--datatype=DL --startday=4]
```

Be back soon.
Bruce

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> Oh, yea, Spanish ... but only in the weather.

Look for the hidden file (since you have the weather now) ~/.conkyForecast.config ... in there (it defaults to English)

Mine looks like:

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /home/bruloo/Conky/cache
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxxxxxx
XOAP_LICENCE_KEY = xxxxxxxxxxxxxxxxx

```

make sure **LOCALE = es** reads **LOCALE = en**
and put the codes you got from weather.com in the last two lines.

Be back soon.
Bruce

Where would I save the weather template at? I noticed that you created a folder in your Home directory called Conky and saved your scripts there. I'd imagine that it would make things a whole lot easier to do that. I really appreciate your assistance with this. I'm already working on a new .conkyrc file. I've used yours as a base and am in the process of changing the fonts, colors, and sizes. If I run into any problems, I'll be sure to let you know. :D

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> Where would I save the weather template at? I noticed that you created a folder in your Home directory called Conky and saved your scripts there. I'd imagine that it would make tings a whole lot easier to do that. I really appreciate your assistance with this. I'm already working on a new .conkyrc file. I've used yours as a base and am in the process of changing the fonts, colors, and sizes. If I run into any problems, I'll be sure to let you know. :D

You can save it anywhere as lonk as you tell conky where it is.

Yes, I created various directories:

~/Conky - for the actual conky(rc) files I use. I have almos 200 of them (collect over a period of time)

~/Conky/scripts - I keep "any" script relating to conky in here, and my "templates" happen to be here as well - and:

~/Conky/Text - where I keep text files relating to different things about conky.

Easier that way.

Bruce

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> You can save it anywhere as lonk as you tell conky where it is.

Yes, I created various directories:

~/Conky - for the actual conky(rc) files I use. I have almos 200 of them (collect over a period of time)

~/Conky/scripts - I keep "any" script relating to conky in here, and my "templates" happen to be here as well - and:

~/Conky/Text - where I keep text files relating to different things about conky.

Easier that way.

Bruce

That definitely makes a lot of sense. Thanks for the tip.

I've run into a problem with the fonts. I've changed the Zekton font to something else, but they don't seem to change. Am I doing something wrong or should I go ahead and download the Zekton font?

Now I've run into a problem with the calendar. For some reason, I'm getting a "permission denied" error in the terminal when I try to access it.

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> That definitely makes a lot of sense. Thanks for the tip.

I've run into a problem with the fonts. I've changed the Zekton font to something else, but they don't seem to change. Am I doing something wrong or should I go ahead and download the Zekton font?

I've called the Zekton fonts in the part above TEXT.

I'd get the font, All fonts act different even if the "size=19" is the same.

It will change things a LOT!

Bruce

---

### Post by pemur1 on 2009-01-26
> **Bruce M. said:**
> I've called the Zekton fonts in the part above TEXT.

I'd get the font, All fonts act different even if the "size=19" is the same.

It will change things a LOT!

Bruce

OK. Thank you so much! Sorry to be such a bother with this. You're a tremendous help.

---

### Post by Bruce M. on 2009-01-26
> **pemur1 said:**
> OK. Thank you so much! Sorry to be such a bother with this. You're a tremendous help.

Don't worry about it. In time you'll be helping others.
My first post on conky was on [Dec 24th, 07]("http://ubuntuforums.org/showthread.php?t=281865&page=116"), and I must have typed 50 posts between then and the 26th -- right through Christmas. People helped me, so I help others today.

Today was your day. :D Looking forward to seeing the end result.

have a great day.
Bruce

---

### Post by pemur1 on 2009-01-27
I've finally gotten some time to work on this. I got the calendar to work right (looks great!), and changed some other things, but I'm having a few problems. I'd like the clock to be 12 hour instead of 24 hour, and I can't figure out how to get the conky itself narrower. Screen shot below. Any assistance would be greatly appreciated.

EDIT: OK. I figured out why I couldn't get the conky narrower. The size of the logo was throwing everything off.

---

### Post by Bruce M. on 2009-01-28
> **pemur1 said:**
> I've finally gotten some time to work on this. I got the calendar to work right (looks great!), and changed some other things, but I'm having a few problems. I'd like the clock to be 12 hour instead of 24 hour, and I can't figure out how to get the conky itself narrower. Screen shot below. Any assistance would be greatly appreciated.

EDIT: OK. I figured out why I couldn't get the conky narrower. The size of the logo was throwing everything off.

No, not the size, the position. :D
Mine works beautifully.

I'm working on that clock problem, I'm sure there is a way.

I'll post results when (if) I find it.

Bruce

---

### Post by pemur1 on 2009-01-28
Thanks, Bruce!

It's beginning to look half-way decent. I haven't even tried to figure out the myweather part yet. I wouldn't mind some gtk scripts, but everything I've read about them seems like a foreign language to me. I've used Ubuntu for only about 10 months and have never taken the opportunity to read up on scripts and other things.

Here's a screenshot of what I have so far. I'll need to change the font color and probably some other stuff. 

I did read something about you having a script that shows the temperature of your graphics card. Do you happen to have that handy?

Thanks for all of the assistance.

---

### Post by Bruce M. on 2009-01-28
> **pemur1 said:**
> Thanks, Bruce!

It's beginning to look half-way decent. I haven't even tried to figure out the myweather part yet. I wouldn't mind some gtk scripts, but everything I've read about them seems like a foreign language to me. I've used Ubuntu for only about 10 months and have never taken the opportunity to read up on scripts and other things.

Here's a screenshot of what I have so far. I'll need to change the font color and probably some other stuff. 

I did read something about you having a script that shows the temperature of your graphics card. Do you happen to have that handy?

Thanks for all of the assistance.

Go to the link I gave you originally, the scripts are there, check my original conkymain and you'll see how I simply renamed them to use as needed.

I can see where you're conky file could use some "touch up" with spacing etc.

Please post it here so I can look at it. OK. :D

---

### Post by pemur1 on 2009-01-29
> **Bruce M. said:**
> Go to the link I gave you originally, the scripts are there, check my original conkymain and you'll see how I simply renamed them to use as needed.

I can see where you're conky file could use some "touch up" with spacing etc.

Please post it here so I can look at it. OK. :D

Here you go:

```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=9
xftfont Zekton:size=9
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 blue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment tr  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y 35
text_buffer_size 256 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

#${font DejaVu Sans Mono:size=9}TCP Connections
#1-1055: ${tcp_portmon 1 1055 count}${alignr 2}1056-65535: ${tcp_portmon 1056 65535 count}$font

#${font DejaVu Sans Mono:bold:size=9}VR: ${execi 300 /usr/bin/perl ~/conky/scripts/HowLong.pl "13 March 09"}$font
#${color0}${hr}$color

TEXT
${font Zekton:size=12}${color4}${alignc}UTC:$color ${utime %H:%M}
${font Zekton:size=9}${color7}Man: $color${tztime Canada/Central %H:%M}${alignr 2}${color7}Ont: $color${tztime Canada/Eastern %H:%M}$font
${color0}${hr}
${goto 70}${font COPRGTL:bold:size=9}${color7}Elizabeth City, NC$color
${goto 70}${color4}36° 17' 39" N${goto 164}76° 15' 5" W$color$font
${font LCDMono:size=45}${time %H:%M}$font
${voffset -63}${font Zekton:size=20}${alignr 5}${time %b}$font
${font Zekton:size=15}${alignr 5}${time %y}$font
${color0}${hr 1}$color
${font LCDMono:size=15}${color2}${pre_exec ~/conky/scripts/calendar.sh semana}
${color 888888}${pre_exec ~/conky/scripts/calendar.sh pasado}${color2}${pre_exec ~/conky/scripts/calendar.sh hoy}${color 888888}${pre_exec ~/conky/scripts/calendar.sh futuro}
$font${voffset -30}${color7}${font OpenLogos:size=100}v$font$color

${voffset -65}${font Zekton:size=10}${color2}Timeline:$color${alignr 2}$uptime_short
${color0}${hr 1}$color
${alignc}${color7}<= ${color8}Temperatures ${color9}=>$color
${font DejaVu Sans Mono:size=9}${color4}CPU: ${color5}${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs ~/conky/scripts/ColorTempCPU.sh}°$color${goto 80}${color4}Core: ${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs ~/conky/scripts/ColorTempCore.sh}°$color${goto 150}${color4}M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/conky/scripts/ColorTempMB.sh}°$color${alignr 2}${color4}GPU: ${execpi 8 sh -c "DISPLAY=:0.0 nvidia-settings -q gpucoretemp | grep Attribute | cut --characters 41-42" | xargs ~/conky/scripts/ColorTempGPU.sh}°$font
${voffset 10}${font DejaVu Sans Mono:size=9}${color2}Process:$color${alignr 2}${color 888888}${cpubar cpu0 14,140}$color
${color4}${voffset -16}${goto 140}$running_processes /$processes${alignr 5}$cpu%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu2 14,140}$color
${voffset 5}${color7}Load:		${goto 70}${color3}${loadavg 1}	${goto 140}${loadavg 2}${alignr 5}${loadavg 3}$color
${voffset 5}${color2}RAM:$color${alignr 2}${color 888888}${membar 14,140}$color
${color4}${voffset -16}${goto 140}$mem${alignr 5}$memperc%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu3 14,140}$color
${voffset 5}${color7}Buffered:${color3}	${goto 70}${buffers}${alignr 2}${color7}Cached:${color3} ${cached}
${voffset 5}${color2}SWAP:$color${alignr 2}${color 888888}${swapbar 14,140}$color
${color4}${voffset -16}${goto 140}$swap${alignr 5}$swapperc%$font
${voffset -16}${alignr 2}${color yellow}${cpubar cpu4 14,140}$color
${color0}${hr 1}$color
${voffset 5}${color2}HD Info${color7} -$color Free${color7} - Used$color
${voffset 5}${color2}sda: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sda | cut --characters 27-28 | xargs ~/conky/scripts/ColorTempHDD.sh}°$color   ${color2}Disk I/O:$color   ${diskio sda}
${font DejaVu Sans Mono:size=9}		${goto 25}${color7}Root:$color	${goto 90}${fs_free_perc /}%	${goto 135}${fs_free /}${color2}${alignr 2}${color7}${fs_used /}$color$font
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Home:$color	${goto 90}${fs_free_perc /home/peter1}%	${goto 135}${fs_free /home/peter1}${alignr 2}${color7}${fs_used /home/peter1}$color$font
${voffset 5}${color2}sdb: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sdb | cut --characters 31-32 | xargs ~/conky/scripts/ColorTempHDD.sh}°$color     ${color2}Disk I/O:$color  ${diskio sdb}
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Data:$color	${goto 90}${fs_free_perc /media/Data}%	${goto 135}${fs_free /media/Data}${alignr 2}${color7}${fs_used /media/Data}$color$font
${color0}${hr}$color
${voffset 5}${alignc 2}${color2}IP:  $color${addr eth0}
${color8}Dn:$color${downspeed eth0} k/s ${totaldown eth0}${alignr 2}${color7}Up:$color${upspeed eth0} k/s ${totalup eth0}
${color2}In:  $color${tcp_portmon 1 32767 count}${alignc}${color2}Out:  $color${tcp_portmon 32768 61000 count}${alignr 2}${color2}Total:  $color${tcp_portmon 1 65535 count}
${font DejaVu Sans Mono:size=9}${color8}Today:$color${goto 55}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 140}${color7}Today:$color${goto 185}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
${color8}Week:$color${goto 55}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 140}${color7}Week:$color${goto 185}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
${color8}Month:$color${goto 55}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 140}${color7}Month:$color${goto 185}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}$font
${color0}${hr}$color
${goto 60}${color9}${font Zekton:size=12}${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d'  | sed 's/$/ of TRASH /'}$font$color
```

Thanks again!

---

### Post by Bruce M. on 2009-01-29
> **pemur1 said:**
> Here you go:

Thanks again!

No problem, it's attached as "conkymain2" I have also included the **ColorTemp sh** files you asked about. and a full screen image of it running on my machine.

I removed the time reference for Man and Ont as I didn't think you really wanted the times zones for two Canadian provinces. (I have family there)

There will be some problems if you don't have a nvidia video card. for the GPU temp. but it gives the idea of how to use it.

**Also note:** sdb (second hard drive) you can remove that or make sure it points to the mount point if you have one.

Also in order to get the temperatures working you must install:
[B]lm-sensors
hddtemp[/B]

and to use the botton portion where it shows **Today, Week and Month** you'll need **vnstat**

Any more questions just ask.
Bruce

---

### Post by pemur1 on 2009-01-29
Wow!

That looks great! :D

Thanks so much for taking the time to help me.

This is why Ubuntu is the best OS. People are more than happy with assisting the less experienced users.

---

### Post by Bruce M. on 2009-01-29
> **pemur1 said:**
> Wow!

That looks great! :D

Thanks so much for taking the time to help me.

This is why Ubuntu is the best OS. People are more than happy with assisting the less experienced users.

A year and a half ago I was right where you are. [Some reading!]("http://ubuntuforums.org/showthread.php?t=281865&page=116")
People helped me, I pay them back by helping others.

Makes the Ubuntu world a better place to be.
Have a nice day/night.
Bruce

---

### Post by BurnChao on 2009-01-31
> **seldon77 said:**
> 7. **If you do have funky desktop effects on your desktop (Compiz, etc)** place a startup script called .conky_start.sh in your home directory:
```
#!/bin/bash
sleep 60 && conky;
```
This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky and try to do funky things with it. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs).

I'm sorry, I can't understand this at all. I don't what is meant by "place a startup script". I tried copying and pasting the code into Terminal, that doesn't seem to be right.

Maybe someone could break this step down into smaller pieces for me?

Also, I get a bunch of errors in Terminal whether I use the default conf file or the one provided aat the top of this thread. (not the same errors for each conf.) But I'll worry more about trying to fix those after I can get Conky to run at start up.

Anyways, thanks in advance to anyone who can help me.

---

### Post by pemur1 on 2009-01-31
> **BurnChao said:**
> I'm sorry, I can't understand this at all. I don't what is meant by "place a startup script". I tried copying and pasting the code into Terminal, that doesn't seem to be right.

Maybe someone could break this step down into smaller pieces for me?

Also, I get a bunch of errors in Terminal whether I use the default conf file or the one provided aat the top of this thread. (not the same errors for each conf.) But I'll worry more about trying to fix those after I can get Conky to run at start up.

Anyways, thanks in advance to anyone who can help me.

Step 1 - Open your text editor (Applications/Accessories/Text Editor).
Step 2 - Copy & paste the first code into the text editor.
Step 3 - Save the file as .conky_start.sh in your Home directory (You can change the wait time for Conky to open. Example: 60 to 20 seconds = sleep 20 && conky)
Step 4 - Open the Terminal. Copy & paste the second code into the terminal.

Follow the rest of the instructions to add it to your startup programs.

---

### Post by BurnChao on 2009-02-01
Great, thanks.

---

### Post by djtreo on 2009-02-04
hi everyone!

new in conky here. followed all the setup and scripts and stuff, restarted my system and whalla..

conky loads in a "windowed" manner as oppose to the screenshot on the first page of this thread and it loads somewhere on the bottom left portion of my screen.

what i want is load conky window-less in the right part of the screen same as the screenshot of the thread starter.

any idea?

by the way, i copy-pasted the script supplied by the thread starter. thanks in advance.

---

### Post by hellmitre on 2009-02-05
pemur1, what's your dock app? It looks nice. AWN?

---

### Post by HuaiDan on 2009-02-05
I think many of the errors noted on the first page could have been avoided if n00bs realized that "/home/bob" in the OP should be "/home/YOUR DIRECTORY

And don't type "YOUR DIRECTORY". Substitute the name of your home folder.

---

### Post by Bruce M. on 2009-02-06
> **HuaiDan said:**
> I think many of the errors noted on the first page could have been avoided if n00bs realized that "/home/bob" in the OP should be "/home/YOUR DIRECTORY

And don't type "YOUR DIRECTORY". Substitute the name of your home folder.

I agree. I also advocate NOT using the default ~/.conkyrc but creating one with a different name in a different place.

All of mine are in: ~/Conky

For new people **[SIZE="4"]~/[/SIZE]** is equal to /home/what_you_called_your_home_directory

Some examples:
/home/bruloo <--- mine
/home/ubuntu
/home/Tom <-- bet this is Tom's computer

Want to see yours - Open your file manager (see attached). The name_you_see is your home directory and can be used as:

/home/the_name_you_see
or a shortcut:
~/

Have a nice day.
Bruce

---

### Post by j2r7 on 2009-02-13
This is most excellent! thanks to you and everyone  . . .

---

### Post by pemur1 on 2009-02-14
> **hellmitre said:**
> pemur1, what's your dock app? It looks nice. AWN?

Sorry for the delay answering. I did something stupid and had to reinstall Ubuntu.

That's actually Cairo Dock. Just did some tweaking to it.

---

### Post by Foster Grant on 2009-02-18
> **AngelBreath said:**
> I m trying to make it work in kubuntu 8.10 but no luck.Running conky from terminal i m taking the same messages (the minor ones) my backround becomes black and no conky at all.

 Any idea?

That's what I got, too.

I'm going to poke around the Kubuntu forums ... which you already knew about, of course :D ... and see if they have anything.

---

### Post by Valshar on 2009-02-26
Hi, I'm having trouble making Conky read the battery time left and percentage, I don't really know what to try. This is what I have on it:

```
${font Webdings:size=16}~${font}   Battery: ${alignr}${battery_time BAT0}
${font StyleBats:size=12} ${font}${tab 10} ${battery_percent BAT0}% ${battery_bar BAT0}
```

---

### Post by frogotronic on 2009-03-17
Hello,

I get a warning when I logout with conky running:  'Warning: These windows do not support "save current setup" and will have to be restarted manually next time you log in'

Any ideas how to fix this?

- CH

---

### Post by DarkReaper79 on 2009-03-20
New conky user here. So far so good, looking forward to editing this. Thanks!

---

### Post by Bruce M. on 2009-03-21
> **DarkReaper79 said:**
> New conky user here. So far so good, looking forward to editing this. Thanks!

Welcome to the wonderful, addictive, conky world.

We're here if you have any questions.

Have a nice day.
Bruce

---

### Post by DarkReaper79 on 2009-03-22
You are very right about being addictive:p I cant count how many I tried before I got one I liked, then edited some of it. Im sure this wont be end once I learn more.

---

### Post by Bruce M. on 2009-03-22
> **DarkReaper79 said:**
> You are very right about being addictive:p I cant count how many I tried before I got one I liked, then edited some of it. Im sure this wont be end once I learn more.

Have you tried any of K's Scripts? See my signature...

Here they are:

    * conkyDeluge
    * conkyEmail
    * conkyExaile
    * conkyForecast
    * conkyGoogleCalendar
    * conkyPidgin
    * conkyRhythmbox

Now they spice up conky a LOT!

---

### Post by DarkReaper79 on 2009-03-22
I used to have one conky with weather in it. I forgot who the person was that did it. But I am trying out conkyForecast. Other than stupid mistakes like, wrong spelling, and mixing up the location code, I got a basic one working. Now to get it to load at start up. I got the other conky to load at boot, but this one seem not to want to. Ill look into it deeper tomorrow.

---

### Post by Bruce M. on 2009-03-22
> **DarkReaper79 said:**
> I used to have one conky with weather in it. I forgot who the person was that did it. But I am trying out conkyForecast. Other than stupid mistakes like, wrong spelling, and mixing up the location code, I got a basic one working. Now to get it to load at start up. I got the other conky to load at boot, but this one seem not to want to. Ill look into it deeper tomorrow.

Check out my guide in my sig, it explains how to set up two or more conkys to start on boot.

---

### Post by DarkReaper79 on 2009-03-23
> **Bruce M. said:**
> Check out my guide in my sig, it explains how to set up two or more conkys to start on boot.

I finally got it. I already had the .startconky file, i edited the paths, it didnt work. Then I realised that the spelling was wrong on the forecast file](*,) Thanks for the help, Im sure Ill need more, when I get more into this.

---

### Post by Bruce M. on 2009-03-23
> **DarkReaper79 said:**
> I finally got it. I already had the .startconky file, i edited the paths, it didnt work. Then I realised that the spelling was wrong on the forecast file](*,) Thanks for the help, Im sure Ill need more, when I get more into this.

We'll be here. :)

---

### Post by KitChy on 2009-03-29
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/External}%   ${fs_bar 6 /media/External}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

That's my current conky script but when I go to run this, nothing happens. However, when I run it in the terminal, this is the output it get:
```
 conky
Conky: desktop window (14000ae) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
```

Any ideas on what's the problem?

---

### Post by DarkReaper79 on 2009-03-29
> **KitChy said:**
> ```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/External}%   ${fs_bar 6 /media/External}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

That's my current conky script but when I go to run this, nothing happens. However, when I run it in the terminal, this is the output it get:
```
 conky
Conky: desktop window (14000ae) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
```

Any ideas on what's the problem?


How does it look when you run it in the terminal? Is it ok? all the info there? If you want it to start at boot, you will need a startconky script.

---

### Post by KitChy on 2009-03-29
The 2nd part of my post shows what is displayed in terminal when I run "conky"

---

### Post by DarkReaper79 on 2009-03-29
here is one of mine, maybe you can find it useful.

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white
#own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
alignment middle_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 30

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
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

#colors
#white
color1 FFFFFF
# light blue
color2 6892C6
#Red
color3 F80707
TEXT
${color2}SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${color2}${font}   Kernel:  ${color1}${alignr}${kernel}
${color2}${font StyleBats:size=16}A${color2}${font}   CPU1: ${color1}${cpu cpu1}% ${color1}${alignr}${cpubar cpu1 8,60}
${color2}${font StyleBats:size=16}A${color2}${font}   CPU2: ${color1}${cpu cpu2}% ${alignr}${color1}${cpubar cpu2 8,60}
${color2}${font StyleBats:size=16}g${color2}${font}   RAM: ${color1}$memperc% ${alignr}${color1}${membar 8,60}
${color2}${font StyleBats:size=16}j${color2}${font}  SWAP: ${color1}$swapperc% ${alignr}${color1}${swapbar 8,60}
${color2}${font Webdings:size=16}~${color2}${font}  Battery: ${color1}${battery_percent BAT0}% ${alignr}${color1}${battery_bar 8,60 BAT0}
${color2}${font StyleBats:size=16}q${color2}${font}   Uptime: ${color1}${alignr}${color1}${uptime}

${color2}DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${color1}${time %A %d %Y}

${color2}HD ${hr 2}
${voffset 4}${color2}${font Pie charts for maps:size=14}7${font}   ${voffset -5}${color2}Root:
${voffset 4}${color1}${fs_used /}/${fs_size /}${alignr}${fs_bar 8,60 /}

${voffset 4}${color2}${font Pie charts for maps:size=14}7${font}   ${voffset -5}${color2}Home:
${voffset 4}${color1}${fs_used /home/darkreaper79}/${fs_size /home/darkreaper79} ${alignr}${fs_bar 8,60 /home/darkreaper79}

${voffset 4}${color2}${font Pie charts for maps:size=14}7${font}   ${voffset -5}${color2}My Book:
${voffset 4}${color1}${fs_used /media/My_Book}/${fs_size /media/My_Book} ${alignr}${fs_bar 8,60 /media/My_Book}


${color2}NETWORK ${hr 2}

${if_existing /proc/net/route wlan0}
${color2}${voffset -6}${font PizzaDude Bullets:size=14}O${color2}${font}   Up: ${color1}${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 3465A4 729FCF}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}U${color2}${font}   Down: ${color1}${downspeed wlan0} kb/s ${alignr}${color1}${downspeedgraph wlan0 8,60 3465A4 729FCF}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}N${color2}${font}   Upload: ${color1}${alignr}${totalup wlan0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}T${color2}${font}   Download: ${color1}${alignr}${totaldown wlan0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}Z${color2}${font}   Signal: ${color1}${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}a${color2}${font}   Local Ip: ${color1}${alignr}${addr wlan0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}b${color2}${font}   Public Ip: ${color1}${alignr}${execi 1 ~/.scripts/ip.sh}

${else}${if_existing /proc/net/route eth0}
${color2}${voffset -6}${font PizzaDude Bullets:size=14}O${color2}${font}   Up: ${color1}${upspeed eth0} kb/s ${alignr}${color1}${upspeedgraph eth0 8,60 3465A4 729FCF}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}U${color2}${font}   Down: ${color1}${downspeed eth0} kb/s ${alignr}${color1}${downspeedgraph eth0 8,60 3465A4 729FCF}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}N${color2}${font}   Upload: ${color1}${alignr}${totalup eth0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}T${color2}${font}   Download: ${color1}${alignr}${totaldown eth0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}a${color2}${font}   Local Ip: ${color1}${alignr}${addr eth0}
${color2}${voffset 4}${font PizzaDude Bullets:size=14}b${color2}${font}   Public Ip: ${color1}${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=16}4${color3}${font}   Network Unavailable
${endif}

---

### Post by DarkReaper79 on 2009-03-29
> **KitChy said:**
> The 2nd part of my post shows what is displayed in terminal when I run "conky"


Sorry, I meant on the screen, the layout of the conky itself, not what it lists in the terminal. I should of word it better.

---

### Post by KitChy on 2009-03-29
Nothing gets displayed. Nothing at all, Which I find weird.

---

### Post by DarkReaper79 on 2009-03-29
> **KitChy said:**
> Nothing gets displayed. Nothing at all, Which I find weird.

Try adding this before the TEXT section


# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

it seem to work for me before.

---

### Post by Th3Professor on 2009-04-12
Hi!

Could someone please help me with a "conky recipe" that would accompany these "ingredients":


[LIST]
[*]hostname
[/LIST]

[LIST]
[*]4 CPUs (quad core) - percent usages and temperatures
[/LIST]

[LIST]
[*]GPU - temperature(s)
[/LIST]

[LIST]
[*]fan speed (about 8 fans total, all are using about 3 fan plug-ins on mobo)
[/LIST]

[LIST]
[*]memory + swaps (percent usages)
[/LIST]

[LIST]
[*]disks (used/free + RWX activity, currently sda + md0 (or sda + dm-0,dm-1,dm-2), sde1 (external drive), & scd0 (dvd/cd); or literally these: sda1, sda5, sda6, sde1, mapper/vg0-01, mapper/vg0-02, mapper/vg0-03, scd0)
[/LIST]

[LIST]
[*]processes (w/ CPU + memory usages)
[/LIST]

[LIST]
[*]internet (download/upload totals+speeds, currently eth0 + various ports used with torrents)
[/LIST]

[LIST]
[*]calendar of current month (optional)
[/LIST]

[LIST]
[*]new email (optional (currently using evolution))
[/LIST]

[LIST]
[*]ups (back-up power supply (optional))
[/LIST]

[LIST]
[*]uptime (optional)
[/LIST]

[LIST]
[*]am I missing anything?
[/LIST]
...how do I include a terminal command line built in to conky (if it's even possible)?

...it also looks like I can monitor voltages, specifically (according to gkrellm) "Vcor1", "Vcor2", "+5V", "+12V", "-12V", "-5V", "Stby", and "Vbat"; they show various readings, though this one, "+3.3V", shows 0.0 ...why might someone want to monitor their voltages? If I do, how could I include that data in my conky?

---

### Post by miegiel on 2009-04-12
> **Th3Professor said:**
> Hi!

Could someone please help me with a "conky recipe" that would accompany these "ingredients":


[LIST]
[*]**hostname**
[/LIST]
I don't have that 1, check :
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

[LIST]
[*]4 **CPUs (quad core) - percent usages and temperatures**
[/LIST]
My dual core stuff:

${cpugraph cpu1 3f3f3f ffffff}
${cpugraph cpu2 3f3f3f ffffff}
${cpubar cpu1}
${cpubar cpu2}
cpu 0 = ${cpu cpu1}%  cpu 1 = ${cpu cpu2}% ${alignr}load = ${loadavg}

[LIST]
[*]**GPU - temperature(s)**
[/LIST]
requires lm-sesors, my GPU/PCIe sensor is k8temp-pci-00c3

gpu  = ${hwmon 0 temp 1}C ${hwmon 0 temp 2}C ${hwmon 0 temp 3}C ${hwmon 0 temp 4}C

[LIST]
[*]**fan speed (about 8 fans total, all are using about 3 fan plug-ins on mobo)**
[/LIST]
requires lm-sesors again , my motherboard sensor is it8716-isa-0228 and only 3 of my 6 fan connectors can read the RPMs

fan  = ${hwmon 1 fan 1}rpm ${hwmon 1 fan 2}rpm ${hwmon 1 fan 3}rpm (cpu/ex1/ex2)

[LIST]
[*]**memory + swaps (percent usages)**
[/LIST]
$membar
ram =  $mem ($memperc%)   ${alignr}swap = $swap ($swapperc%)

[LIST]
[*]**disks (used/free + RWX activity**, currently sda + md0 (or sda + dm-0,dm-1,dm-2), sde1 (external drive), & scd0 (dvd/cd); or literally these: sda1, sda5, sda6, sde1, mapper/vg0-01, mapper/vg0-02, mapper/vg0-03, scd0)
[/LIST]
Disk stuff :

${fs_bar 6 /}
root used: ${fs_used} ${alignr}${fs_free}${fs_free_perc}% free
${fs_bar 6 /home/}
home used: ${fs_used /home/} ${alignr}${fs_free /home/} ${fs_free_perc /home/}% free
${fs_bar 6 /media/data/}
data used: ${fs_used /media/data/} ${alignr}${fs_free /media/data/} ${fs_free_perc /media/data/}% free
${diskiograph_write /dev/sda 25,320 3f3f3f ffffff}
${diskiograph_read /dev/sda 25,320 3f3f3f ffffff}
sda write: ${diskio_write /dev/sda} read: ${diskio_read /dev/sda} total: ${diskio /dev/sda}
${diskiograph_write /dev/md0 25,320 3f3f3f ffffff}
${diskiograph_read /dev/md0 25,320 3f3f3f ffffff}
md0 write: ${diskio_write /dev/md0} read: ${diskio_read /dev/md0} total: ${diskio /dev/md0}


[LIST]
[*]**processes (w/ CPU + memory usages)**
[/LIST]
See above and :

${top name 1} ${top cpu 1} ${top mem 1} ${top pid 1} (c/m/p)
${top name 2} ${top cpu 2} ${top mem 2} ${top pid 2}
${top name 3} ${top cpu 3} ${top mem 3} ${top pid 3}

${top_mem name 1} ${top_mem cpu 1} ${top_mem mem 1} ${top_mem pid 1} (c/m/p)
${top_mem name 2} ${top_mem cpu 2} ${top_mem mem 2} ${top_mem pid 2}
${top_mem name 3} ${top_mem cpu 3} ${top_mem mem 3} ${top_mem pid 3}

[LIST]
[*]**internet (download/upload totals+speeds**, currently eth0 + various ports used with torrents)
[/LIST]
Graphs and numbers

${upspeedgraph eth2 25,320 3f3f3f ffffff}
${downspeedgraph eth2 25,320 3f3f3f ffffff}
${addr eth2} +${upspeed eth2}kB/s ${totalup eth2} -${downspeed eth2}kB/s ${totaldown eth2}
${upspeedgraph eth1 25,320 3f3f3f ffffff}
${downspeedgraph eth1 25,320 3f3f3f ffffff}
${addr eth1} +${upspeed eth1}kB/s ${totalup eth1} -${downspeed eth1}kB/s ${totaldown eth1}

TCP/IP connections

${tcp_portmon 1 65535 rhost 0}
${tcp_portmon 1 65535 lport 0} ${tcp_portmon 1 65535 rport 0} ${tcp_portmon 1 65535 rip 0}
${tcp_portmon 1 65535 rhost 1}
${tcp_portmon 1 65535 lport 1} ${tcp_portmon 1 65535 rport 1} ${tcp_portmon 1 65535 rip 1}
${tcp_portmon 1 65535 rhost 2}
${tcp_portmon 1 65535 lport 2} ${tcp_portmon 1 65535 rport 2} ${tcp_portmon 1 65535 rip 2}
${tcp_portmon 1 65535 rhost 3}
${tcp_portmon 1 65535 lport 3} ${tcp_portmon 1 65535 rport 3} ${tcp_portmon 1 65535 rip 3}
${tcp_portmon 1 65535 rhost 4}
${tcp_portmon 1 65535 lport 4} ${tcp_portmon 1 65535 rport 4} ${tcp_portmon 1 65535 rip 4}
${tcp_portmon 1 65535 rhost 5}
${tcp_portmon 1 65535 lport 5} ${tcp_portmon 1 65535 rport 5} ${tcp_portmon 1 65535 rip 5}
${tcp_portmon 1 65535 rhost 6}
${tcp_portmon 1 65535 lport 6} ${tcp_portmon 1 65535 rport 6} ${tcp_portmon 1 65535 rip 6}
${tcp_portmon 1 65535 rhost 7}
${tcp_portmon 1 65535 lport 7} ${tcp_portmon 1 65535 rport 7} ${tcp_portmon 1 65535 rip 7}
${tcp_portmon 1 65535 rhost 8}
${tcp_portmon 1 65535 lport 8} ${tcp_portmon 1 65535 rport 8} ${tcp_portmon 1 65535 rip 8}
${tcp_portmon 1 65535 rhost 9}
${tcp_portmon 1 65535 lport 9} ${tcp_portmon 1 65535 rport 9} ${tcp_portmon 1 65535 rip 9}
${tcp_portmon 1 65535 rhost 10}
${tcp_portmon 1 65535 lport 10} ${tcp_portmon 1 65535 rport 10} ${tcp_portmon 1 65535 rip 10}
${tcp_portmon 1 65535 rhost 11}
${tcp_portmon 1 65535 lport 11} ${tcp_portmon 1 65535 rport 11} ${tcp_portmon 1 65535 rip 11}
${tcp_portmon 1 65535 rhost 12}
${tcp_portmon 1 65535 lport 12} ${tcp_portmon 1 65535 rport 12} ${tcp_portmon 1 65535 rip 12}
${tcp_portmon 1 65535 rhost 13}
${tcp_portmon 1 65535 lport 13} ${tcp_portmon 1 65535 rport 13} ${tcp_portmon 1 65535 rip 13}
${tcp_portmon 1 65535 rhost 14}
${tcp_portmon 1 65535 lport 14} ${tcp_portmon 1 65535 rport 14} ${tcp_portmon 1 65535 rip 14}
${tcp_portmon 1 65535 rhost 15}
${tcp_portmon 1 65535 lport 15} ${tcp_portmon 1 65535 rport 15} ${tcp_portmon 1 65535 rip 15}

[LIST]
[*]**calendar of current month** (optional)
[/LIST]
Don't use conky for that, sorry :) see conky links above

[LIST]
[*]**new email** (optional (currently using evolution))
[/LIST]
Don't use conky for that, sorry :) see conky links above

[LIST]
[*]**ups** (back-up power supply (optional))
[/LIST]
Same :twisted:

[LIST]
[*]**uptime** (optional)
[/LIST]
I don't need that either, see links again.

There :) you will need to edit some stuff to match your machine of course.
Attached a screenshot and my .conkyrc (renamed as .txt)

---

### Post by Bruce M. on 2009-04-12
> **KitChy said:**
> Nothing gets displayed. Nothing at all, Which I find weird.

When you open a terminal and type:
```
conky
```
what it will display is the default conky that comes with the program **or** ~/.conkyrc (a hidden file in your /home directory).

If you have created a conky file someplace else:
```
conky
```
will not find it.

Try:
```
conky -c /path_to/your_conky_file &
```
mine looks like:
```
conky -c ~/Conky/conkymain &
```

Have a nice day.
Bruce

---

### Post by spartan1011 on 2009-04-12
Great post... first .conkyrc file that I have tried that has worked with minimal tweaking. Keep up the good work.

---

### Post by Th3Professor on 2009-04-13
> **miegiel said:**
> 
My dual core stuff:

${cpugraph cpu1 3f3f3f ffffff}
${cpugraph cpu2 3f3f3f ffffff}
${cpubar cpu1}
${cpubar cpu2}
cpu 0 = ${cpu cpu1}%  cpu 1 = ${cpu cpu2}% ${alignr}load = ${loadavg}

These are working nice, thank you. :)

Is there a way to monitor CPU temps?

> **miegiel said:**
> requires lm-sesors, my GPU/PCIe sensor is k8temp-pci-00c3

gpu  = ${hwmon 0 temp 1}C ${hwmon 0 temp 2}C ${hwmon 0 temp 3}C ${hwmon 0 temp 4}C

gkrellm appears to be showing temps for cpu & gpu, though I don't know if I have lm-sensors runnin' for that.

(I'm basically trying to take all of the readings/monitoring of data that's showing in gkrellm and move it over to conky.)

I tried the above code for GPU temps but it didn't work.

Is there a way to monitor GPU fan?

> **miegiel said:**
> 
requires lm-sesors again , my motherboard sensor is it8716-isa-0228 and only 3 of my 6 fan connectors can read the RPMs

fan  = ${hwmon 1 fan 1}rpm ${hwmon 1 fan 2}rpm ${hwmon 1 fan 3}rpm (cpu/ex1/ex2)

These readings (fan speeds) are working nice. :)

> **miegiel said:**
> 
$membar
ram =  $mem ($memperc%)   ${alignr}swap = $swap ($swapperc%)

This (memory usage/%/etc.) is also working nice.

> **miegiel said:**
> 
Disk stuff :

${fs_bar 6 /}
root used: ${fs_used} ${alignr}${fs_free}${fs_free_perc}% free
${fs_bar 6 /home/}
home used: ${fs_used /home/} ${alignr}${fs_free /home/} ${fs_free_perc /home/}% free
${fs_bar 6 /media/data/}
data used: ${fs_used /media/data/} ${alignr}${fs_free /media/data/} ${fs_free_perc /media/data/}% free
${diskiograph_write /dev/sda 25,320 3f3f3f ffffff}
${diskiograph_read /dev/sda 25,320 3f3f3f ffffff}
sda write: ${diskio_write /dev/sda} read: ${diskio_read /dev/sda} total: ${diskio /dev/sda}
${diskiograph_write /dev/md0 25,320 3f3f3f ffffff}
${diskiograph_read /dev/md0 25,320 3f3f3f ffffff}
md0 write: ${diskio_write /dev/md0} read: ${diskio_read /dev/md0} total: ${diskio /dev/md0}

...not having a lot of luck with this.
So far I'm only able to get readings from / (sda), which also houses "home".
I'm also able to see the read/write data on sda.
...not having much luck with the md0 though.
...and no luck with the external hard drive.

Here's a look at what's mounted where (or at least the main things)...
/ --> /dev/sda5
/studio/workspace --> /dev/sda6
/studio/vault --> /dev/mapper/vg0-vault
/zone --> /dev/mapper/vg0-zone
/nomad --> /dev/mapper/vg0-nomad
/media/My Book --> /dev/sde1

I've tried variations of those, for the "My Book" I tried "My\ Book" to get the space in there, tried renaming it without a space but the external drive wouldn't let me. I've tried the mappers without the "-(name)", without the "vg0". Though even sda6 wasn't reading, it seems like it only wants to display info on sda (not partitions within). I'm not sure. (Pretty confused on this bit.)

> **miegiel said:**
> 
${top name 1} ${top cpu 1} ${top mem 1} ${top pid 1} (c/m/p)
${top name 2} ${top cpu 2} ${top mem 2} ${top pid 2}
${top name 3} ${top cpu 3} ${top mem 3} ${top pid 3}

${top_mem name 1} ${top_mem cpu 1} ${top_mem mem 1} ${top_mem pid 1} (c/m/p)
${top_mem name 2} ${top_mem cpu 2} ${top_mem mem 2} ${top_mem pid 2}
${top_mem name 3} ${top_mem cpu 3} ${top_mem mem 3} ${top_mem pid 3}

This is working nice, I went ahead and added a 4th one in their for both top cpu usage and top memory usage.

> **miegiel said:**
> 
Graphs and numbers

${upspeedgraph eth2 25,320 3f3f3f ffffff}
${downspeedgraph eth2 25,320 3f3f3f ffffff}
${addr eth2} +${upspeed eth2}kB/s ${totalup eth2} -${downspeed eth2}kB/s ${totaldown eth2}
${upspeedgraph eth1 25,320 3f3f3f ffffff}
${downspeedgraph eth1 25,320 3f3f3f ffffff}
${addr eth1} +${upspeed eth1}kB/s ${totalup eth1} -${downspeed eth1}kB/s ${totaldown eth1}

This is working nice. :) I'm only using eth0, so I've just got it set to that (no wireless or alternate wireds).

> **miegiel said:**
> 
TCP/IP connections

${tcp_portmon 1 65535 rhost 0}
${tcp_portmon 1 65535 lport 0} ${tcp_portmon 1 65535 rport 0} ${tcp_portmon 1 65535 rip 0}
${tcp_portmon 1 65535 rhost 1}
${tcp_portmon 1 65535 lport 1} ${tcp_portmon 1 65535 rport 1} ${tcp_portmon 1 65535 rip 1}
${tcp_portmon 1 65535 rhost 2}
${tcp_portmon 1 65535 lport 2} ${tcp_portmon 1 65535 rport 2} ${tcp_portmon 1 65535 rip 2}
${tcp_portmon 1 65535 rhost 3}
${tcp_portmon 1 65535 lport 3} ${tcp_portmon 1 65535 rport 3} ${tcp_portmon 1 65535 rip 3}
${tcp_portmon 1 65535 rhost 4}
${tcp_portmon 1 65535 lport 4} ${tcp_portmon 1 65535 rport 4} ${tcp_portmon 1 65535 rip 4}
${tcp_portmon 1 65535 rhost 5}
${tcp_portmon 1 65535 lport 5} ${tcp_portmon 1 65535 rport 5} ${tcp_portmon 1 65535 rip 5}
${tcp_portmon 1 65535 rhost 6}
${tcp_portmon 1 65535 lport 6} ${tcp_portmon 1 65535 rport 6} ${tcp_portmon 1 65535 rip 6}
${tcp_portmon 1 65535 rhost 7}
${tcp_portmon 1 65535 lport 7} ${tcp_portmon 1 65535 rport 7} ${tcp_portmon 1 65535 rip 7}
${tcp_portmon 1 65535 rhost 8}
${tcp_portmon 1 65535 lport 8} ${tcp_portmon 1 65535 rport 8} ${tcp_portmon 1 65535 rip 8}
${tcp_portmon 1 65535 rhost 9}
${tcp_portmon 1 65535 lport 9} ${tcp_portmon 1 65535 rport 9} ${tcp_portmon 1 65535 rip 9}
${tcp_portmon 1 65535 rhost 10}
${tcp_portmon 1 65535 lport 10} ${tcp_portmon 1 65535 rport 10} ${tcp_portmon 1 65535 rip 10}
${tcp_portmon 1 65535 rhost 11}
${tcp_portmon 1 65535 lport 11} ${tcp_portmon 1 65535 rport 11} ${tcp_portmon 1 65535 rip 11}
${tcp_portmon 1 65535 rhost 12}
${tcp_portmon 1 65535 lport 12} ${tcp_portmon 1 65535 rport 12} ${tcp_portmon 1 65535 rip 12}
${tcp_portmon 1 65535 rhost 13}
${tcp_portmon 1 65535 lport 13} ${tcp_portmon 1 65535 rport 13} ${tcp_portmon 1 65535 rip 13}
${tcp_portmon 1 65535 rhost 14}
${tcp_portmon 1 65535 lport 14} ${tcp_portmon 1 65535 rport 14} ${tcp_portmon 1 65535 rip 14}
${tcp_portmon 1 65535 rhost 15}
${tcp_portmon 1 65535 lport 15} ${tcp_portmon 1 65535 rport 15} ${tcp_portmon 1 65535 rip 15}

...no luck with this. :(

The stuff that is working already... thank you! :p ...the stuff that isn't working, any ideas what I can do to get them to work?

---

### Post by Bruce M. on 2009-04-14
Hi Folks.

Well it's official, [Conky Hardcore!]("http://conky.linux-hardcore.com/") is open for business. Keep in mind, it's young, under-development and we still have a lot of work to do on it. I personal have a ton of material I have to put up and I know uncertain has a lot more.

Unless uncertain and I specifically state that the work is ours, all information has been gathered from various forums. Of which this thread is the biggest contributor. Many other "forums" direct their conky requests right here, to this specific thread, so it is understandable as to why.

Our "Welcome to Conky Hardcore!" message:

> We’re putting together an encyclopaedia of sorts - dedicated to the Conky system monitor and all the tricks you can make it do. Long have we all wished that there was one place where we could go to find out what we needed to know about Conky and how to make it do what we want. Over time, you’re going to see this grow into that place.

For now, since both your hosts (Bruce & Uncertain) primarily use Debian based systems, this is going to be a little bit Debian-centric. Rest assured, we’ve spent a fair amount of time combing the Conky-threads in Arch, OpenSuse, Fedora, Gentoo, DreamLinux, Ubuntu and other forums, all in the spirit of making this the most complete repository of Conky knowledge around.

What this is not going to be is a help line. People writing comments and emails that contain the phrases, *“How do I …”* or, *“Can someone tell me how to …”* will either be redirected to the various forum threads where all that sort of discussion takes place, *or be ignored/deleted*. Our first priority is to gather the information to put here so you have that “one place” to come to. After all there are Conky threads in most Linux Forums, duplicating those types of threads here will result in this “encyclopaedia” of ideas and samples of how to do things with Conky loosing it’s value as people will have to wade through hundreds of posts to get what they want.

What this is going to be is a place to collect screen shots, scripts, example configurations (from the simple to the obscene), and a showcase for some of the more unique, artistic and creative configurations we’ve seen. We’re going to provide all the above, plus links to even more resources so that everybody from the total “newbie” to the veterans can come here and find something useful.

Unfortunately, when putting together a collection of information like this, with all these different sources, it’s not always possible to credit the original author for their work. Generally, if either of us knows for sure where a script or piece of code came from, that person will be duly credited. If any doubts or uncertainty (or general lack of information) exist as to who may have been the original innovator behind a particular idea, we will leave it uncredited. If you want to claim something we’re displaying as your work, just drop us a line and provide a link to a forum or blog post that shows where and when you came up with the idea, and we’ll see what we can work out.

If you have a new or different way of doing something you see displayed, have a fresh or unique Conky configuration you’d like to share with the world, or have links to other resources that we may have missed, please drop us a line and pass it along.

We hope you enjoy the site!
Bruce & Uncertain

Have a nice day, conkistadors
Bruce

---

### Post by Th3Professor on 2009-04-15
> **Bruce M. said:**
> Hi Folks.

Well it's official, [Conky Hardcore!]("http://conky.linux-hardcore.com/") is open for business. Keep in mind, it's young, under-development and we still have a lot of work to do on it. I personal have a ton of material I have to put up and I know uncertain has a lot more.

Unless uncertain and I specifically state that the work is ours, all information has been gathered from various forums. Of which this thread is the biggest contributor. Many other "forums" direct their conky requests right here, to this specific thread, so it is understandable as to why.

Our "Welcome to Conky Hardcore!" message:



Have a nice day, conkistadors
Bruce

Hey cool site. Maybe you could include these in the howto pages?:


[LIST]
[*]How to monitor CPU temps.
[/LIST]

[LIST]
[*]How to monitor GPU temps.
[/LIST]

[LIST]
[*]How to monitor GPU fan.
[/LIST]

[LIST]
[*]How to monitor disks (used/free & read/write) like these:
[/LIST]
[INDENT]
[LIST]
[*]/ --> /dev/sda5 (normal partition)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /studio/workspace --> /dev/sda6 (normal partition)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /studio/vault --> /dev/mapper/vg0-vault (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /zone --> /dev/mapper/vg0-zone (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /nomad --> /dev/mapper/vg0-nomad (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /media/My Book --> /dev/sde1 (external drive)
[/LIST]
[/INDENT]
[LIST]
[*]How to monitor TCP/IP connections (as with torrent transfers)
[/LIST]
...that is... those are the things I'm currently having difficulties getting to work in conky.

---

### Post by Th3Professor on 2009-04-16
Any ideas/help on the subjects below?

> **Th3Professor said:**
> Hey cool site. Maybe you could include these in the howto pages?:


[LIST]
[*]How to monitor CPU temps.
[/LIST]

[LIST]
[*]How to monitor GPU temps.
[/LIST]

[LIST]
[*]How to monitor GPU fan.
[/LIST]

[LIST]
[*]How to monitor disks (used/free & read/write) like these:
[/LIST]
[INDENT]
[LIST]
[*]/ --> /dev/sda5 (normal partition)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /studio/workspace --> /dev/sda6 (normal partition)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /studio/vault --> /dev/mapper/vg0-vault (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /zone --> /dev/mapper/vg0-zone (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /nomad --> /dev/mapper/vg0-nomad (raid5+lvm)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*] /media/My Book --> /dev/sde1 (external drive)
[/LIST]
[/INDENT]
[LIST]
[*]How to monitor TCP/IP connections (as with torrent transfers)
[/LIST]
...that is... those are the things I'm currently having difficulties getting to work in conky.

Thanks!

---

### Post by Bruce M. on 2009-04-16
> **Th3Professor said:**
> Any ideas/help on the subjects below?

Thanks!

[LIST]
[*]How to monitor CPU temps.
[*]How to monitor GPU temps.
[*]How to monitor GPU fan.
[/LIST]
[lm-sensors]("http://www.lm-sensors.org/"), get it from the repos. Then run:
```
sudo sensors-detect
```
answer yes (default) even to the last one that defaults No.

Now you need to have lines similar to but not these in conky:

```
CPU: ${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCPU.sh}°
Core: ${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCore.sh}°
M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempMB.sh}°
GPU: ${execpi 8 sh -c "DISPLAY=:0.0 nvidia-settings -q gpucoretemp | grep Attribute | cut --characters 41-42" | xargs ~/Conky/scripts/ColorTempGPU.sh}°
```

I say "similar to" because I'm using the colorize scripts from Crinos and I needed heavy help with the grep command.  Each machine is different.

[LIST]
[*]How to monitor disks (used/free & read/write) like these:
[/LIST]

These first three are on my hda:
```
Root: ${fs_free_perc /}% ${fs_free /} ${fs_used /}
Home: ${fs_free_perc /home/bruloo}% ${fs_free /home/bruloo} ${fs_used /home/bruloo}
ubl: ${fs_free_perc /media/ubl}% ${fs_free /media/ubl} ${fs_used /media/ubl}
```
**/media/ubl** is a partition on the drive I use for personal stuff.

```
b21: {fs_free_perc /media/b21}% ${fs_free /media/b21} ${fs_used /media/b21}
b22: ${fs_free_perc /media/b22}% ${fs_free /media/b22} ${fs_used /media/b22}
```
**b21 and b22** are 20GB partitions on my 40GB second drive, hd**b**, I use for backups and images.

That's the used and free, I don't use read/write but the commands are:

> **diskio** 	(device) 	 Displays current disk IO. Device is optional, and takes the form of sda for /dev/sda. Individual partitions are allowed.
**diskiograph** 	(device) (height),(width) (gradient colour 1) (gradient colour 2) (scale) 	Disk IO graph, colours defined in hex, minus the #. If scale is non-zero, it becomes the scale for the graph.
**diskio_read** 	(device) 	Displays current disk IO for reads. Device as in diskio.
**diskiograph_read** 	(device) (height),(width) (gradient colour 1) (gradient colour 2) (scale) 	Disk IO graph for reads, colours defined in hex, minus the #. If scale is non-zero, it becomes the scale for the graph. Device as in diskio.
**diskio_write** 	(device) 	Displays current disk IO for writes. Device as in diskio.

That's a start. Wish I could help with grep, but I'm at a loss.

Why not ask here: [http://ubuntuforums.org/showthread.php?t=281865&page=655](http://ubuntuforums.org/showthread.php?t=281865&page=655)

**[COLOR="Red"][SIZE="5"]EDIT:[/SIZE][/COLOR]** I found the post that explains this "sensors" better, by one of my mentors; John.Michael.Kane, done way back in 2005: [Here is how you can gather your cpu video card fan speed.]("http://ubuntuforums.org/showpost.php?p=5045934&postcount=2448"). There, now I feel better.

Have a nice day.
Bruce

---

### Post by Th3Professor on 2009-04-17
Okay excellent help thank you...
I'm now another step closer to getting it all working.

It's interesting how the disk drives are meant to be used, in the used/free commands it works with /directory-name but in the diskio type commands it appears to only work with /dev names. I tried sda5, sda6, sde1 with diskio/diskiograph but it would only display read/write changes on sda (apparently the whole drive). I was unable to get the I/O to display for the /dev/mapper volume group.

I'm still currently having difficulties getting these to work:

[LIST]
[*]CPU temps
[*]GPU temps+fan
[*]diskio/diskiograph (read/write) for sda5, sda6, mapper/vg0-vault, and sde1
[*]TCP/IP connections (for torrent transfers)
[/LIST]
Also, what are the units in the "cpu average" readings?
(They apparently cycle every 1, 5, and 15 minutes.)

Thank you!

EDIT:
wow, just saw that link with the edit update in previous reply, leading to:
[http://ubuntuforums.org/showpost.php?p=5045934&postcount=2448](http://ubuntuforums.org/showpost.php?p=5045934&postcount=2448)
(I'll look into that for the gpu fan. ty)

---

### Post by l-x-l on 2009-04-19
Hello all,

This is my very 1st post here. I'm a new Ubuntu (Ibex) user (2 weeks) via Wubi. I followed the instructions in the 1st post. But when I tried running conky I get the message. I'm stuck & not sure what to do next. Any help would be appreciated.

```

Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (1a6) is root window
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
```


Edit: I see '/media/sda1' in the OP's '.conkyrc' file but I don't have it in my root directory. Should I? When I remove that line refering to '/media/sda1' from the code conky still doesn't work. I get the same message in the terminal minus that 1st line.

---

### Post by Bruce M. on 2009-04-19
> **l-x-l said:**
> Hello all,

This is my very 1st post here. I'm a new Ubuntu (Ibex) user (2 weeks) via Wubi. I followed the instructions in the 1st post. But when I tried running conky I get the message. I'm stuck & not sure what to do next. Any help would be appreciated.

First and foremost - Welcome to the Ubuntu Forums and Conky.

Check the HowTo in my sig and see if anything there can help you.

Also if you do mot have a "/media/sda1" then the line should not be in the conky you are using.

Have a nice day.
Bruce

---

### Post by l-x-l on 2009-04-19
> **Bruce M. said:**
> First and foremost - Welcome to the Ubuntu Forums and Conky.

Check the HowTo in my sig and see if anything there can help you.

Also if you do mot have a "/media/sda1" then the line should not be in the conky you are using.

Have a nice day.
Bruce


Thank you much. After a few hours of toying with it, I did just that & removed the '/media/sda1'. I also figured why I thought conky wasn't running. In fact, Conky was running afterall. However, for some reason the line "own_window_type override" didn't allow it to appear on my screen, even though it was running. When I changed it to 'own_window_type normal', then I could see conky.

Wow... only a few painful hours to figure that out. What fun. I can already tell that this project will be a labor of love.

My next task is to make conky transparent on all 4 of my desktops with different wallpapers.

---

### Post by Kawaiii on 2009-05-05
Hello,
I am new to conky and was setting up a script.  I would like to add a RSS feed, but the site often has very long headlines that stretch conky horizontally.  I can set the maximum width, but that cuts off the rest of the headline.  Is there a way to make there be a word wrap so it continues on the next line?

Also, how do I make my total uploads and downloads be for the past 24-hour period? So that time period is always the past 24 hours.

---

### Post by maheshasolkar on 2009-05-05
> **Kawaiii said:**
> I would like to add a RSS feed, but the site often has very long headlines that stretch conky horizontally.  I can set the maximum width, but that cuts off the rest of the headline.  Is there a way to make there be a word wrap so it continues on the next line?

If you are using execi to fetch the feed, you could pipe your fetch command to 'fold':

```
${execi 300 fetch_feed | fold --width=40}
```

This will wrap the feed text wider than 40 columns.

---

### Post by Kawaiii on 2009-05-05
> **maheshasolkar said:**
> If you are using execi to fetch the feed, you could pipe your fetch command to 'fold':

```
${execi 300 fetch_feed | fold --width=40}
```

This will wrap the feed text wider than 40 columns.

execi using conky_rss.sh doesn't seem to get the RSS titles right.  For example, [inputting Gizmodo's xml feed]("http://feeds.gawker.com/gizmodo/excerpts.xml") gave all sorts of weird extra stuff.  And a twitter feed that relies on line breaks suddenly doesn't show the extra line.  using just ```
${rss http://url 30 item_titles 2} 
``` displayed the titles correctly, but without folding. However, the rss command ignores fold. Is there a way to get best of both worlds?

---

### Post by Bloemetjesgordijn on 2009-05-06
Hi 
Thx for the how to

I followed you instructions, Conky start up but I am getting conky as a seperate application in my wallpaper.

Looks like (sort of):

[IMG]http://www.gnome-look.org/CONTENT/content-pre1/92328-1.png[/IMG]

and not the conky I want (conky as a shadow in my wallpaper, like yours):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96421&d=1229299247[/IMG]

What did I do wrong??? Can you help me??

Cheerz

Bloemetjesgordijn

---

### Post by Kawaiii on 2009-05-06
Sorry in advance, I'm still a linux noob.
I haven't been able to find a way that lets me display RSS feeds correctly (some give extra code in the title, some need to be multiple lines long with linebreaks) AND have wordwrap, I'm not too sure what to do with that.

Also, looking at some of the configs that I am seeing floating around, some people are able to have a bandwidth total for the week, month, etc. Is there a way to do this for the previous 24 hours? My bandwidth is limited to 2 GB/24 hours, upload and download, and I'd like an easy way to keep track of this with conky, if possible.

Thanks.  I'm not sure what sort of information you might need from me to help, so just ask.

---

### Post by UJM on 2009-05-14
I love the config in the first post by seldon77 - "very functional conky config", when I'm using bittorrent the network display shows my upload / download speeds and also the bar-graphs (one red & one green) change in intensity from dark to light it's very very clever!

---

### Post by sophtpaw on 2009-05-21
Hi,

As you can see from my [screenshot]("http://img513.imageshack.us/my.php?image=screenshotiws.png") conky is sitting slightly to high. What is it i need to adjust in .conkyrc to bring it down a little?

thank you

---

### Post by sophtpaw on 2009-05-21
....Also, conky covers any application that goes into its view. Would like to set it so that it stays underneath like background

---

### Post by Bruce M. on 2009-05-21
> **Kawaiii said:**
> Also, looking at some of the configs that I am seeing floating around, some people are able to have a bandwidth total for the week, month, etc. Is there a way to do this for the previous 24 hours? My bandwidth is limited to 2 GB/24 hours, upload and download, and I'd like an easy way to keep track of this with conky, if possible.

For Yesterday:

```
${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 140} ${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 205} ${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
```

Have a nice day.
Bruce

---

### Post by dccrens on 2009-05-25
Looking for a little help on startup script. 

I have conky running on several computers running Intrepid. I recently upgraded one of them to Jaunty. I am very familiar with many forms of Linux, and Unix, so know a little... I have the following in my ~/Conky/conkymain 

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external Scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#
# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#
# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_used           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_used_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_free           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	platform               (dev), type, n  platform sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one platform  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# Use Xft?
use_xft yes
xftfont HandelGotD:size=8
#xftfont DejaVu Sans:size=8
#xftfont Liberation Sans:size=9
#xftfont Terminus:size=8
#xftfont Liberation Sans:size=9
override_utf8_locale yes
text_buffer_size 2048

# Text alpha when using Xft
#xftalpha 0.8
xftalpha 0.5

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

#Set Maximum Width
maximum_width 270

# Minimum size of text area
minimum_size 250 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# shadecolor black
default_outline_color black
default_shade_color black
#own_window_colour white

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# fiddle with window
use_spacer left

#Default font
font arial

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 50

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
override_utf8_locale yes

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer left

#Use short units for disk size (G = Gigabyte , M = Megabyte, etc) - Doesn't seem to work 
#short_units on

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color0 red
color1 GreenYellow
color2 turquoise
color3 gold
color4 green
color5 white
color6 MediumSpringGreen
color7 orange
color8 DarkSlateBlue
color9 lightgreen


#Not being used
#  ${color4}C:  ${color5}${fs_used /media/C} / ${fs_free /media/C}  ${color8}${fs_bar 10 /media/C}${color5}${offset -40}${fs_used_perc /media/C}%${color}
#  ${color4}D:  ${color5}${fs_used /media/D} / ${fs_free /media/D}  ${color8}${fs_bar 10 /media/D}${color5}${offset -40}${fs_used_perc /media/D}%${color}
#  ${color4}E:  ${color5}${fs_used /media/E} / ${fs_free /media/E}  ${color8}${fs_bar 10 /media/E}${color5}${offset -40}${fs_used_perc /media/E}%${color}
#  ${color4}F:  ${color5}${fs_used /media/F} / ${fs_free /media/F}  ${color8}${fs_bar 10 /media/F}${color5}${offset -40}${fs_used_perc /media/F}%${color}
#  ${color4}G:  ${color5}${fs_used /media/G} / ${fs_free /media/G}  ${color8}${fs_bar 10 /media/G}${color5}${offset -40}${fs_used_perc /media/G}%${color}
#${if_mounted /media/USB_L}  ${color4}USB_L:  ${color5}${fs_used /media/L} / ${fs_free /media/L}  ${color8}${fs_bar 10 /media/L}${color5}${offset -40}${fs_used_perc /media/L}%${color}${endif}
#${if_mounted /media/USB_M}  ${color4}USB_M:  ${color5}${fs_used /media/M} / ${fs_free /media/M}  ${color8}${fs_bar 10 /media/M}${color5}${offset -40}${fs_used_perc /media/M}%${color}${endif}
#${if_mounted /media/USB_N}  ${color4}USB_N:  ${color5}${fs_used /media/N} / ${fs_free /media/N}  ${color6}${fs_bar 10 /media/N}${color5}${offset -40}${fs_used_perc /media/N}%${color}${endif}

# Text stuff
TEXT
${font :size=12}${color2}${alignc}${time %H:%M}$color$font
${font :size=10}${color tomato}${alignc}${time %A, %d %b. %Y}$color${font :size=8}
${color7}SYSTEM ${hr 2}${color}
  ${color2}${pre_exec echo $USERNAME} on $nodename 
  $sysname $kernel
  ${color tomato}Intel Core2 X6800 ${color4} @ ${color0}${freq_dyn_g}Gz$color 
  ${color4}UpTime: ${color0}$uptime${color}
${color7}PENDING MAIL ${hr 2}${color}
${if_up eth1}  ${color4}GMAIL: ${execi 60 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=XXXXX --password=XXXXX --ssl --mailinfo=2} ${endif}
${color7}TEMPS & CPU LOAD ${hr 2}${color}
  ${color0}${cpugraph cpu1 15, 120 000000 FF4900}${color} ${offset -90}${voffset 5}${font :size=8}${color5}Load:${cpu cpu1}% ${color}${font :size=8}                   ${voffset -5}${color0}${cpugraph cpu2 15, 0 000000 FF4900}${color} ${offset -90}${voffset 5}${font :size=8}${color5}Load:${cpu cpu2}% ${color}${font :size=8}
  ${color4}Core0 Temp: ${color0}${execi 8 sensors | grep -A 1 'Core 0' | cut -c15-16 | sed '/^$/d'}C  ${alignr}${color4}Core1 Temp: ${color0}${execi 8 sensors | grep -A 1 'Core 1' | grep -A 1 'crit' | cut -c15-16 | sed '/^$/d'}C
  ${color4}CPU Temp: ${color5}${hwmon 1 temp 2}C ${alignr}${color4}GPU Temp: ${color5}${execi 300 nvidia-settings -q GPUCoreTemp | grep "caver" | cut -d ':' -f3 | cut -d ' ' -f2 | cut -d '.' -f1 ;}C
  ${color4}CPU Fan Spd: ${color5}${hwmon 1 fan 2} rpm ${alignr}${color4}${alignr}${color4}Drive sda: ${color5}${hddtemp /dev/sda}
  ${color4}Vcore: ${color5}${hwmon 1 in 0}V ${alignr}${color4}Drive sdb: ${color5}${hddtemp /dev/sdb}
  ${color4}MB Temp: ${color5}${hwmon 1 temp 3}C ${alignr}${color4}MB Fan Spd: ${color5}${hwmon 1 fan 3} rpm
${color7}MEMORY / DISK ${hr 2}$color
  ${color4}RAM: ${color3} $mem/$memmax ${color purple}${membar 10}$color ${offset -100}${font :size=8}${color5}$memperc%${font :size=8}
  ${color4}Swap: ${color3} $swap/$swapmax ${color purple}${swapbar 10}$color ${offset -100}${font :size=8}${color5}$swapperc%${font :size=8}
  ${color4}HD IO: ${color3}${diskio} ${color #0077ff}${color #0077ff}${alignr}${diskiograph 10, 150 ff0000 0000ff}${color}
${color7}FILE SYSTEM (Total / Free -- Percent Used) ${hr 2} ${color}
  ${color4}/root: ${color5}${fs_size /} / ${fs_free /}${color}  ${color6}${fs_bar 10 /}${color5}${offset -40}${fs_used_perc /root}%${color}
  ${color4}/home: ${color5}${fs_used /home} / ${fs_free /home}  ${color6}${fs_bar 10 /home}${color5}${offset -40}${fs_used_perc /home}%${color}
  ${color4}/var: ${color5}${fs_used /var} / ${fs_free /var}  ${color6}${fs_bar 10 /var}${color5}${offset -40}${fs_used_perc /var}%${color}
  ${color4}/usr/local: ${color5}${fs_used /usr/local} / ${fs_free /usr/local}  ${color6}${fs_bar 10 /usr/local}${color5}${offset -40}${fs_used_perc /usr/local}%${color}
  ${color4}/data: ${color5}${fs_used /data} / ${fs_free /data}  ${color6}${fs_bar 10 /data}${color5}${offset -40}${fs_used_perc /data}%${color}
${color7}PROCESSES ${hr 2}$color
  ${color tomato} PROC NAME              ${alignr}PID     CPU%    MEM%$color
   ${color4}${top name 1}                ${alignr}${color5}${top pid 1}   ${top cpu 1}    ${top mem 1}${color}
   ${color4}${top name 2}                ${alignr}${color5}${top pid 2}   ${top cpu 2}    ${top mem 2}${color}
   ${color4}${top name 3}                ${alignr}${color5}${top pid 3}   ${top cpu 3}    ${top mem 3}${color}
   ${color4}${top name 4}                ${alignr}${color5}${top pid 4}   ${top cpu 4}    ${top mem 4}${color}
${if_up eth1}${color7}NETWORK ${color2}eth1 ${addr br0}) ${color7}${hr 2}$color
  ${color4}Down: ${color Red}${downspeedf eth1}${color} k/s ${alignr}${color4}Up: ${color Red}${upspeedf eth1}${color} k/s
  ${color blue}${downspeedgraph eth1 15,100 ff0000 0000ff} ${alignr}${color red}${upspeedgraph eth1 
  15,100 0000ff ff0000}$color
  ${color4}Total: ${color5}${totaldown eth1} ${alignr}${color4}Total: ${color5}${totalup eth1}
${else}
${color7}NETWORK: No Network - GW: ${gw_ip} ${color7}${hr 2}
${endif}
${color7}LOGGING ${hr 2}$color
  ${color5}${execi 30 tail -n3 /var/log/messages | fold -w50}
${color7}WEATHER${hr 2}$color 
${color4} Leesburg, VA: ${color4}Current: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 --refetch --datatype=CC}${color4} 
 Temp: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=LT}${color4} Precip: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=PC}${color4} Humidity: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=HM} ${color4}   
 Winds: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=WS}  ${color4}From The:${color5} ${execi 3600 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=WD}   ${color cyan}${font Arrows:size=10}${execi 3600 python ~/Scripts/conkyForecast.py -r --location=USVA0427 --datatype=BF}${font :size=8}
          ${font Weather:size=30}${color cyan}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=WF  --startday=0 --endday=0 --spaces=0}${font :size=8}    ${voffset -22}${offset 10}${font Weather:size=30}${color cyan}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=WF  --startday=1 --endday=1}${font :size=8}    ${voffset -22}${offset 15}${font Weather:size=30}${color cyan}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=WF  --startday=2 --endday=2}${font :size=8}    ${voffset -22}${offset 15}${font Weather:size=30}${color cyan}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=WF  --startday=3 --endday=3}${font :size=8}    ${voffset -22}${offset 15}${font Weather:size=30}${color cyan}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=WF  --startday=4 --endday=4}${font :size=8}
     ${color1}${font monospace:bold:size=10}   Now    ${color1}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 --datatype=DW  --shortweekday --startday=1 --endday=4 --spaces=3}
  ${font monospace:bold:size=10}${color4}Hi: ${color5}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --datatype=HT --hideunits --startday=0}    ${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --datatype=HT  --hideunits --startday=1 --endday=4 --spaces=3}
  ${font monospace:bold:size=10}${color4}Lo: ${color5}${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --datatype=LT --hideunits --night --startday=0}    ${execi 10800 python ~/Scripts/conkyForecast.py --location=USVA0427 -i --datatype=LT --hideunits --night --startday=1 --endday=4 --spaces=3}

```

I am using weather and other advance features they work great. In fact, if I start conky by running 
```
conky -c ~/Conky/conkymain
```

At the command line everything works great. 

However, when I start it from a start script, like this:
```
#!/bin/bash
pkill conky
sleep 5 &&	
conky -c /home/dccrens/Conky/conkymain

```

I get the following output:
```
#!/bin/bash
pkill conky
+ pkill conky
sleep 5 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c /home/dccrens/Conky/conkymain
+ sleep 5
+ conky -c /home/dccrens/Conky/conkymain
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x6200001
  Serial number of failed request:  232
  Current serial number in output stream:  232
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &

```

This makes no sense to me. I have used just about every variation of "start" or "kill and start" scripts posted on this and other forums... I have changed the "sleep values" and have used variations on background, etc. The standard start script worked fine in Intrepid but since I upgraded to Jaunty it produces this "X" related error...

In Jaunty, everything else seems fine. I can run all graphic intensive apps. Play movies, etc. Not seeing any other errors. 

Any thoughts on why I am getting this X error. I have googled the error but not much luck there. My google-fu seems to be weakening...

Thanks.

PS: Bruce - I love what u are doing with Conky Hardcore!

---

### Post by Bruce M. on 2009-05-25
> **dccrens said:**
> Looking for a little help on startup script. 

PS: Bruce - I love what u are doing with Conky Hardcore!

Well thank you, but it is a joint effort.  :)

As to a start up script why not try this:

```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else

#sleep 30  # not required for xfce - 30 or more for others
conky -c ~/Conky/conkymain &
#conky -c ~/Conky/conkyforecast &

 exit
fi
```

That script can be used in "auto-start" and as a launcher.
If conky is running "click" and it's off and click again after editing and it's on.

**EDIT:** It worked when I tested Xfce 9.04

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-05-25
> **sophtpaw said:**
> Hi,

As you can see from my [screenshot]("http://img513.imageshack.us/my.php?image=screenshotiws.png") conky is sitting slightly to high. What is it i need to adjust in .conkyrc to bring it down a little?

thank you

> **sophtpaw said:**
> ....Also, conky covers any application that goes into its view. Would like to set it so that it stays underneath like background

Show us your conky file so we can help you.

Have a nice day.
Bruce

---

### Post by dccrens on 2009-05-25
> **Bruce M. said:**
> Well thank you, but it is a joint effort.  :)

As to a start up script why not try this:

```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else

#sleep 30  # not required for xfce - 30 or more for others
conky -c ~/Conky/conkymain &
#conky -c ~/Conky/conkyforecast &

 exit
fi
```

That script can be used in "auto-start" and as a launcher.
If conky is running "click" and it's off and click again after editing and it's on.

**EDIT:** It worked when I tested Xfce 9.04

Have a nice day.
Bruce

Bruce,

Thanks. I had already tried your script from one of your previous posts. No Joy... 

I have been playing more and it appears that it happens if I have the config files in a different directory than my home directory. Why? - I have no clue. I moved the "conkymain" config file to ~/Conky directory as you had done. I liked that suggestion and used the "conky -c ~/Conky/conkymain" to launch. That is when I get the error. I moved it back to ~/.conkyrc and everything is ok... very strange. I also noticed that it is intermittent. Sometimes it actually will work (with "conky -c ~/Conky/conkymain") and sometime it throws the error. Maybe some glitch in the X server...

---

### Post by Bruce M. on 2009-05-25
> **dccrens said:**
> Bruce,

Thanks. I had already tried your script from one of your previous posts. No Joy...

Hi Dave,

Don't know what to say, I'm still using 8.10 here.

I do wish you luck though.
Bruce

---

### Post by benjsec on 2009-05-28
Hi,

Hoping someone can help me before I start going mad here!
I've only just discovered conky this week, and mostly loving it so far - I've got it all set up and going on my laptop, and working really well (even if I do keep spending hours making tweaks), but I'm having a bit of a problem now putting it on my desktop pc.
The conky window appears fine (but with the shading), and behaves properly until it's updated once, then it moves above all windows. This happens if it runs at start up, if I start it from the terminal when the pc's been on for hours, when I use the 30s delay script, basically all the time! I've tried using the conkyrc file from my laptop (which is still behaving), but even that is doing the same.
My desktop's running Jaunty, upgraded from Intrepid, if that makes a difference at all!

Mr conkyrc for completeness:
```
#Author: Diggs
#Modified by: Ben S
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont 123:size=7.7

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
# mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour white

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 215
maximum_width 200

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color white
#default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 0.5

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
use_spacer none

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

${hr 2.75} 
${alignc}[   ${exec lsb_release -d | cut -f 2}    ] 
${hr 2.75}
${alignc}${nodename}   
${alignc}$kernel
${alignc}System Updates Available: ${execi 3600 aptitude search "~U" | wc -l | tail}
${alignc}Uptime: ${uptime}
${stippled_hr 1.75}
${alignc}[    CPU    ]
Frequency: ${alignr}${freq} MHz
Processes: ${alignr}$processes ( $running_processes running )
Cpu: ( ${cpu cpu0} % ) ${alignc}${color green}${cpubar 4 cpu0}${color white}
${cpugraph 30,200 FF8200 ff0000}
${stippled_hr 1.75}
${alignc}[    Memory    ]
Ram ${alignr}$mem / $memmax ( $memperc % ) 
${color green}${membar 4}${color white} 
swap ${alignr}$swap / $swapmax ( $swapperc % ) 
${color green}${swapbar 4}${color white}
${stippled_hr 1.75}
${alignc}[    Processes    ]
 PID      Name ${alignr}CPU        Memory
${top pid 1}  ${top name 1}$alignr ${top cpu 1} %   ${top mem 1} %
${top pid 2}  ${top name 2}$alignr ${top cpu 2} %   ${top mem 2} %
${top pid 3}  ${top name 3}$alignr ${top cpu 3} %   ${top mem 3} %
${stippled_hr 1.75}
${alignc}[    Hard Drive    ]
Root: 
${fs_used /}/${fs_size /}${alignr}( ${fs_used_perc /} % )
${color green}${fs_bar 4 /}${color white}
Films: 
${fs_used /home/ben/Videos/Films}/${fs_size /home/ben/Videos/Films}${alignr}( ${fs_used_perc /home/ben/Videos/Films} % )
${color green}${fs_bar 4 /home/ben/Videos/Films}${color white}
TV: 
${fs_used /home/ben/Videos/TV}/${fs_size /home/ben/Videos/TV}${alignr}( ${fs_used_perc /home/ben/Videos/TV} % )
${color green}${fs_bar 4 /home/ben/Videos/TV}${color white}
${stippled_hr 1.75}
${alignc}[     ${if_up wlan0}Wireless${else}Ethernet${endif}     ]
${if_up wlan0}Connected To:$alignr${wireless_essid wlan0} ( ${wireless_link_qual_perc wlan0} % )
${color green}${wireless_link_bar wlan0}${color white}
Internal IP: $alignr ${addr wlan0}${color white}
External IP: $alignr ${execi 300 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
Down: ${color white}${downspeed wlan0} k/s ${alignr}${color white}Up:${color white} ${upspeed wlan0} k/s
${color white}${downspeedgraph wlan0 20,85 FF800 ff0000} ${alignr}${upspeedgraph wlan0 20,85 FF0000 FF9900}$color
TCP Connections 1-1055: $alignr ${tcp_portmon 1 1055 count}
TCP Connections 1056-65535: $alignr ${tcp_portmon 1056 65535 count}
${else}Internal IP: $alignr ${addr eth0}
External IP: $alignr ${execi 300 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${color white}Down: ${color white}${downspeed eth0} k/s ${alignr}${color white}Up:${color white} ${upspeed eth0} k/s
${color white}${downspeedgraph eth0 20,90 FF8200 ff0000} ${alignr}${upspeedgraph eth0 20,90 FF0000 FF9900}$color
${color}TCP Connections 1-1055: $alignr ${tcp_portmon 1 1055 count}
${color}TCP Connections 1056-65535: $alignr ${tcp_portmon 1056 65535 count}${endif}
${stippled_hr 1.75}
${alignc}[     HellaNZB     ]
${alignc}${execi 10 ~/scripts/hellaconk.py -n}
Percent Done: ${execi 10 ~/scripts/hellaconk.py -p}%${alignr}ETA: ${execi 10 ~/scripts/hellaconk.py -e}
Speed: ${execi 10 ~/scripts/hellaconk.py -r} k/s${alignr}Queue Length: ${execi 10 ~/scripts/hellaconk.py -l}
Next: ${execi 10 ~/scripts/hellaconk.py -N}
${hr 2.75}
```

Many Thanks,
Ben

---

### Post by sleepyjon on 2009-05-29
> **seldon77 said:**
> Thanks for the comments and the 'thankses'!

1. This little item is great for figuring out if you've got spy-ware or are being DOS attacked. It will list any programs that are connecting to the outside world, and tell you how many connections they are making:

${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}



This line causes conky to not display for me in xfce on jaunty.

---

### Post by dj_flx on 2009-05-30
Can anyone tell me why:

```
CONNECTIONS ${hr 2}

HTTP: ${tcp_portmon 80 81 count}

HTTPS: ${tcp_portmon 443 444 count}

Torrent: ${tcp_portmon 52594 52600 count}

TOR: ${tcp_portmon 9050 9051 count}

Total: ${tcp_portmon 1 65535 count}
```

only gives me a total count and 0 for everything else?

---

### Post by groovomata on 2009-06-03
Hello All, I have a conky question. In my display I have, under the 'Network' section, wireless and ethernet ip addresses and up and down kb/s. Please refer to my screenshot.
In the part of my display that shows the upspeed and downspeed of my internet connection, I would like it to show the up and downspeed of whichever adapter is connected. Currently, it only shows the output from wlan0. 
Does anyone know how I would do that?

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 5

# Maximum width
maximum_width 160

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

#  unused text
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_eth2} Mbits/sec
#  hda Temp:${alignr}${execi 1800 /home/tonyt/scripts/.hdtemp}

TEXT
hostname:$alignr$nodename
uptime:$alignr$uptime
$sysname $kernel

Network
wlan0:$alignr${addr wlan0}
eth0:$alignr${addr eth0}
up:$alignr${downspeed wlan0} kb/s
down:$alignr${upspeed wlan0} kb/s

System
cpu0 ${cpu cpu1}% ${color white}${cpubar cpu1}$color
cpu1 ${cpu cpu2}% ${color white}${cpubar cpu2}$color
ram: $memperc% ${color white}$membar$color
swap: $swapperc% ${color white}$swapbar$color
hda1: ${fs_used_perc /}% ${color white}${fs_bar /}$color
hda5: ${fs_used_perc /home}% ${color white}${fs_bar /home/}$color
processes: $processes ${alignr}running: $running_processes
```

---

### Post by latenite4 on 2009-06-13
Running Ubuntu 9.04 with Conky 1.6.1 
Nvidia GeForce4 MX 4000 graphics card 
Nvidia driver version 96.43.10

conky is basically working OK, but I can't get the
'nvidia' variable to work.  It should print
out Nvidia GPU info but instead it just prints out '${nvidia}'

Any idea why the nvidia conky variable doesn't work?

Thx, Rod

---

### Post by Bruce M. on 2009-06-14
> **latenite4 said:**
> Running Ubuntu 9.04 with Conky 1.6.1 
Nvidia GeForce4 MX 4000 graphics card 
Nvidia driver version 96.43.10

conky is basically working OK, but I can't get the
'nvidia' variable to work.  It should print
out Nvidia GPU info but instead it just prints out '${nvidia}'

Any idea why the nvidia conky variable doesn't work?

Thx, Rod

Have you tried upgrading your nvidia driver?

---

### Post by gmitrev on 2009-06-15
SOLVED
[COLOR=Gray]
I have a problem with the program. I've read the instructions on the first page and copied the configuration file but conky doesn't refresh every three seconds (as in the conf file). I have changed it to 1.0, but it still doesn't refresh properly, I think it does refresh every minute or so. 

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 0.1
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
```Any suggestions?

[COLOR=Black]The problem was in the script. [/COLOR]
[/COLOR]

---

### Post by Cam42 on 2009-07-05
I've installed conky, now how do I start it? /n00b question

---

### Post by p0cky84 on 2009-07-05
> **seldon77 said:**
> **FOR HARDY AND IBEX. NOTE: for old Ubuntu versions, see here: [http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)**

Conky is an powerful desktop app that posts system monitoring info onto the root window. It used to be hard to set up properly (had unlisted dependencies, special command line compile options, and requires a mod to xorg.conf to stop it from flickering, and needed devilspie to work without being annoying). It's a lot easier these days, but there are still some tricks.

[CENTER]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96421&d=1229299247[/IMG][/CENTER]

1. Make sure the universe repo is enabled, and install 'conky' from universe repo. ie:
```

    sudo apt-get --assume-yes install conky

```2. Make a configuration file in your home directory (ie. /home/bob). This is the code that describes what you want displayed on your conky desktop.
```

gedit /home/bob/.conkyrc

```3. Obviously, you can put whatever you want in your .conkyrc.

One of the cutest scripts at the moments is called Conky Colours (as in the screenshot above) - [http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328](http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328), but it is a little harder than other scripts to install.

Otherwise, for a very functional conky that I've mashed up from other scripts, you could paste the following code into the file and save / exit. I've added in some cool code that will show what programs on your machine are trying to connect to the outside world (should give you some warning of spyware, etc. on your machine), as well as a summary of whats being written in your /var/log file (system error msgs, etc), and also a list of the top few programs that are chewing up your CPU and memory:

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```If the network connections graph does not work, you will have to change all "eth0" references to "ppp0" (for modem) or "ath0" (for some other devices). 

5. Run 'conky' to see if it works without flickering. If there is flickering, add the dbe module to your /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```anywhere near the end add:
```

Section "Module"
        Load    "dbe"
EndSection

```if there isn't already a Module section, otherwise just add 'Load "dbe"' into your Module section.

6. **If you do not have funky desktop effects on your desktop (Compiz, etc)** - then for vanilla Ubuntu (Gnome), Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot.
[INDENT][I][COLOR=DimGray]NOTE: **Kubuntu users ONLY** make the following changes:
Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```Since we don't use nautilus in Kubuntu, we don't need it.

Also, to get Conky to autostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```**For XFCE ONLY** make the following changes to .conkyrc
```
own_window yes
own_window_type override
own_window_transparent yes

```[/COLOR][/I][/INDENT]7. **If you do have funky desktop effects on your desktop (Compiz, etc)** place a startup script called .conky_start.sh in your home directory:
```
#!/bin/bash
sleep 60 && conky;
```This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky and try to do funky things with it. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs).

Please add comments if anything doesn't work or if you have other ideas and I can update the instructions.

Nice tut, tho next time maybe use "~" instead of "/home/bob" to avoid confusion with the newbs.

---

### Post by Bruce M. on 2009-07-05
> **Cam42 said:**
> I've installed conky, now how do I start it? /n00b question

Try this:  [Conky Hardcore!]("http://conky.linux-hardcore.com/") and check out: [HowTo: A Beginners Guide to Setting up Conky]("http://conky.linux-hardcore.com/?page_id=1289").

If you need more we're here just ask.

Have a nice day.
Bruce

---

### Post by miegiel on 2009-07-07
> **Cam42 said:**
> I've installed conky, now how do I start it? /n00b question

In a terminal

```
conky
``` :twisted:

CTRL + C to stop it again

---

### Post by trayzz on 2009-07-15
thanks a lot!
neat job

however, conky looks a lot different than on your screenshot (maybe it wasn't meant to look like it tho). here's a screenshot [http://files.getdropbox.com/u/642705/permanent/Screenshot.png](http://files.getdropbox.com/u/642705/permanent/Screenshot.png)
say this is the way its supposed to be, can you help me removing everything below "logging"?
or if it shouldnt look like this, tell me what went wrong pls

also, i have a lot of errors showing up in my terminal
here's an excerpt

Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Conky: statfs '/media/sda1': No such file or directory
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Conky: statfs '/media/sda1': No such file or directory

---

### Post by tsekhanovsky on 2009-07-18
> **seldon77 said:**
> 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

I very think that acpitemp - not a CPU temperature, but Motherboard. :)

---

### Post by tsekhanovsky on 2009-07-18
> **miegiel said:**
> In a terminal

```
conky
``` :twisted:

CTRL + C to stop it again

think that "killall conky"  more correct :)

---

### Post by Bruce M. on 2009-07-19
> **tsekhanovsky said:**
> I very think that acpitemp - not a CPU temperature, but Motherboard. :)

I believe it is neither:

```
bruloo@bruloo:~$ acpi -t
     Thermal 0: ok, 21.8 degrees C
bruloo@bruloo:~$ acpi -V
     Thermal 0: ok, 21.8 degrees C
     Cooling 0: Processor 0 of 0
     Cooling 1: Fan 1 of 1
bruloo@bruloo:~$
``` 


And the third line in sensors (that never changes):

```
bruloo@bruloo:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +21.8°C  (crit = +96.8°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +42.0°C

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.46 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.34 V  (min =  +9.18 V, max =  +0.24 V)   ALARM
+3.3V:       +3.10 V  (min =  +1.47 V, max =  +3.98 V)
+5V:         +4.88 V  (min =  +5.97 V, max =  +4.59 V)   ALARM
-12V:       -11.87 V  (min = -13.10 V, max = -13.59 V)   ALARM
V5SB:        +5.03 V  (min =  +0.24 V, max =  +1.75 V)   ALARM
VBat:        +2.98 V  (min =  +1.01 V, max =  +3.09 V)
fan1:       3590 RPM  (min = 168750 RPM, div = 2)  ALARM
CPU Fan:       0 RPM  (min =   -1 RPM, div = 8)  ALARM
fan3:       4141 RPM  (min = 9926 RPM, div = 2)  ALARM
M/B Temp:    +37.0°C  (high = +12.0°C, hyst =  +8.0°C)  ALARM  sensor = thermistor
CPU Temp:    +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:        +9.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
cpu0_vid:   +0.000 V
beep_enable:enabled

bruloo@bruloo:~$
```

I'm still researching the "mystery" temperature of ACPI! For me it's thermal or ambient temp until I find something different. I have an email in ti the acpi "help" list.

Have a nice day.
Bruce

---

### Post by tsekhanovsky on 2009-07-19
> **Bruce M. said:**
> I believe it is neither:

```
bruloo@bruloo:~$ acpi -t
     Thermal 0: ok, 21.8 degrees C
bruloo@bruloo:~$ acpi -V
     Thermal 0: ok, 21.8 degrees C
     Cooling 0: Processor 0 of 0
     Cooling 1: Fan 1 of 1
bruloo@bruloo:~$
```
And the third line in sensors (that never changes):

```
bruloo@bruloo:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +21.8°C  (crit = +96.8°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +42.0°C

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.46 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.34 V  (min =  +9.18 V, max =  +0.24 V)   ALARM
+3.3V:       +3.10 V  (min =  +1.47 V, max =  +3.98 V)
+5V:         +4.88 V  (min =  +5.97 V, max =  +4.59 V)   ALARM
-12V:       -11.87 V  (min = -13.10 V, max = -13.59 V)   ALARM
V5SB:        +5.03 V  (min =  +0.24 V, max =  +1.75 V)   ALARM
VBat:        +2.98 V  (min =  +1.01 V, max =  +3.09 V)
fan1:       3590 RPM  (min = 168750 RPM, div = 2)  ALARM
CPU Fan:       0 RPM  (min =   -1 RPM, div = 8)  ALARM
fan3:       4141 RPM  (min = 9926 RPM, div = 2)  ALARM
M/B Temp:    +37.0°C  (high = +12.0°C, hyst =  +8.0°C)  ALARM  sensor = thermistor
CPU Temp:    +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:        +9.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
cpu0_vid:   +0.000 V
beep_enable:enabled

bruloo@bruloo:~$
```I'm still researching the "mystery" temperature of ACPI! For me it's thermal or ambient temp until I find something different. I have an email in ti the acpi "help" list.

Have a nice day.
Bruce

:) you saw, in my laptop acpi temp - the MB temp. 
Ps: think different :))
Pps: &#1087;&#1088;&#1072;&#1074;&#1076;&#1072; &#1075;&#1076;&#1077;-&#1090;&#1086; &#1088;&#1103;&#1076;&#1086;&#1084; :)

---

### Post by Bruce M. on 2009-07-19
> **tsekhanovsky said:**
> 
Pps: &#1087;&#1088;&#1072;&#1074;&#1076;&#1072; &#1075;&#1076;&#1077;-&#1090;&#1086; &#1088;&#1103;&#1076;&#1086;&#1084; :)

Agree 100%

---

### Post by cwhisperer on 2009-07-28
> **sophtpaw said:**
> Hi,

As you can see from my [screenshot]("http://img513.imageshack.us/my.php?image=screenshotiws.png") conky is sitting slightly to high. What is it i need to adjust in .conkyrc to bring it down a little?

thank you

change the gap_y value to 30 or 40

---

### Post by Bruce M. on 2009-07-28
> **cwhisperer said:**
> change the gap_y value to 30 or 40

Looks like you need to play with your x - y values (above TEXT)

```
gap_x 0 # left-right
gap_y 30 # up - down
```

A negative number moves UP or LEFT
Positive number Down or Right

Have a nice day.
Bruce

---

### Post by abansb on 2009-07-28
I never could get Conky to work till I used this tutorial

---

### Post by karlmp on 2009-07-29
spyware on linux?

---

### Post by bobmendon on 2009-08-13
Help! I am getting two things happening when conky runs:

1. I'm getting the shadows things because I am running compiz-fusion.

2. If I open an app, it goes under the transparent conky window.

To further explan this has never happened with straight Ubuntu 9.0.4 but this has been built over Crunchbang#! and I suspect there are conflicting things happening with the compositing. 

At any rate, If I new the correct way to post the files here I would. I can't attach them and when I post them inside a post, somebody always yess at me and tells me I should use some other method that I can't find.

---

### Post by miegiel on 2009-08-13
> **bobmendon said:**
> Help! I am getting two things happening when conky runs:

1. I'm getting the shadows things because I am running compiz-fusion.

2. If I open an app, it goes under the transparent conky window.

To further explan this has never happened with straight Ubuntu 9.0.4 but this has been built over Crunchbang#! and I suspect there are conflicting things happening with the compositing. 

At any rate, If I new the correct way to post the files here I would. I can't attach them and when I post them inside a post, somebody always yess at me and tells me I should use some other method that I can't find.

Try editing or adding the next 2 lines in your .conkyrc (above the TEXT line ofcourse ;))
```
draw_shades no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by Stoneface on 2009-08-15
I have ```
draw_shades no
``` and ```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
``` but the conky window is still above all windows/programs... 

Here is the complete script as used by me on jaunty Jackalope:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by miegiel on 2009-08-15
> **Stoneface said:**
> I have ```
draw_shades no
``` and ```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
``` but the conky window is still above all windows/programs... 

Here is the complete script as used by me on jaunty Jackalope:

...

try ```
own_window no
```

---

### Post by Stoneface on 2009-08-15
Thanks for the input Miegiel. I did a lot of trial and error stuff. I rebooted about 5 times :-) I added:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

own_window_type desktop did the trick.

---

### Post by Stoneface on 2009-08-15
Only sometimes the Conky screen just disappears when I minimize and maximize some windows... Then when I enter conky in the terminal it comes back again. Strange..

---

### Post by lazylew on 2009-08-16
I got as far as step 7 of the tutorial, but am stuck here: 
      Code:
     ```
chmod a+x .conky_start.sh 
```
 [COLOR=Red]and add it to your startup programs (menu: system->preferences->session->startup programs).
[/COLOR]
The code in terminal gave no error, but this last [COLOR=Red]line[/COLOR] is unclear, because I don't see anything related to conky in the startup programs.

---

### Post by Stoneface on 2009-08-16
Well you just click on browse next to the command box after you clicked on add startup application and then locate conky (usr/bin I believe) so you can add it to the startup programs.. Like that it will startup like all the others. But somehow it still disappeasrs every now and then. Maybe I need to chmod the file.. or go though the tutorial again. When I enter conky in a terminal I get this output:
```
me@laptop:~$ conky
Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (1a000ae) is subwindow of root window (13c)
Conky: window type - desktop
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

```

---

### Post by Stoneface on 2009-08-16
When I enter ```
conky &
``` and then x close the terminal the conky process seems to keep on running. The weird thing is that I have added the conky script to the start up programs so it shouldn't be closed after having been started up at the beginning anyway now should it?
Maybe because I added the the wrong conky script?

One more thing, when I right click the desktop the conky Windows disappears. Any ideas why?

---

### Post by miegiel on 2009-08-16
> **lazylew said:**
> I got as far as step 7 of the tutorial, but am stuck here: 
      Code:
     ```
chmod a+x .conky_start.sh 
```
 [COLOR=Red]and add it to your startup programs (menu: system->preferences->session->startup programs).
[/COLOR]
The code in terminal gave no error, but this last [COLOR=Red]line[/COLOR] is unclear, because I don't see anything related to conky in the startup programs.

*chmod* changes the permissions of a file, *+x* makes it executable (can't remember what the *a* does, try *man chmod*). To test if the script works run it in a terminal.

```
sh .conky_start.sh
```

Once your *.conky_start.sh* is executable you need to add it, but with a *sh* in front of it, as a new entry in the *Startup Programs* or *Sesions* list (it's been renamed from *Sesions* to *Startup Programs* since intrepid or jaunty).

@**Stoneface** you need to use the startup script to delay conky's start up a bit, so that it won't start before the desktop has finished loading, or else it will drop behind the desktop (and you won't see it).

---

### Post by Stoneface on 2009-08-16
And I guess conky_start.sh should have

```
#!/bin/bash
sleep 30 &&
conky &
```

or something similar and should be added to the startup applications?

Other question: /usr/bin/conky should or does not need to be added to startup applications?

Reading this once more: [http://ubuntuforums.org/showthread.php?p=5436679](http://ubuntuforums.org/showthread.php?p=5436679)

---

### Post by miegiel on 2009-08-16
> **Stoneface said:**
> And I guess conky_start.sh should have

```
#!/bin/bash
sleep 30 &&
conky &
```

or something similar and should be added to the startup applications?

Other question: /usr/bin/conky should or does not need to be added to startup applications?

Reading this once more: [http://ubuntuforums.org/showthread.php?p=5436679](http://ubuntuforums.org/showthread.php?p=5436679)

*Startup Programs* or *Sesions* starts the conky startup script, which in turn waits 30 seconds (*sleep 30*) and then starts conky.

---

### Post by Stoneface on 2009-08-16
home/my-name/conky/conkymain is the script's location now. In sessions I load this script now:

```
#!/bin/bash
sleep 30 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```

I named the script startconky.sh and chmod a+x it. Then I did sh startconky.sh and got no errors. Just waited a bit now and yeah! It does run! Right clicking or left clicking on the Desktop makede it disappear until I changed:
```
own_window_type desktop
```
to
```
own_window_type override
``` :P

---

### Post by lazylew on 2009-08-16
> **Stoneface said:**
> Well you just click on browse next to the command box after you clicked on add startup application and then locate conky ....[/code]that simple hey? thanks! it works :-)

---

### Post by abdusamed on 2009-08-17
[SIZE=4]**MY CONKY IS SOO MESSEED UPPP**[/SIZE]
[B]
LOOK AT MY SCREENSHOT AND YOU WILL KNOW WHAT THE PROB IS!![/B]

I did what you typed to do and i pasted everything the way is typed up. But still.**. i coming out WAY to differennttt**

Also.. it doesnt even start at startup though i did what you told me to do.. Its on ubuntu 9.04.

I my picture two.. the error in the end keeps on repeating.

---

### Post by Stoneface on 2009-08-17
One thing I saw and that should help you a bit further... ```
chmod a+x .conky_start.sh
``` is a command to change the file permission that should be entered in the terminal. It should not be put in the startup .sh script. this what I have in .conky_start.sh:
```
#!/bin/bash
sleep 30 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```

---

### Post by miegiel on 2009-08-17
> **abdusamed said:**
> **MY CONKY IS SOO MESSEED UPPP**
[B]
LOOK AT MY SCREENSHOT AND YOU WILL KNOW WHAT THE PROB IS!![/B]

I did what you typed to do and i pasted everything the way is typed up. But still.**. i coming out WAY to differennttt**

Also.. it doesnt even start at startup though i did what you told me to do.. Its on ubuntu 9.04.

I my picture two.. the error in the end keeps on repeating.

[LIST=1]
[*]replace the *chmod a+x .conky_start.sh* line in *.conky_start.sh* with *conky -c ~/.conkyrc &*
[*]run *chmod a+x .conky_start.sh* in a terminal
[*]run *conky* in a terminal to test conky
[*]run *sh .conky_start.sh* in a terminal to test the startup (delay) script
[*]if you're still having trouble, post your *.conkyrc*, *.conky_start.sh* and any errors you get from the terminal in code boxes ```
[ code ] [ / code ] (without the spaces ofc ;) 
```
[*]take it easy with the CAPS :) we're not blind
[/LIST]

---

### Post by fire_beast on 2009-08-19
I have the most odd thing happening with mine.  If I click too far left on the conky window, a box stretches over toward my desktop icons and actually clicks on them...I can open all of my icons from the left side of my conky...if I click on the right side, the box just extends toward them, but doesn't make contact (as is displayed in my screenshot)  any ideas?  I'm using Ubuntu 9.04.  I included the current code for it as well.

Thanks,
Brandon

---

### Post by Stoneface on 2009-08-20
Compare mine to yours and adjust some of you code here and there. Mine works like a charm!

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
gap_x 20
gap_y 20
 
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by fire_beast on 2009-08-20
I went ahead and checked everything...the only differences are in the info displayed...it has done that odd mouse thing since I got the code you're using, so when I modified it, it didn't make a difference...I checked my code against as many codes as i could find, but I couldn't find the problem. Am I missing something that I'm not skilled enough to see?  when I installed conky, it said it was getting all dependencies, but maybe it didn't get something I needed?

---

### Post by Motorhead Kaze on 2009-09-01
Hi. I went through a couple different tutorials to get Conky up and running the way I wanted it, and it works now, but even though I added "conky" to sessions, when starting up Gnome, I only get the little black box version of Conky that appears as a window.

To get the version of Conky that appears to be part of my desktop running, I actually have to go to a terminal and enter conky -c ~/Conky/conkymain .

Can someone tell me how to get the pretty desktop version of Conky to startup when Gnome boots up? 

By now, it is late at night and my brain is melting. Any help on this would be super.

Thanks in advance

---

### Post by miegiel on 2009-09-01
> **Motorhead Kaze said:**
> Hi. I went through a couple different tutorials to get Conky up and running the way I wanted it, and it works now, but even though I added "conky" to sessions, when starting up Gnome, I only get the little black box version of Conky that appears as a window.

To get the version of Conky that appears to be part of my desktop running, I actually have to go to a terminal and enter conky -c ~/Conky/conkymain .

Can someone tell me how to get the pretty desktop version of Conky to startup when Gnome boots up? 

By now, it is late at night and my brain is melting. Any help on this would be super.

Thanks in advance
If you don't use compiz just add
```
conky -c ~/Conky/conkymain &
```
to *Startup Applications* (under *System / Preferences*)

If you do use compiz, make a startup script containing the code below and save it as *.conky_start.sh*
```
#!/bin/bash
sleep 60 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -d -c ~/Conky/conkymain &
#sleep 0 &&
#conky -d -c ~/Conky/conkyforecast &#!/bin/bash
exit
```
This will delay conky from starting for 60sec so that it doesn't get killed in a "hit and run" when compiz starts. Then run the following in a terminal to make the script executable.
```
chmod a+x .conky_start.sh
```
And finally add *sh .conky_start.sh* to your *Startup Applications*.

Mind you if you test the script by running *sh .conky_start.sh* in a terminal you'll have to wait 60 secs for it to start too ;)

---

### Post by Motorhead Kaze on 2009-09-01
Thanks for responding. I got it working. The trouble was that I got my tutorials crossed between this one and another.

---

### Post by Jordanwb on 2009-09-13
Nevermind. *Facepalm*

---

### Post by JayKay3000 on 2009-09-16
Thanks, just tried this out, works great! Though tweaking it to your personal preference does take quite a bit of time. Should have started earlier :). But it's cool all the same. Just the thing I was after and not too 'fancy' either.

---

### Post by NoobixCubeOne on 2009-09-20
Hi all,

I have followed the steps given by the OP. I did the command line stuff, made the conkyrc file in my Home directory. But I do not see any conky up and running. I am currently running Jaunty.

Please help 

thanks

---

### Post by miegiel on 2009-09-20
> **NoobixCubeOne said:**
> Hi all,

I have followed the steps given by the OP. I did the command line stuff, made the conkyrc file in my Home directory. But I do not see any conky up and running. I am currently running Jaunty.

Please help 

thanks

type ```
conky
``` in a terminal and tell us what happens

---

### Post by NoobixCubeOne on 2009-09-21
> **miegiel said:**
> type ```
conky
``` in a terminal and tell us what happens

I feel quite silly now :lolflag:

Thanks for the help

---

### Post by ali_ali on 2009-10-10
hi ! i finished setting up conky , but i hav a problem , wen i use desktop effects to show all currently opened windows , conky as well as panel darkens , how 2 get rid of this , i hav included screenshots 
plz do help .... thank u...

---

### Post by miegiel on 2009-10-10
> **ali_ali said:**
> hi ! i finished setting up conky , but i hav a problem , wen i use desktop effects to show all currently opened windows , conky as well as panel darkens , how 2 get rid of this , i hav included screenshots 
plz do help .... thank u...

I think you need to disable the desktop effects for conky windows in compiz. Open the *CompizConfig Settings Manager* (it's in the settings menu). If you don't have it installed :
```
sudo apt-get install compizconfig-settings-manager
```
Under *window decoration* > *shadow windows* I've got *!(name=panel)*. But it could also be a setting somewhere else in CCSM (CompizConfig Settings Manager). *!* stands for not, *panel* stands for windows that are panels, you could also try *!(name=panel | conky)*

Also make sure transparency is turned on in your *.conkyrc*
```
own_window_transparent yes
```
in the part above the *TEXT* line.

---

### Post by ali_ali on 2009-10-11
hey thanks for the reply [miegiel]("http://ubuntuforums.org/member.php?u=514319")... i tried out wat u said but still i hav the same problem , actually the darkening of the conky & pannel occurs only when i  take my mouse pointer to the top-left corner of the desktop to display all currently opened widows (scale windows) , otherwise everythin is fine conky has  transperent background ,
:) ...

---

### Post by DeMus on 2009-10-11
I've been playing around with Conky also. My latest result is shown in the attachment.

---

### Post by miegiel on 2009-10-11
> **ali_ali said:**
> hey thanks for the reply [miegiel]("http://ubuntuforums.org/member.php?u=514319")... i tried out wat u said but still i hav the same problem , actually the darkening of the conky & pannel occurs only when i  take my mouse pointer to the top-left corner of the desktop to display all currently opened widows (scale windows) , otherwise everythin is fine conky has  transperent background ,
:) ...

Maybe 1 of the conky adicts in the [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") thread knows. Also good for showing off your conky creations ;)

---

### Post by ali_ali on 2009-10-11
yh miegiel i'l post my query 2 the therad u specified , hope i'l get a solution , thanks for de link dude ... [URL="http://ubuntuforums.org/member.php?u=514319"]
[/URL]

---

### Post by admiral123q on 2009-10-21
> **seldon77 said:**
> **FOR HARDY AND IBEX. NOTE: for old Ubuntu versions, see here: [http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)**

Conky is an powerful desktop app that posts system monitoring info onto the root window. It used to be hard to set up properly (had unlisted dependencies, special command line compile options, and requires a mod to xorg.conf to stop it from flickering, and needed devilspie to work without being annoying). It's a lot easier these days, but there are still some tricks.

[CENTER]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96421&d=1229299247[/IMG][/CENTER]

1. Make sure the universe repo is enabled, and install 'conky' from universe repo. ie:
```

    sudo apt-get --assume-yes install conky

```2. Make a configuration file in your home directory (ie. /home/bob). This is the code that describes what you want displayed on your conky desktop.
```

gedit /home/bob/.conkyrc

```3. Obviously, you can put whatever you want in your .conkyrc.

One of the cutest scripts at the moments is called Conky Colours (as in the screenshot above) - [http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328](http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328), but it is a little harder than other scripts to install.

Otherwise, for a very functional conky that I've mashed up from other scripts, you could paste the following code into the file and save / exit. I've added in some cool code that will show what programs on your machine are trying to connect to the outside world (should give you some warning of spyware, etc. on your machine), as well as a summary of whats being written in your /var/log file (system error msgs, etc), and also a list of the top few programs that are chewing up your CPU and memory:

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```If the network connections graph does not work, you will have to change all "eth0" references to "ppp0" (for modem) or "ath0" (for some other devices). 

5. Run 'conky' to see if it works without flickering. If there is flickering, add the dbe module to your /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```anywhere near the end add:
```

Section "Module"
        Load    "dbe"
EndSection

```if there isn't already a Module section, otherwise just add 'Load "dbe"' into your Module section.

6. **If you do not have funky desktop effects on your desktop (Compiz, etc)** - then for vanilla Ubuntu (Gnome), Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot.
[INDENT][I][COLOR=DimGray]NOTE: **Kubuntu users ONLY** make the following changes:
Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```Since we don't use nautilus in Kubuntu, we don't need it.

Also, to get Conky to autostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```**For XFCE ONLY** make the following changes to .conkyrc
```
own_window yes
own_window_type override
own_window_transparent yes

```[/COLOR][/I][/INDENT]7. **If you do have funky desktop effects on your desktop (Compiz, etc)** place a startup script called .conky_start.sh in your home directory:
```
#!/bin/bash
sleep 60 && conky;
```This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky and try to do funky things with it. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs).

Please add comments if anything doesn't work or if you have other ideas and I can update the instructions.
guys.... im new in ubuntu how i can install?? i cant understund wehre we type this words?? ty.

---

### Post by miegiel on 2009-10-21
> **admiral123q said:**
> guys.... im new in ubuntu how i can install?? i cant understund wehre we type this words?? ty.

In a [terminal]("http://en.wikipedia.org/wiki/GNOME_Terminal"), check the *applications* menu, it should be under *accessories*.

2 tips :
[LIST=1]
[*]copy and paste works better than typing
[*]use the *Tab* key to auto complete commands
[/LIST]

---

### Post by ThomasDenmark on 2009-10-21
I have followed the instructions from the first post of this thread, and when running conky I got this error:

Conky: statfs '/media/sda1': No such file or directory

Now, I understand why I get this error: because I do not have a /media/sda1! But I dont understand why the error keeps showing when I comment out the line in .conkyrc:

# hda1: ${fs_free_perc /media/sda1}%  ${fs_bar 6 /media/sda1}$color

Same problem after commenting out. However, if I completely delete the line, the problem disappears. 

Have I misunderstood something about how to make comments in an rc file?

Thomas

---

### Post by miegiel on 2009-10-22
> **ThomasDenmark said:**
> I have followed the instructions from the first post of this thread, and when running conky I got this error:

Conky: statfs '/media/sda1': No such file or directory

Now, I understand why I get this error: because I do not have a /media/sda1! But I dont understand why the error keeps showing when I comment out the line in .conkyrc:

# hda1: ${fs_free_perc /media/sda1}%  ${fs_bar 6 /media/sda1}$color

Same problem after commenting out. However, if I completely delete the line, the problem disappears. 

Have I misunderstood something about how to make comments in an rc file?

Thomas

I guess you've got nothing mounted in */media/sda1* or you need a extra / at the end.

Some examples :
```
${fs_free_perc} or ${fs_free_perc /} gives free % of your *root* partition
${fs_free /home/}                    gives free % of your *home* partition (if you have home on it's own partition)
${fs_free_perc /media/sda1/}          gives free % of whatever partition you mounted in */media/sda1*.

```

---

### Post by ThomasDenmark on 2009-10-29
Miegel, thanks for your swift response. However, you have answered to a different question, than I intended to ask. 

When commenting out this line, I still get the same error. 

My question is simply, why does conky still seem to parse (and act upon) a line in the conkyrc file, that I have commented out. 

Isn't lines beginning with # supposed to be disregarded by conky?

Thomas

---

### Post by miegiel on 2009-10-29
> **ThomasDenmark said:**
> Miegel, thanks for your swift response. However, you have answered to a different question, than I intended to ask. 

When commenting out this line, I still get the same error. 

My question is simply, why does conky still seem to parse (and act upon) a line in the conkyrc file, that I have commented out. 

Isn't lines beginning with # supposed to be disregarded by conky?

Thomas

Only in the lines above TEXT, below it everything parses.

---

### Post by ThomasDenmark on 2009-10-29
Ok, now I get it. Thanks.

---

### Post by Dispenser on 2009-11-03
Here's one for ya.

[FONT=monospace]in system monitor it shows that I have a two core Intel 6600 @ 2.40GHz

but when I use[/FONT] ${freq}[FONT=monospace] in conky it displays 1.60Ghz

earlier today it would display the correct speed in conky if I had system monitor open but now it seems stuck at 1.60Ghz

Any ideas?

Thanks,
PEZ
[/FONT]

---

### Post by miegiel on 2009-11-03
> **Dispenser said:**
> Here's one for ya.

[FONT=monospace]in system monitor it shows that I have a two core Intel 6600 @ 2.40GHz

but when I use[/FONT] ${freq}[FONT=monospace] in conky it displays 1.60Ghz

earlier today it would display the correct speed in conky if I had system monitor open but now it seems stuck at 1.60Ghz

Any ideas?

Thanks,
PEZ
[/FONT]

Your CPU is probably clocking down because it hasn't got that much to do (keeps it cool and saves energy). Check what happens when you run a virus scan or *glxgears* (in the terminal).

---

### Post by Dispenser on 2009-11-04
... a virus scan???  In Linux?  teeheehee.

That is what I thought though, just wanted to verify.

Thanks

---

### Post by madshad on 2009-12-09
Ok Heres what Im trying to do... get my Conky to display what I playing on Atunes (using Mplayer as player, but will switch to xine if easier)

I got this script working with rythembox but i dont like rthymbox because i cant spell it...

```

${font Fontdinerdotcom Sparkly:size=30} Listening to ${font}
${font Fontdinerdotcom Sparkly:size=50} ${exec rhythmbox-client --no-start --print-playing-format "%ta"}${font}
${font Fontdinerdotcom Sparkly:size=30} ${exec rhythmbox-client --no-start --print-playing-format "%tt"} ${font}

$alignc ${font Fontdinerdotcom Sparkly:size=20} ${exec rhythmbox-client --no-start --print-playing-format "%te - %td"} ${font}

${font Fontdinerdotcom Sparkly:size=20}From their hit Album...
${font Fontdinerdotcom Sparkly:size=30} ${exec rhythmbox-client --no-start --print-playing-format "%at"}${font}
```

I tried to just change rythembox-client to mplayer and tried Atune too, no luck

i found this online somewhere in a non-english forum
```
${if_running MPlayerapp}
Playing:
${color ffaa00}${font Bistream Vera Sans:size=11}$alignc${execi 5 ~/.conky/MPlayer title}
${font Bistream Vera Sans:size=7}${color black}${voffset -5}by: ${color yellow}${execi 5 ~/.conky/MPlayer artist}
${color slate grey}from: ${color yellow}${execi 5 ~/.conky/MPlayer album}
${execibar 2 ~/.conky/MPlayer progress}${else}${color slate grey}${alignc}Cisza i spokój${endif}
```

but that didnt even show up on screen.

thanks for any help :)

---

### Post by miegiel on 2009-12-09
> **madshad said:**
> Ok Heres what Im trying to do... get my Conky to display what I playing on Atunes (using Mplayer as player, but will switch to xine if easier)

I got this script working with rythembox but i dont like rthymbox because i cant spell it...

```

${font Fontdinerdotcom Sparkly:size=30} Listening to ${font}
${font Fontdinerdotcom Sparkly:size=50} ${exec rhythmbox-client --no-start --print-playing-format "%ta"}${font}
${font Fontdinerdotcom Sparkly:size=30} ${exec rhythmbox-client --no-start --print-playing-format "%tt"} ${font}

$alignc ${font Fontdinerdotcom Sparkly:size=20} ${exec rhythmbox-client --no-start --print-playing-format "%te - %td"} ${font}

${font Fontdinerdotcom Sparkly:size=20}From their hit Album...
${font Fontdinerdotcom Sparkly:size=30} ${exec rhythmbox-client --no-start --print-playing-format "%at"}${font}
```

I tried to just change rythembox-client to mplayer and tried Atune too, no luck

i found this online somewhere in a non-english forum
```
${if_running MPlayerapp}
Playing:
${color ffaa00}${font Bistream Vera Sans:size=11}$alignc${execi 5 ~/.conky/MPlayer title}
${font Bistream Vera Sans:size=7}${color black}${voffset -5}by: ${color yellow}${execi 5 ~/.conky/MPlayer artist}
${color slate grey}from: ${color yellow}${execi 5 ~/.conky/MPlayer album}
${execibar 2 ~/.conky/MPlayer progress}${else}${color slate grey}${alignc}Cisza i spokój${endif}
```

but that didnt even show up on screen.

thanks for any help :)

It's probably because ```
${execi 5 ~/.conky/MPlayer ...
``` calls a script called *MPlayer* in the (hidden) *.conky* directory in your home dir. I'm guessing the script grabes artist, album and progress info from *mplayer*.

btw The CCCC (Collaborating Conky Config Community) resides in [this mega thread]("http://ubuntuforums.org/showthread.php?t=281865"). A great place for inspiration and asking for assistance.

---

### Post by Suky on 2009-12-23
Hi seldon77,

I would like to thanks for your tutorial, BTW May I have your fever to help me?

1. My conky windows width is take over a half of my desk top screen. How to resize like your example. I meant that my conky window look double width than your window.

2. I have warning message --- Conky: border_margin is deprecated, please use window.border_inner_margin instead --- When I comment at line "border margin 9" this message is not display.

3. What is "Fortune" and where should I get it from? I got message "sh: fortune: not found"

Thanks
:)

---

### Post by miegiel on 2009-12-23
> **Suky said:**
> Hi seldon77,

I would like to thanks for your tutorial, BTW May I have your fever to help me?

1. My conky windows width is take over a half of my desk top screen. How to resize like your example. I meant that my conky window look double width than your window.
The conky window resizes to the size it needs. There's probably a line (below the *TEXT* line) that makes the conky window that wide. Alternatively you can set the max width with
```
maximum_width 200
```
in the _config part_ of the *.conyrc* (above the *TEXT* line). The 200 value is the width in pixels, change it to the max width you want.

> 2. I have warning message --- Conky: border_margin is deprecated, please use window.border_inner_margin instead --- When I comment at line "border margin 9" this message is not display.
Change the line
```
border margin 9
```
to
```
border_inner_margin 9
```
The 9 value is the margin in pixels again. See [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) for more info on the config part of your *.conyrc* (and [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) for the variables part of your *.conyrc*).

> 3. What is "Fortune" and where should I get it from? I got message "sh: fortune: not found"

Thanks
:)
It refers to the fortune script that gets the fortune message for conky. Conky can't find it probably because you don't have the script in your home directory (try googling "conky fortune script" or something like that if you want to have it). Or just remove the
```
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```
lines.

---

### Post by Suky on 2009-12-23
Hi miegiel, Thanks for your help.:popcorn:

---

### Post by Suky on 2009-12-23
Hi miegiel, Thanks for your help.:popcorn:

maximum_width 200 --> working !!!

window.border_inner_margin --> error message "no such configuration: 'window.border_inner_margin'" So, I remarked and its work.

Thanks

---

### Post by DynastyX on 2010-01-01
Ok I've been working at this for a while and I keep getting errors so I need some help. This first one is particularly annoying.
```
Conky: border_margin is deprecated, please use window.border_inner_margin instead

```So to please Conky, I changed "border_margin" to "window.border_inner_margin"... Just as it asked, but now I get this error.
```
Conky: /home/steven/.conkyrc: 77: no such configuration: 'window.border_inner_margin'
```#-o

Then there's this too,
```
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

```How can I fix this? I'm also having troubles with the network monitor, I've tried all three variations you've suggested and I still see "Network (No Address)". I'm using 32bit Karmic and running wifi on my laptop.

All help is appreciated.

---

### Post by DynastyX on 2010-01-02
I fixed the boarder issue by simply getting rid of that line. I still can't get the network monitor to work, and I still get the (Not all processes could be identified, non-owned process info will not be shown, you would have to be root to see it all.) message.

---

### Post by stinkeye on 2010-01-02
It sounds like your trying to access some info that needs root permission.
Are you using hddtemp.If so, look here ...[_[COLOR="DarkRed"]http://conky.linux-hardcore.com/?page_id=427[/COLOR]_]("http://conky.linux-hardcore.com/?page_id=427")
If you post on this thread with your conky config someone will point you in the right direction.
[_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=1129[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=1129")

---

### Post by mltucker on 2010-01-25
> **miegiel said:**
> 
It refers to the fortune script that gets the fortune message for conky. Conky can't find it probably because you don't have the script in your home directory (try googling "conky fortune script" or something like that if you want to have it). Or just remove the
```
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```
lines.

The problem is that it's trying to execute the fortune program which you haven't installed (you can execute arbitrary shell commands with execi).  To install fortune, use

```

sudo apt-get install fortune

```

So to summarize this bit of the conky config, "${color orange}" means set the color to orange, "FORTUNE" prints fortune, "${hr 2}" means print a horizontal rule of height 2, "$color" ends the orange coloring.  Next, "execi 120" execute and insert the results of the following command every 120 seconds, which is "fortune -s | fold -w50".  "fortune -s" prints a short adage, while "fold -w50" wraps the lines at width 50.  Use "man fortune" and "man fold" to learn more about these commands.

---

### Post by l3git.h4cker on 2010-01-25
Ah yes this I've been looking for something like his for a long time.
Rainmeter hasn't quite met my expectations when it comes to wine.

---

### Post by michaelparez on 2010-01-30
Thanks for the steps given for the ubuntu screen savers and other desktop settings.

---

### Post by tstrike on 2010-03-09
Hi guys.... how do expand the size of the box that Conky runs in???  I am also having problems with some flickering...  One final thing.... is there like a general repository that we can just look at Conky types and scripts.... been dredging thru 1000k posts is insane LOL  Thanks in advance for your contributions my friends

---

### Post by trayzz on 2010-03-10
> **tstrike said:**
> Hi guys.... how do expand the size of the box that Conky runs in??? I am also having problems with some flickering... One final thing.... is there like a general repository that we can just look at Conky types and scripts.... been dredging thru 1000k posts is insane LOL Thanks in advance for your contributions my friends

this command should do it:
```
minimum_size x y
```i'm not sure whether there's a repository for that or not. maybe you want to check this page though, [http://conky.linux-hardcore.com/?page_id=352](http://conky.linux-hardcore.com/?page_id=352)

---

### Post by tstrike on 2010-03-10
> **trayzz said:**
> this command should do it:
```
minimum_size x y
```i'm not sure whether there's a repository for that or not. maybe you want to check this page though, [http://conky.linux-hardcore.com/?page_id=352](http://conky.linux-hardcore.com/?page_id=352)

Thanks Trayzz... I will check this out and circle back with my results. I deeply appreciate your help.  Ubuntu is fun indeed.

---

### Post by stinkeye on 2010-03-10
You can also use  
```
maximum_width
```
along with the previous config setting to set a fixed width

eg
```
minimum_size 300
maximum_width 300
```

[_**[COLOR="DarkRed"]Conky Hardcore[/COLOR]**_]("http://conky.linux-hardcore.com/") is good site to have a look at.

---

### Post by tstrike on 2010-03-10
> **stinkeye said:**
> You can also use  
```
maximum_width
```along with the previous config setting to set a fixed width

eg
```
minimum_size 300
maximum_width 300
```[_**[COLOR=DarkRed]Conky Hardcore[/COLOR]**_]("http://conky.linux-hardcore.com/") is good site to have a look at.

 Here is the problem I am having ...

---

### Post by stinkeye on 2010-03-10
If you don't set a maximum_width the width of your conky will be set 
by the line that draws the widest.
At the moment it looks like it may be your gmail section.

Post your conky config so I can have a look.
What's your screen resolution?
If your problem is cutting off of your gmail
increase your "y" value in
minimum_size x y
to almost your vertical screen size.

---

### Post by tstrike on 2010-03-10
Below is my conkrc

use_xft yes
xftfont OpenLogos DejaVu Sans Mono:size=8

update_interval 2
total_run_times 0
double_buffer yes
text_buffer_size 3072

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 400 400
maximum_width 400 400


default_color white
draw_shades no

color0 white
color1 E07A1F
color2 green

alignment top_right
gap_x 10
gap_y 5

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
${font Arial Black:size=10}${time %H:%M}${alignr}${time %d %B %Y}${font}${image ~/.scripts/pc.png -p 210,50 -s 80x80}${image ~/.scripts/hd.png -p 200,148 -s 50x50}${image ~/.scripts/proc.png -p 200,200 -s 90x90}${image ~/.scripts/red.png -p 190,335 -s 100x100}

${color1}${font Zekton:style=Bold:pixelsize=13}System Information [ ${nodename} ${machine} ]${font} ${hr 2}${alignr}${color}
${voffset +1}${font OpenLogos:size=15}u${voffset -4}${font}   Ubuntu 9.04 ${kernel}${voffset -5}${alignr 15}${font OpenLogos:size=15}  T${voffset -4}${font}Gnome 2.28.0
${voffset +3}${font Illustrate IT:size=15}I${voffset -6}${font}   INTEL DUAL CPU 2 x ${freq 1} MHz${alignr}CPU: ${cpu cpu1}%   ${cpugraph cpu1 8,50}
${voffset +5}${font StyleBats:size=15}g${voffset -4}${font}   RAM Free : ${memmax}${alignr}Usage: $memperc%   ${membar 8,50}
${voffset +3}${font StyleBats:size=15}v${voffset -4}${font}   Update: ${execi 600 aptitude search "~U" | wc -l | tail} package(s)${alignr 10}${voffset +1}${font StyleBats:size=15}q${voffset -4}${font}  Uptime: ${uptime}
${color1}${font Zekton:style=Bold:pixelsize=13}Disc Data ${font} ${hr 2}${color}
${font Pie charts for maps:size=13}7${font}${voffset -4}   ${fs_used /}/${fs_size /} ${fs_bar 8,50 /}${tab 138}${voffset -4}${font PizzaDude Bullets:size=13}J${font}${voffset -1} Lectura  :${tab 10}${diskio_read /dev/sda}${alignr 2}${diskiograph_read /dev/sda 8,50}
${font StyleBats:size=16}${voffset +1}l${font}${voffset -5}   Temperature ${execi 300 hddtemp /dev/sda -n;}° C ${tab 138}${font PizzaDude Bullets:size=13}q${font} Write Rate:${tab 10}${diskio_write /dev/sda}${alignr 2}${diskiograph_write /dev/sda 8,50}
${color1}${font Zekton:style=Bold:pixelsize=13}Processes ${font} ${hr 2}${color}
$font$processes procesos  ($running_processes activos)
${color green}NAME $alignr CPU     MEM${color}
${top name 1} $alignr ${top cpu 1}   ${top mem 1}
${top name 2} $alignr ${top cpu 2}   ${top mem 2}
${top name 3} $alignr ${top cpu 3}   ${top mem 3}
${top name 4} $alignr ${top cpu 4}   ${top mem 4}
${top name 5} $alignr ${top cpu 5}   ${top mem 5}
${color1}${font Zekton:style=Bold:pixelsize=13}Network Stats ${font} ${hr 2}${color}
${voffset +2}${font PizzaDude Bullets:size=11}O${font}   Up: ${upspeed wlan0}${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset +2}${font PizzaDude Bullets:size=11}U${font}   Down: ${downspeed wlan0}${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset +2}${font PizzaDude Bullets:size=11}N${font}   TDown: ${alignr}${totalup wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}T${font}   TUp: ${alignr}${totaldown wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}Y${font}   Bit Rate:  ${alignr}${wireless_essid wlan0} a ${wireless_bitrate wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}Z${font}   Signal Str:  ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}a${font}   Ip Local: ${alignr}${addr wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}b${font}   Ip Public: ${alignr}${execi 1 ~/.scripts/ip.sh}
You have ${color3}${texeci 60 perl ~/.scripts/gmail.pl n} ${color}new gmail(s).
${execi 60 perl ~/.scripts/gmail.pl s}

---

### Post by stinkeye on 2010-03-10
try this
```
use_xft yes
xftfont OpenLogos DejaVu Sans Mono:size=8

update_interval 2
total_run_times 0
double_buffer yes
text_buffer_size 3072

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 400 700
maximum_width 400 


default_color white
draw_shades no

color0 white
color1 E07A1F
color2 green

alignment top_right
gap_x 10
gap_y 5

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
${font Arial Black:size=10}${time %H:%M}${alignr}${time %d %B %Y}${font}${image ~/.scripts/pc.png -p 210,50 -s 80x80}${image ~/.scripts/hd.png -p 200,148 -s 50x50}${image ~/.scripts/proc.png -p 200,200 -s 90x90}${image ~/.scripts/red.png -p 190,335 -s 100x100}

${color1}${font Zekton:style=Boldixelsize=13}System Information [ ${nodename} ${machine} ]${font} ${hr 2}${alignr}${color}
${voffset +1}${font OpenLogos:size=15}u${voffset -4}${font} Ubuntu 9.04 ${kernel}${voffset -5}${alignr 15}${font OpenLogos:size=15} T${voffset -4}${font}Gnome 2.28.0
${voffset +3}${font Illustrate IT:size=15}I${voffset -6}${font} INTEL DUAL CPU 2 x ${freq 1} MHz${alignr}CPU: ${cpu cpu1}% ${cpugraph cpu1 8,50}
${voffset +5}${font StyleBats:size=15}g${voffset -4}${font} RAM Free : ${memmax}${alignr}Usage: $memperc% ${membar 8,50}
${voffset +3}${font StyleBats:size=15}v${voffset -4}${font} Update: ${execi 600 aptitude search "~U" | wc -l | tail} package(s)${alignr 10}${voffset +1}${font StyleBats:size=15}q${voffset -4}${font} Uptime: ${uptime}
${color1}${font Zekton:style=Boldixelsize=13}Disc Data ${font} ${hr 2}${color}
${font Pie charts for maps:size=13}7${font}${voffset -4} ${fs_used /}/${fs_size /} ${fs_bar 8,50 /}${voffset -4}${goto 255}${font PizzaDude Bullets:size=13}J${font}${voffset -1} Lectura :${diskio_read /dev/sda}${alignr 2}${diskiograph_read /dev/sda 8,50}
${font StyleBats:size=16}${voffset +1}l${font}${voffset -5} Temperature ${execi 300 hddtemp /dev/sda -n;}° C ${goto 240}${font PizzaDude Bullets:size=13}q${font} Write Rate :${diskio_write /dev/sda}${alignr 2}${diskiograph_write /dev/sda 8,50}
${color1}${font Zekton:style=Boldixelsize=13}Processes ${font} ${hr 2}${color}
$font$processes procesos ($running_processes activos)
${color green}NAME $alignr CPU MEM${color}
${top name 1} $alignr ${top cpu 1} ${top mem 1}
${top name 2} $alignr ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top cpu 3} ${top mem 3}
${top name 4} $alignr ${top cpu 4} ${top mem 4}
${top name 5} $alignr ${top cpu 5} ${top mem 5}
${color1}${font Zekton:style=Boldixelsize=13}Network Stats ${font} ${hr 2}${color}
${voffset +2}${font PizzaDude Bullets:size=11}O${font} Up: ${upspeed wlan0}${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset +2}${font PizzaDude Bullets:size=11}U${font} Down: ${downspeed wlan0}${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset +2}${font PizzaDude Bullets:size=11}N${font} TDown: ${alignr}${totalup wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}T${font} TUp: ${alignr}${totaldown wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}Y${font} Bit Rate: ${alignr}${wireless_essid wlan0} a ${wireless_bitrate wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}Z${font} Signal Str: ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}a${font} Ip Local: ${alignr}${addr wlan0}
${voffset +2}${font PizzaDude Bullets:size=11}b${font} Ip Public: ${alignr}${execi 1 ~/.scripts/ip.sh}
You have ${color3}${texeci 60 perl ~/.scripts/gmail.pl n} ${color}new gmail(s).
${execi 60 perl ~/.scripts/gmail.pl s}
   	
```

When you want to insert code in the forums use the # button and paste between the [/CODE] blocks.

Also you need to install hddtemp to see your drive temperature.
[**_[COLOR="DarkRed"]Using hddtemp[/COLOR]_**]("http://conky.linux-hardcore.com/?page_id=427")

---

### Post by stinkeye on 2010-03-10
Actually, your original conky should display properly by changing
```
minimum_size 400 400
maximum_width 400 400 
```
to
```
minimum_size 450 [COLOR="DarkRed"]700[/COLOR]
maximum_width 450 
```

and just increase [COLOR="DarkRed"]700[/COLOR] if you can't see all your gmail.

---

### Post by tstrike on 2010-03-11
> **stinkeye said:**
> Actually, your original conky should display properly by changing
```
minimum_size 400 400
maximum_width 400 400 
```to
```
minimum_size 450 [COLOR=DarkRed]700[/COLOR]
maximum_width 450 
```and just increase [COLOR=DarkRed]700[/COLOR] if you can't see all your gmail.

This worked quite well and thanks for the wonderful assistance. Everything got fixed with your code suggestion. In the future I think I will include the weather but I want to see how much real estate the weather takes...

Please see the attached screenie that incorporates your changes.

---

### Post by Random_Dude on 2010-03-27
Noob question: What do you do after saving the .conkyrc file?

I've tried opening the console and type "conky", it starts the program but all I get is an ugly black window on my desktop.

I'm still inexperienced in ubuntu, could someone explain me how conky works?

Thanks

---

### Post by miegiel on 2010-03-27
> **Random_Dude said:**
> Noob question: What do you do after saving the .conkyrc file?

I've tried opening the console and type "conky", it starts the program but all I get is an ugly black window on my desktop.

I'm still inexperienced in ubuntu, could someone explain me how conky works?

Thanks

By default, if you saved *.conkyrc* in your */home/you/*, running *conky* in a terminal should use the *.conkyrc* you made to run. If you want to run a conky script with a different mane or saved somewhere else use :
```
conky -c /home/[COLOR="Blue"]you/where.conky.script.is.saved/conky.script[/COLOR]
```
[COLOR="blue"]Change to what ever your username/path/script is[/COLOR]

More info on running conky :
```
conky -h
```

---

### Post by Random_Dude on 2010-03-27
Thanks for the help :).
I've seen what the problem was.

Now I have some other minor problems:

> Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (20000cf) is subwindow of root window (10a)
Conky: window type - override
Conky: drawing to created window (0x5200001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory


Some of the info in the window doesn't appear, but at least it isn't black. :lol:
I'll try to fix this when I have the time.;)

---

### Post by miegiel on 2010-03-27
> **Random_Dude said:**
> Thanks for the help :).
I've seen what the problem was.

Now I have some other minor problems:

```
Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (20000cf) is subwindow of root window (10a)
Conky: window type - override
Conky: drawing to created window (0x5200001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
```

Some of the info in the window doesn't appear, but at least it isn't black. :lol:
I'll try to fix this when I have the time.;)

Check your conky script above the TEXT line and replace *border_margin* with *border_inner_margin*

Next check your conky script below the TEXT line for */media/sda1* and replace it by something that makes sense , like a single / for your root partition or */home/* for your home partition, etc. (if you only have 1 partition just use /).

---

### Post by Random_Dude on 2010-03-28
> **miegiel said:**
> Check your conky script above the TEXT line and replace *border_margin* with *border_inner_margin*

Next check your conky script below the TEXT line for */media/sda1* and replace it by something that makes sense , like a single / for your root partition or */home/* for your home partition, etc. (if you only have 1 partition just use /).

Thanks miegiel!
I had to manually install Ubuntu along with windows, so I have more than one partition on my hard drive (if this is what you mean by partition). Still, I used the / and I think it's working fine.

> Conky: desktop window (20000cf) is subwindow of root window (10a)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer
sh: fortune: not found


Is there still something missing?

---

### Post by miegiel on 2010-03-28
> **Random_Dude said:**
> Thanks miegiel!
I had to manually install Ubuntu along with windows, so I have more than one partition on my hard drive (if this is what you mean by partition). Still, I used the / and I think it's working fine.

```
Conky: desktop window (20000cf) is subwindow of root window (10a)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer
sh: fortune: not found
```

Is there still something missing?

Yes, install fortune (if you want to use it) or remove the fortune bit in your conky. It probably looks like *${execi 120 fortune -s | fold -w50}*

```
sudo apt-get install fortune
```

Here are some examples of fortunes output :
```
user@machine:~$ fortune 
Chicken Little was right.
user@machine:~$ fortune 
Many enraged psychiatrists are inciting a weary butcher.  The butcher is
weary and tired because he has cut meat and steak and lamb for hours and
weeks.  He does not desire to chant about anything with raving psychiatrists,
but he sings about his gingivectomist, he dreams about a single cosmologist,
he thinks about his dog.  The dog is named Herbert.
		-- Racter, "The Policeman's Beard is Half-Constructed"
user@machine:~$ fortune 
I think we are in Rats' Alley where the dead men lost their bones.
		-- T.S. Eliot
```

Now you've gotten this far, check [this thread]("http://ubuntuforums.org/showthread.php?t=281865") for inspiration. There are some great conkies there and it's a good place to ask for tips/help (my conky is at post8487787). And of course, it's a good place to show off you conky creations.

---

### Post by Random_Dude on 2010-03-28
Thanks for everything miegiel.

I just have one final question:
When I run conky and try to close the console, it says it'll kill the program but it doesn't, so I just close it anyway. Is this supposed to happen? Does it affect the system?

Thanks again.;)

---

### Post by miegiel on 2010-03-28
> **Random_Dude said:**
> Thanks for everything miegiel.

I just have one final question:
When I run conky and try to close the console, it says it'll kill the program but it doesn't, so I just close it anyway. Is this supposed to happen? Does it affect the system?

Thanks again.;)

You're welcome and yes, it used to kill conky, sometimes it still does. If you don't want to keep a terminal open, start conky with the *-d* switch.

---

### Post by meral.ch on 2010-04-29
Great howto!

I confirm smooth sailing under ubuntu 10.4 :)

The most important thing is the example .conkyrc file.



Forget adesklets, gdesklets and the rest. Conky FTW! :)

---

### Post by Spencer Caplan on 2010-07-27
So for the most part I have been able to navigate my way through Conky, but I seem to be stuck figuring out how to so the coloring for the inside parts of the graphs only, not the whole thing. For example, I can make the entire graph of CPU activity Indigo, but how do I change only the inside while leaving the outline black (or whatever color I choose?) Thanks in advance for the help!

---

### Post by Jonny87 on 2010-10-07
I'm loving it!
Just a couple questions though, sorry if they've been covered, I have tried reading every page.

The Network Meter.
I saw in a post that it was possible to get it saying an weekly/monthly total upload/download. Is it possible to get it to keep an indefinite total, regardless of restarting the computer?
If so how?

The Disk space.
I've manged to add another one for an extra HDD that I have but it's not always mounted. Is there a way to get that one to only show when its mounted instead of having it say 100% when its not mounted?
Here is the line that I have so far;
```
Library:  ${fs_free_perc /media/Library}%   ${fs_bar 6 /media/Library}$color
```

---

### Post by anhnt on 2011-03-27
I use ubuntu 10.10 amd 64 in laptop asus a42f,and install conky.But it doesn't display temperatur and battery.Anyone help me?
Code:
  # Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorate,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color D9D4CC
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 45

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${font :size=10:style=bold}SYSTEM${font} ${hr 1}
${voffset 8}${font OpenLogos:size=16}${color 7B9494}u${color}${font}    ${voffset -6}User:  ${alignr 20}${exec users | cut -d " "  -f1}@${nodename}
${voffset 3}         Release:  ${alignr 20}${pre_exec lsb_release -r -s} (${pre_exec lsb_release -c -s})
${voffset 3}         Kernel:  ${alignr 20}${kernel}
${voffset 3}         Updates: ${alignr 20}${execi 28800 OSUpdate} available
${voffset 8}${font StyleBats:size=16}${color 7B9494}A${color}${font}    ${voffset -5}CPU1: ${cpu cpu1}% / ${color 7B9494}${exec sensors | grep  "Core0" | cut -d "+" -f2 | cut -c1-6}C${color}${alignr}${color  7B9494}${cpubar cpu1 8,60}${color}
#${font StyleBats:size=16}${color 7B9494}A${color}${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${voffset 5}${font StyleBats:size=16}${color 7B9494}g${color}${font}    ${voffset -5}RAM: $memperc% ${alignr}${color 7B9494}${membar  8,60}${color}
${voffset 5}${font StyleBats:size=16}${color 7B9494}j${color}${font}    ${voffset -5}SWAP: $swapperc% ${alignr}${color 7B9494}${swapbar  8,60}${color}
${voffset 5}${font Webdings:size=16}${color 7B9494}~${color}${font}   ${voffset -5}Battery: ${battery_percent BAT1}% ${alignr}${color  7B9494}${battery_bar 8,60 BAT1}${color}
${voffset 5}${font StyleBats:size=16}${color 7B9494}q${color}${font}   ${voffset -5}Uptime: ${alignr}${uptime}
${voffset 5}${font StyleBats:size=16}${color 7B9494}k${color}${font}    ${voffset -5}Processes: ${alignr}$processes ($running_processes running)
${voffset 10}${font :size=10:style=bold}FILE SYSTEM${font} ${hr 1}
${voffset 8} ${color 7B9494}${font Weather:size=17}yz${font}${color}     ${voffset -4}Temperatur: ${color 7B9494}${hddtemp  /dev/sda}°C${color}${alignr}/dev/sda
${voffset 8}${font Poky:size=15}${color 7B9494}y${color}${font}${offset  6}${voffset -7}Root: ${font Liberation Sans:size=8}${color  7B9494}${fs_used_perc /}%${font}${color}
${color 7B9494}${voffset 2}${fs_bar 4,20 /}${offset 8}${voffset -2}${color}Free: ${fs_free /}${alignr}Used: ${fs_used /}
${voffset 8}${font Poky:size=15}${color 7B9494}y${color}${font}${offset  6}${voffset -7}Home: ${font Liberation Sans:size=8}${color  7B9494}${fs_used_perc /home}%${font}${color}
${color 7B9494}${voffset 2}${fs_bar 4,20 /home}${offset 8}${voffset  -2}${color}Free: ${fs_free /home}${alignr}Used: ${fs_used /home}
${voffset 8}${font :size=10:style=bold}NETWORK${font} ${hr 1}
${if_existing /proc/net/route wlan0}
${voffset 2}${color 7B9494}${voffset -6}${font PizzaDude  Bullets:size=14}O${color}${font}   ${voffset -2}Up: ${upspeed wlan0}  kb/s ${alignr}${color 7B9494}${upspeedgraph wlan0 8,60}${color}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}U${color}${font}   ${voffset -2}Down: ${downspeed wlan0}  kb/s ${alignr}${color 7B9494}${downspeedgraph wlan0 8,60}${color}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}N${color}${font}   ${voffset -2}Upload:  ${alignr}${totalup wlan0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}T${color}${font}   ${voffset -2}Download:  ${alignr}${totaldown wlan0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}Z${color}${font}   ${voffset -2}Signal:  ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}a${color}${font}   ${voffset -2}Local Ip:  ${alignr}${addr wlan0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}b${color}${font}   ${voffset -2}Public Ip:  ${alignr}${execi 1 ~/Conky/scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset 2}${color 7B9494}${voffset -6}${font PizzaDude  Bullets:size=14}O${color}${font}   ${voffset -2}Up: ${upspeed eth0} kb/s  ${alignr}${color 7B9494}${upspeedgraph eth0 8,60}${color}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}U${color}${font}   ${voffset -2}Down: ${downspeed eth0}  kb/s ${alignr}${color 7B9494}${downspeedgraph eth0 8,60}${color}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}N${color}${font}   ${voffset -2}Upload:  ${alignr}${totalup eth0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}T${color}${font}   ${voffset -2}Download:  ${alignr}${totaldown eth0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}a${color}${font}   ${voffset -2}Local Ip:  ${alignr}${addr eth0}
${voffset 2}${color 7B9494}${voffset 4}${font PizzaDude  Bullets:size=14}b${color}${font}   ${voffset -2}Public Ip:  ${alignr}${execi 1 ~/Conky/scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}




[IMG]http://i239.photobucket.com/albums/ff57/tuananh86vn/Screenshot-4.png[/IMG]

---

### Post by stinkeye on 2011-03-27
Install hddtemp and lm-sensors
[**_[COLOR="DarkRed"]http://conky-pitstop.wikidot.com/programs[/COLOR]_**]("http://conky-pitstop.wikidot.com/programs")


Your also missing the [**_[COLOR="#8b0000"]Open Logos[/COLOR]_**]("http://www.dafont.com/openlogos.font") and [**_[COLOR="DarkRed"]StyleBats[/COLOR]_**]("http://www.dafont.com/style-bats.font") fonts,
which is why you see the large letters down the left side.

---

### Post by TerryP on 2011-12-19
Good info that is still relevant. :)

---

### Post by DGINSD on 2012-09-05
> **trazart said:**
> To remove the shadow from the conky window you can also play with your Window Decoration preferences. Change which windows should have, or should not have, shadows.

[IMG]http://bayimg.com/image/gammcaabh.jpg[/IMG]

And add the line below to your .conkyrc file.
```
own_window_title mi_conky
```

I realize this is a very old post but can someone shed a little light on how to get rid of the shadow decoration on the conky window?

---

### Post by bra|10n on 2012-09-05
own_window_type override
or
own_window_type normal

You can find a current conky thread with plenty of help in the Community Cafe...

---

### Post by astrobob.tk on 2013-08-17
> **Stoneface said:**
> Right clicking or left clicking on the Desktop makede it disappear until I changed:
```
own_window_type desktop
```
to
```
own_window_type override
``` :P

Thanks :D That solved my problem too :D

---

### Post by 3dmatrix on 2013-09-11
I have just installed conky but i am not able to locate any script or programme to edit / configure it. Plz advise.

---

