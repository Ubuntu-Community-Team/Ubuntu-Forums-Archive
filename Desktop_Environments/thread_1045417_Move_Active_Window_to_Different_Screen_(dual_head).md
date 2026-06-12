---
title: "Move Active Window to Different Screen (dual head)"
date: 2009-01-20
forum: Desktop Environments
---

### Post by enthooz on 2009-01-20
I was looking for a built-in method of moving the active window between screens in a dual-head Gnome environment using keyboard shortcuts.  Instead of the solution, I found many others looking for the same.  Here's the solution I came up with.

It's limited in that I can only specify to move the window to a specific X-coordinate on the screen -- in my case, I chose to move the active window to the left-most portion of whichever screen I choose, maintaining the Y-coordinate, width, and height of the screen.  This solution uses wmctrl.

[http://www.sweb.cz/tripie/utils/wmctrl/]("http://www.sweb.cz/tripie/utils/wmctrl/")

Also, I run Ubuntu 8.10 with Gnome (or Blackbox), but that should be irrelevant as this solution should even work in Fluxbox, Enlightenment, or any other EWMH/NetWM compatible X Window Manager.

[LIST=1]
[*]Install wmctrl.

```
sudo apt-get install wmctrl
```

[*]Go to the custom commands in the Compiz settings manager.  (System > Preferences > CompizConfig Settings Manager > General Options > Commands tab > Commands section)

[*]Add the following commands to move the window to the left screen:
```

wmctrl -r :ACTIVE: -e 0,0,-1,-1,-1
wmctrl -r :ACTIVE: -e 0,1440,-1,-1,-1

```
**NOTE:** Replace 1440 with whatever the horizontal screen resolution is of the left monitor.
**-r <WIN> -e <G>,<X>,<Y>,<W>,<H>** resize/move the window using gravity, x, y, width, height
(gravity of 0 uses window's default gravity and values of -1 specify window's properties for other values.)
The first command above will move the active window to the left most edge of the viewing space.
The second command will move the active window to the 1440 pixels from the left most edge.  In my case, the resolution of my left monitor is 1440x900.  Change 1440 to reflect the horizontal resolution of your setup.

[*]Finally, open the Key Bindings section and create keyboard shortcuts associated with the above commands.  I use <Alt><Super>Left and <Alt><Super>Right, respectively.  These coordinate well with the keyboard shortcuts I use to move screens to other viewports: <Alt><Super>Tab and <Alt><Super><Shift>Tab.

[*]That's all.  Close the Compiz Settings Manager and try it out.
[/LIST]

Please let me know if I made any mistakes transcribing these steps.  Also, I would love some feedback on how to maintain the relative x-coordinate of the screen while moving.  I'm sure there's a better utility than the minimal wmctrl.

Hope this helps.

Yours in linux,
Andrew

---

### Post by ssergeje on 2009-06-04
Tnx a lot for this solution. Worked well on 9.04 :)

Since my second monitor is below and I didn't want the windows to be sticked to the edges my conf was as follows:

```

wmctrl -r :ACTIVE: -e 0,50,50,-1,-1
wmctrl -r :ACTIVE: -e 0,100,950,-1,-1

```

I also suggest using Grid plugin on Dual Head.

---

### Post by enthooz on 2009-06-04
Thanks, I'm glad someone found use for this post.  :)

The Grid plugin is great.  Thanks!

