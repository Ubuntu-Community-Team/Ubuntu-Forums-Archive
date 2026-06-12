---
title: "Show host name on desktop"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by JSpaceCadet on 2007-08-03
Can someone tell me if it is possible to get the computer's host name to show up on the desktop?

If it is possible knowing how would be helpful too ;-)

I am working with a rack full of computers, switching from PC to PC being able to see the host name would sure make things go a lot smoother.

Thanks!
Joe

P.S.: This is something I have done on Windows in the past or I probably wouldn't have thought to ask.

---

### Post by BitTorrentBuddha on 2007-08-03
I'm pretty sure conky can get you where you want. Grab it from the repositories and look around, I'm giving it a shot right now and I'll post back with instructions if you don't figure it out first.```
sudo aptitude install conky
```

---

### Post by BitTorrentBuddha on 2007-08-03
It may be slightly overkill, but this'll get the job done:

1. Download Conky```
sudo aptitude install conky
```
2. Set up your .conkyrc```
gedit ~/.conkyrc
```And paste this into .conkyrc:```
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
default_color black

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
HOSTNAME: ${execi 30 hostname}
```
3. Save and close .conkyrc. Then start up conky.

*[color=red].conkyrc modified from seldon77's guide [here](http://ubuntuforums.org/showpost.php?p=1194508&postcount=1)*[/color]

---

### Post by john.nicholls on 2007-08-03
gkrellm will also display the host name.

---

### Post by JSpaceCadet on 2007-08-04
Thanks to both of you so far.  Both of the solutions work, but I could use a little more guidance...

First, one requirement is that I be able to do an automated installation of any solution.  I really don't want to have to do any more than I have to do on dozens (at this point) machines that are supposed to go out the door almost identically - with some exceptions of course.  I have put together an install script that is working pretty well.  I would like to be able to integrate the solution for the hostname display into that script.

Let me say one thing though, perhaps I should has said it in my initial post.
I am putting computers together for kids with autism and other special needs.  I'm giving them away and they will live in homes where parents have no idea what to do with them.  The kids are very sharp, but if things get changed somehow and don't work, or things move around on them such that they can't find what they need, life becomes difficult for them.  Kids with autism need structure, stability and consistency.  That is why I am working so diligently to make these systems solid.
I hope that helps you understand why I am very particular.  For my own systems I can play around infinitely.  For the kids, I have to get it as right as possible before they leave my office.
Onward....

Conky
This install is easy to install and I can script creation of the configuration file.  When I run conky, I get a number of warning messages, all of which look benign:

parent@frog:~$ conky
Conky: can't load font 'arial'
Conky: desktop window (100005c) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (3200003)
Conky: failed to set up double buffer
Conky: drawing to single buffer

I tried to load the font "purisa", "garuda" and "courier" which are all part of the system and found in xfontsel.  It failed to load all of these fonts.  Maybe this part is just an "oh well".

The config file for Conky that BitTorrentBuddha provided is clearly intended to be simple, and that is accomplished.  I can script that to just create the file since the default is blank (or doesn't exist - I didn't check to be sure).
The fact that Conky locks onto the desktop is ideal.  That way you can't close it accidentally.
The downside is that it's just not attractive, perhaps that is just a matter of configuring things differently so that it is.

GKrellm is very nice to look at.  The default installation includes a ton of measurements, almost all of which aren't needed.  The host name is all I was looking for, but the CPU monitor is very nice as well, and is attractive in the box GKrellm lives in, so I'd keep it in.  The config file for GKrellm states that you should edit it manually.  Going in through the GUI to turn off almost everything and perhaps some other config would be very time consuming, and odds are I would miss things here and there.
Also, I couldn't find a way to permanently attach GKrellm's window to the desktop itself, so that you can't "close" it or otherwise move it.  I tried playing with the "sticky" setting in the config gui, but didn't find that it did anything useful - from what I could tell.  I also tried turning on the setting to allow the window manager decorations, but even with that, the panel gui didn't get me anything more useful.

So far, I would use Conky, though it would be nice if it could be made more attractive.
If there were a way to automate the configuration of GKrellm to the way I need it, and to make it lock to the desktop, it would be a good choice.

If you have any thoughts on these issues I would love to hear them.

I appreciate the feedback I have gotten so far.
Thanks,
Joe

---