Here's a link to a post that explains how to install it for anyone else:
[http://wiki.compiz.org/Plugins/Grid]("http://wiki.compiz.org/Plugins/Grid")

It also mentions at the bottom that the following command *should* install Grid, but that it did not work for the author (I already had it installed by the time I read that):
```
sudo apt-get build-dep compiz-fusion-plugins-main
```

Cheers,
Andrew

---

### Post by kitrule on 2009-07-23
I got excited because I presumed this would shift the window between x-screens, but on my setup it only switches the window between workspaces. What graphics adaptor and drivers are you using?

---

### Post by enthooz on 2009-07-23
> **kitrule said:**
> I got excited because I presumed this would shift the window between x-screens, but on my setup it only switches the window between workspaces. What graphics adaptor and drivers are you using?

@kitrule: I'm using an NVidia GeForce 8800 GT adaptor and the 'nvidia' driver.

This basic functionality of this tip is to change the x position of a window.  If your desktop spans two monitors, changing the x-position of a window equal to or greater than the resolution of the left monitor will effectively position the window on right monitor.  I realize after reading your post that the title should be "Move Active Window to Different Monitor Using TwinView".

It sounds like you're using Xinerama which, as I understand, creates two separate x sessions and displays them on each monitor separately.  Is there a reason you're not using TwinView to have your screen span across both monitors?

---

### Post by kitrule on 2009-07-23
Hi, it's not Xinerama but the native support for separate x screens in the nvidia-settings panel that I'm using. This is for a few reasons:

. VNC-ing in to my desktop when twin-view is configured is unbearably irritating to work with.
. One of the DVIs is connected to my tv so if I'm watching a video on that whilst using VNC from my laptop the video ends up getting piped through the VNC connection and hogging the bandwidth.
. A lot of fullscreen 3d games (e.g. nexuiz) often try to pan across my monitors, thinking that I just have one exceptionally wide screen. I haven't tried it yet, but I'm sure it'll be nice to play a game through the TV whilst watching IRC or torrents download on the monitor when i'm respawning.

I was using VLC to output videos fullscreen only to my tv using ":0.1" but I've upgraded to karmic and that's broken (across x-sessions and within twinview -i think) so I was hoping I'd find another way of transferring the fullscreen video to the tv. At the moment I have to start VLC on my tv and then manage the playlist and options there. The TVs not really up to displaying text well so it would be beneficial to transfer windows between x screens on the fly. I suppose thinking of them as separate x sessions rather than just screen makes it easier to understand why it's not such a simple task and hasn't been developed yet.

Thanks for your quick reply though.

---

### Post by enthooz on 2009-07-23
> **kitrule said:**
> Thanks for your quick reply though.

No worries.  Sounds like you have quite a setup there.  That's the best thing about linux -- just being able to hack away at it and tweak it just to your liking.  Here at work, I just got another monitor -- three total.  We just had this other monitor hangin' around and it's a touch-screen (we develop touch screen kiosks).  Unfortunately, I haven't been able to get it calibrated properly in linux so the y-axis is inverted and it uses the touch area to represent the entire viewable area.  Maybe I'll get it figured out later on.

Here's to our solving out both our issues!

Cheers,
Andrew

---

### Post by 1proton on 2009-09-29
You can also use the 'put' plugin with the 'put to next output' setting from compiz to move windows around. 
[http://wiki.compiz.org/Plugins/Put](http://wiki.compiz.org/Plugins/Put)

Thx for the hint with the Grid plugin.

Regards,
1Proton

---

### Post by f0rcegr0wn on 2010-11-25
I don't know about you guys, but on 10.10 I simply can't get the suggestion working. Neither the put or any other suggestion works to send the active window to another X Screen.

My setup is 3 monitors and 2 cards, 2 monitors on a 8800 GT and one on 210. Xinerama works (but disables compiz) so in an attempt to keep compiz I am trying to work with the screens by sending active window to relevant x-screen.

It's been a while since last post here but I'm hoping someone would know how to handle this in Ubuntu. I have everything setup but this is the last frontier I can't get over.

---

### Post by chips617 on 2010-12-07
I'm using 10.10 with Gnome and the script below works for me. I only have two screens (Lenovo T410 laptop and a second display).

Kudos to these guys for doing most of the actual thinking:
[http://averagepenguin.com/?p=266](http://averagepenguin.com/?p=266)

The script uses xdotool, so grab it if you don't have it installed.

```
sudo apt-get install xdotool
```

Script:

```
#!/bin/bash
#++++++++++++++++
# Monitor Switch
#
# Moves currently focused window from one monitor to the other.
# Designed for a system with two monitors.
# Script should be triggered using a keyboard shortcut.
# If the window is maximized it should remain maximized after being moved.
# If the window is not maximized it should retain its current size, unless
# height is too large for the destination monitor, when it will be trimmed.
#++++++++++++++++

# resolution of left monitor
w_l_monitor=1440
h_l_monitor=900
# resolution of right monitor
w_r_monitor=1280
h_r_monitor=1024

# window title bar height (default title bar height in Gnome)
h_tbar=29

# focus on active window
window=`xdotool getactivewindow`

# get active window size and position
x=`xwininfo -id $window | grep "Absolute upper-left X" | awk '{print $4}'`
y=`xwininfo -id $window | grep "Absolute upper-left Y" | awk '{print $4}'`
w=`xwininfo -id $window | grep "Width" | awk '{print $2}'`
h=`xwininfo -id $window | grep "Height" | awk '{print $2}'`

# window on left monitor
if [ "$x" -lt "$w_l_monitor" ]; then
	new_x=$(($x+$w_l_monitor))
	new_y=$(($y-$h_tbar))
	xdotool windowmove $window $new_x $new_y
	# retain maximization
	if [ "$w" -eq "$w_l_monitor" ]; then
		xdotool windowsize $window 100% 100%
	# adjust height
	elif [ "$h" -gt $(($h_r_monitor-$h_tbar)) ]; then
		xdotool windowsize $window $w $(($h_r_monitor-$h_tbar))
	fi

# window on right monitor
else
	new_x=$(($x-$w_l_monitor))
	new_y=$(($y-$h_tbar))
	xdotool windowmove $window $new_x $new_y
	# retain maximization
	if [ "$w" -eq "$w_r_monitor" ]; then
	  	xdotool windowsize $window 100% 100%
	# adjust height
	elif [ "$h" -gt $(($h_l_monitor-$h_tbar)) ]; then
		xdotool windowsize $window $w $(($h_l_monitor-$h_tbar))
	fi
fi

```

---

### Post by robbie d on 2010-12-07
@f0rcegr0wn, how did you get two cards to work?????
I'm running dual 9500's (with one screen plugged into each) and cannot get my second card to detect. I've put many posts up in the forums here to no avail.

---

### Post by ksatta on 2010-12-08
I've also been looking for this, thanks.

I didn't read the whole thread, so I created another script :D

Well, here it is:
```

# ssfaw (switch_screen_for_active_window)
# by Kimmo Satta (ksatta.linux@gmail.com)

# configurable params
SCREEN_0_WIDTH=1680
# configurable params end here

ver=0.1

echo "ssfaw $ver (switch_screen_for_active_window)"
echo "by Kimmo Satta (ksatta.linux@gmail.com)"
 
maximize_cmd="wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz"
unmaximize_cmd="wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz"
move_to_screen_0="wmctrl -r :ACTIVE: -e 0,0,-1,-1,-1"
move_to_screen_1="wmctrl -r :ACTIVE: -e 0,$SCREEN_0_WIDTH,-1,-1,-1"

screen_arg=$1

case $screen_arg in
   0)
      $unmaximize_cmd
      $move_to_screen_0
      $maximize_cmd
      ;;

   1)
      $unmaximize_cmd
      $move_to_screen_1
      $maximize_cmd
      ;;

   *)	
      echo 
      echo "Moves active window to given screen and maximizes it."
      echo 
      echo "Usage ssfaw [screen number]"
      echo "Screen number can be 0 or 1"
      ;;
esac

```

I think I'll personally use it with xbindkeys.

---

### Post by oarion7 on 2011-04-21
> **chips617 said:**
> 
```

[CODE]#!/bin/bash
#++++++++++++++++
# Monitor Switch
#
# Moves currently focused window from one monitor to the other.
# Designed for a system with two monitors.
# Script should be triggered using a keyboard shortcut.
# If the window is maximized it should remain maximized after being moved.
# If the window is not maximized it should retain its current size, unless
# height is too large for the destination monitor, when it will be trimmed.
#++++++++++++++++

```
(^Clipped)

This is a really excellent script. Thanks so much for posting this! I was searching the web with the same interest as OP and found this script got the job done nicely. I really wanted to do this in GNOME after using awesome window manager for a couple days (but did not adapt it as my default wm for other reasons). So I set this script to run at <super>o which is the same as the default option of doing this in awesome (the functionality is automatic in that software), and I conveniently had nothing bound at <super>o...

There are of course a few weaknesses with this script, and I am happy to say that as a very novice bash scripter (I started scripting in bash about 1 month ago) I managed to improve it for my own use.

One: I have one VGA card, but two monitors. The main one is an LCD that is usually connected to my laptop for my dual monitor desktop. The other is on the other side of my room (an old CRT) which I use as a TV. When I want to use one or the other, I unplug one and plug the other one in. I am fine with this setup, as I almost never use the other montior (I got it out of the garbage and use it strictly for watching TV in bed, which I rarely do anyway.)

The problem with this setup is that my CRT monitor and LCD monitor are of completely different dimensions and thus resolutions. Depending on which one is plugged in, I would need to modify this script or run an alternative version, with the correct resolutions put in. I am sure there are a lot of easier ways to do this; as I said, I am a novice. Because the height of either monitor is always 768px (the different is in horizontal pixels only), I only had to worry about vertical pixels...

```

# I may be using either one of two monitors on the right
# my right monitor is always 768 px vertical
# but the horizontal varies depending on which
# monitor I am using...

# get total horizontal size of both monitors
jip=`xdpyinfo | grep 'dimensions:' | awk '{print $2}' | cut -dx -f1`
# my left monitor should always be 1440px
jap=1440
jup=$(($jip - $jap))

# resolution of left monitor
w_l_monitor=1440
h_l_monitor=900
# resolution of right monitor
w_r_monitor=`echo $jup`
h_r_monitor=768

```
[SIZE="1"]Also, I **could** have saved a variable there. There is no reason for creating the "jup" variable and then echoing back to it in the "w_r_monitor" variable, but after only one month of beginning to make my own scripts (of any sort) I have already developed a bad habit of creating all strings in rhyming, nonsensical triples, Dr. Seuss style.[/SIZE]

As you can see, for **w_r_monitor** instead of a fixed value, it subtracts the fixed width of my main left laptop screen from the width of the total workspace, understanding that to be the horizontal resolution of my right monitor. No matter which monitor I use, the height is 768px, so I didn't have to worry about that variable.

Another inconvenience with this script, that applies probably to all nautilus users, is that if you do not have a window in view and accidentally run this script, or if you have clicked on the Desktop, then the current active window is actually detected as **"x-nautilus-desktop"**. Doing so rather messes up the desktop wallpaper as well as other things, and messed up my desktop to the point of having to restart my X server the first couple times I did it.

To avoid this, I simply wrapped the whole script **after** the initial variables are defined (importantly, after **window**) as follows...

```


#### (after the initial variables:) ####



joo=`xwininfo -id $window | grep "Window id: " | awk '{print $5}' | cut -d\" -f2`
coo="x-nautilus-desktop"

if [ "$joo" == "$coo" ]
then
	exit
else



#### (the rest of the script goes here) ####

fi

```

This way, if you get keyboard-tappy happy while the active window is the desktop, you don't mess up GNOME, instead the script simply cancels. Sorry about the length of this post, I just had a lot of redbull but thought it was appropriate to share my modifications.:guitar:

Thanks again for the beautiful script

---

### Post by hookdump on 2011-04-27
Thanks a lot for this tip!!! It was really useful :)

Btw: It worked on Ubuntu 10.04 with wmctrl

---

### Post by tcoffee on 2011-05-28
Script:

```
#!/bin/bash
#++++++++++++++++
# Monitor Switch
#
# Moves currently focused window from one monitor to the other.
# Designed for a system with two monitors.
# Script should be triggered using a keyboard shortcut.
# If the window is maximized it should remain maximized after being moved.
# If the window is not maximized it should retain its current size, unless
# height is too large for the destination monitor, when it will be trimmed.
#++++++++++++++++

...


```[/QUOTE]

This script works perfectly for me in 10.10 with TwinView. With both monitors rotated to vertical orientation, the TwinView configuration considers them to be horizontally oriented and vertically stacked; however, the script above can be used with the intuitive screen coordinates of their physical geometry, e.g.:

# resolution of left monitor
w_l_monitor=1200
h_l_monitor=1920
# resolution of right monitor
w_r_monitor=1200
h_r_monitor=1920

Previously, switching screens was the only thing I've had to use the mouse for in GNOME ... thanks for this handy solution!

---

### Post by cewan on 2011-06-27
I don't know why but the original script caused some problems for me.
The problem was reproduced in the following way:
1. Focus a window
2. Maximize it
3. Run the script (using keyboard shortcut)
4. Focus any other window
5. Focus the first window again
6. The window will now jump to the other monitor (where it was first maximized)

This did not happen for all windows, but it always happened for Chrome and Firefox.

I modified the script to remove this problem. Here is the modified version:

```
#!/bin/bash
#++++++++++++++++
# Monitor Switch
#
# Moves currently focused window from one monitor to the other.
# Designed for a system with two monitors.
# Script should be triggered using a keyboard shortcut.
#++++++++++++++++

# width of left monitor
w_l_monitor=1920

# focus on active window
window=`xdotool getactivewindow`

# get active window position and width
x=`xwininfo -id $window | grep "Absolute upper-left X" | awk '{print $4}'`
y_abs=`xwininfo -id $window | grep "Absolute upper-left Y" | awk '{print $4}'`
y_rel=`xwininfo -id $window | grep "Relative upper-left Y" | awk '{print $4}'`
w=`xwininfo -id $window | grep "Width" | awk '{print $2}'`

# unmaximize
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz

# calculate new x position
if [ "$x" -lt "$w_l_monitor" ]; then
	# window on left monitor
	new_x=$(($x+$w_l_monitor))
else
	# window on right monitor
	new_x=$(($x-$w_l_monitor))
fi

#move window. Need to subtract the relative y-position.
new_y=$(($y_abs-$y_rel))
xdotool windowmove $window $new_x $new_y

if [ "$w" -eq "$w_l_monitor" ]; then
	# maximize
	wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
fi
```

---

### Post by tomvanbraeckel on 2012-03-02
I expanded ksatta's script (thanks !) so that you don't need to specify which screen you want to move the window to.

It just moves the window to the other screen if no argument was given.

So if you run this script, your window will be unmaximized, moved to the other screen, and maximized again. 

```
# ssfaw (switch_screen_for_active_window)
# by Kimmo Satta (ksatta.linux@gmail.com)
# Screen toggle added by Tom Van Braeckel (tomvanbraeckel@gmail.com)

# configurable params
SCREEN_0_WIDTH=1366
# configurable params end here

ver=0.2

echo "ssfaw $ver (switch_screen_for_active_window)"
echo "by Kimmo Satta (ksatta.linux@gmail.com)"
echo "Screen toggle added by Tom Van Braeckel (tomvanbraeckel@gmail.com)"
echo
echo "Make sure you install wmctrl, xdotool and xwininfo or some things won't work !"

maximize_cmd="wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz"
unmaximize_cmd="wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz"
move_to_screen_0="wmctrl -r :ACTIVE: -e 0,0,-1,-1,-1"
move_to_screen_1="wmctrl -r :ACTIVE: -e 0,$SCREEN_0_WIDTH,-1,-1,-1"

screen_arg=$1

# if no argument was given, we just move the window to the other screen
if [ -z "$screen_arg" ]; then
        # detect on which screen the window currently is
        window=$(xdotool getactivewindow)
        x=$(xwininfo -id "$window" | grep "Absolute upper-left X" | cut -d ' ' -f 7)
        #echo "window = $window"
        #echo "x = $x"
        if [ "$x" -ge "$SCREEN_0_WIDTH" ]; then
                echo "Your window is on the right, so I'm moving it to the left"
                screen_arg=0
        else
                echo "Your window is on the left, so I'm moving it to the right"
                screen_arg=1
        fi
fi

case $screen_arg in
0)
$unmaximize_cmd
$move_to_screen_0
$maximize_cmd
;;

1)
$unmaximize_cmd
$move_to_screen_1
$maximize_cmd
;;

esac

```

---

