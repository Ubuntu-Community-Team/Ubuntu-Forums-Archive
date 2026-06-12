---
title: "A few questions about Fluxbox, Nautilus, and Conky"
date: 2012-01-09
forum: Desktop Environments
---

### Post by KFwLsKvVAs on 2012-01-09
Hello,

I'm running Ubuntu 11.10 with fluxbox.  I found that without a program drawing the desktop, wallch (a wallpaper changer) doesn't work.  So far the only program that I know of that will draw the desktop and work with wallch is nautilus, so my startup script has nautilus as well as wallch --constant.  

Now I run into a problem with this setup when trying to run conky.  When I run conky it flashes on the desktop for a second, and then is immediately covered by nautilus.  I've tried different settings for "own_window_type" in my .conkyrc file, and none of them keep it above nautilus.  So I was wondering if there isn't maybe a different program that would enable wallch to work that wouldn't actually cover the desktop like nautilus does (when I right click before launching nautilus, I get the fluxbox menu, afterwards I get the normal gnome right click menu), or barring that if there's any way to set conky to be above nautilus so that it doesn't disappear.  

Also, is there any way to launch nautilus without actually opening a browser window?  I'm really only using it to draw the desktop, if there were a more elegant solution that would be so cool.  

Thanks for any help.

---

### Post by a z on 2012-01-13
i wouldn't use nautilus for wallpaper, kinda un-does the lightweight aspect of fluxbox - you're almost half way to running gnome at that point.
Feh is awesome for doing fluxbox wallpaper. there is a great feh/fluxbox wiki here:
[https://wiki.archlinux.org/index.php/Fluxbox#Using_Feh_with_FluxBox](https://wiki.archlinux.org/index.php/Fluxbox#Using_Feh_with_FluxBox)
cheers,
a z

ps, feh also probably won't draw your wallpaper OVER your conky

---

### Post by andrew.46 on 2012-01-15
> **a z said:**
> i wouldn't use nautilus for wallpaper, kinda un-does the lightweight aspect of fluxbox - you're almost half way to running gnome at that point.

I agree completely: there is a sort of creeping addition of features that can happen to a sparse fluxbox setup that eventually turns it from a lean mean fighting machine to a pale GNOME imitation :). On my own fluxbox setup I use thunar for file mangement and simply set the wallpaper in the [fluxbox overlay file]("http://fluxbox-wiki.org/index.php?title=Style_overlay"). Best keep it as simple as possible...

---

### Post by KFwLsKvVAs on 2012-01-24
Many thanks for the replies.  

I noticed too that the more gnome apps that I ran the clunkier things got.  I'll try feh and see if that works better.  Thanks again for the replies.

---

### Post by m_duck on 2012-01-24
You can launch Nautilus to be a file manager only with:```
nautilus --no-desktop
```
Feh can be used alone, as can Nitrogen to set the wallpaper. From memory (not used FB for a while), Fluxbox has its own wallpaper setter (which IIRC uses feh/eterm etc to actually do the wallpaper setting) called fbsetbg.

---

### Post by KFwLsKvVAs on 2012-01-24
Well I tried a number of different configurations to try to get feh to set the wallpaper, and ran into issues when using a dual monitor (bg was basically one image stretched really large, and it didn't play nice with the fluxbox right click menu).  I also tried gsetbg, as well as fbsetbg, but they work for setting a single image as a background, whereas I prefer a wallpaper that changes every once in a while.  

Also, I didn't want nautilus to launch and not draw the background, I wanted it to launch and draw the background but not overlap conky and not pop up the actual file manager.  

I came up with a sort of not-so-elegant but clever solution though.  
I found out that once the background is changed in wallch with nautilus running, you can kill nautilus and the background persists.  SO.
In my fluxbox startup script, I had nautilus and wallch both start immediately on login.  Then I had another command that slept for 10 seconds before killing nautilus (which is the same amount of time I have cairo-dock sleeping for before it starts).  So upon login, the wallpaper changes, nautilus' file browser window pops up, then 10 seconds after login killall nautilus executes, as well as cairo-dock and conky.  So basically I've got a fresh wallpaper every login, which I can deal with.  I'm learning python programming currently in my spare time, and if I can write a better wallpaper changer program that doesn't rely on nautilus to draw the desktop, believe me I'll be sharing it.

---

### Post by KFwLsKvVAs on 2012-01-24
Scratch that above post.  

I figured out I could do 

```
${execi 30 fbsetbg -r /home/bonez/Wallpapers}
```

within conky to get a new wallpaper every 30 seconds (though I don't plan to keep it to that frantic of a pace), and not have to mess around with nautilus at all.  Thanks for all the help though.

---

### Post by KFwLsKvVAs on 2012-01-25
Just thought I'd update with the final config.  

My .fluxbox/startup is as follows:
```
#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/home/bonez/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
sleep 5 && conky &
nm-applet &
sleep 10 && cairo-dock &
xscreensaver &
xscreensaver-daemon &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec fluxbox
# or if you want to keep a log:
# exec fluxbox -log "/home/bonez/.fluxbox/log"
```

and my .conkyrc is as follows:
```
### Conky Display Settings
	 
	# set to yes if you want Conky to be forked in the background
	background yes
	 
	#font
	use_xft yes
	xftfont Sans:size=8
	xftalpha 1
	 
	# Update interval in seconds
	update_interval 1.0
	 
	# This is the number of times Conky will update before quitting
	# Set to zero to run forever.
	total_run_times 0
	 
	# Create own window instead of using desktop (required in nautilus)
	own_window yes
	 
	# Use pseudo transparency with own_window?
	own_window_transparent yes
	 
	# If own_window is yes, you may use type normal, desktop or override
	own_window_type desktop
	 
	# If own_window is yes, these window manager hints may be used
	own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
	 
	# Use double buffering (reduces flicker-maybe)
	double_buffer yes
	 
	# Minimum size of text area
	minimum_size 210 200
	 
	# Maximum width of text area
	maximum_width 350
	 
	# Draw shades?
	draw_shades yes
	 
	# Draw outlines?
	draw_outline no
	 
	# Draw borders around text?
	draw_borders no
	 
	# Draw borders around graphs?
	draw_graph_borders no
	 
	# Default colors and also border colors
	default_color white
	default_shade_color black
	default_outline_color white
	 
	# Text alignment, other possible values are commented
	#alignment top_left
	#alignment top_right
	#alignment bottom_left
	#alignment bottom_right
	#alignment middle_left
	alignment middle_right
	#alignment none
	 
	# Gap between borders of screen and text
	# same thing as passing -x at command line
	#(in pixels-me thinks)
	gap_x 12
	gap_y 12
	 
	# Subtract file system buffers from used memory?
	no_buffers yes
	 
	# Should all text to be in uppercase?
	uppercase no
	 
	# number of cpu samples to average
	# set to 1 to disable averaging
	cpu_avg_samples 2
	 
	# Force UTF8? note that UTF8 support required XFT
	override_utf8_locale no
	 
	### Conky Output
	 
	TEXT
	${color 2F7CA9}
	${font sans-serif:bold:size=8}SYSTEM ${hr 2}
	${font sans-serif:normal:size=8}$sysname $kernel on $machine
	Host:$alignr$nodename
	Uptime:$alignr$uptime
	RAM:$alignr$mem/$memmax
	Swap usage:$alignr$swap/$swapmax
	Disk usage:$alignr${fs_used /}/${fs_size /}
	Total CPU usage:$alignr${cpu cpu0}%
	 
	${font sans-serif:bold:size=8}PROCESSOR ${hr 2}
	${font sans-serif:normal:size=8}${top name 1} $alignr ${top pid 1} ${top cpu 1}
	${top name 2} $alignr ${top pid 2} ${top cpu 2}
	${top name 3} $alignr ${top pid 3} ${top cpu 3}
	${top name 4} $alignr ${top pid 4} ${top cpu 4}
	${top name 5} $alignr ${top pid 5} ${top cpu 5}
	 
	${font sans-serif:bold:size=8}MEMORY ${hr 2}
	${font sans-serif:normal:size=8}${top_mem name 1}${alignr}${top mem 1} %
	${top_mem name 2}${alignr}${top mem 2} %
	$font${top_mem name 3}${alignr}${top mem 3} %
	$font${top_mem name 4}${alignr}${top mem 4} %
	$font${top_mem name 5}${alignr}${top mem 5} %
	 
	${font sans-serif:bold:size=8}NETWORK ${hr 2}
	${if_existing /proc/net/route eth1} ${font sans-serif:italic:size=8} $alignc Wireless
	${font sans-serif:normal:size=8}IP address: $alignr ${addr eth1}
	SSID: $alignr ${wireless_essid eth1}
	Speed: $alignr ${wireless_bitrate eth1}
	Connection quality: $alignr ${wireless_link_qual_perc eth1}%
	Inbound ${downspeed eth1} kb/s $alignr Total: ${totaldown eth1}
	Outbound ${upspeed eth1} kb/s $alignr Total: ${totalup eth1}
	${endif}
	${if_existing /proc/net/route eth0} ${font sans-serif:italic:size=8} $alignc Wired
	${font sans-serif:normal:size=8}IP address: $alignr ${addr eth0}
	Inbound ${downspeed eth0} kb/s $alignr Total: ${totaldown eth0}
	Outbound ${upspeed eth0} kb/s $alignr Total: ${totalup eth0}
	${endif}
	${if_existing /proc/net/route ppp0} ${font sans-serif:italic:size=8} $alignc Mobile
	${font sans-serif:normal:size=8}IP address: $alignr ${addr ppp0}
	Inbound ${downspeed ppp0} kb/s $alignr Total: ${totaldown ppp0}
	Outbound ${upspeed ppp0} kb/s $alignr Total: ${totalup ppp0}
	${endif}
${execi 400 fbsetbg -r /home/bonez/Wallpapers/New_Wallpapers}
```

I ran into an issue just using my regular path for wallpapers because I had subfolders within it, and fbsetbg would try to set one of the folders and error out.  I solved that problem with 
```
bonez@bonez-Latitude-E6400-2:~$ find /home/bonez/Wallpapers -name '*.jpg' -exec mv '{}' /home/bonez/Wallpapers/New_Wallpapers/ \;

```

And now everything's working like a charm.  Took some time and some meditation to Norwegian black metal but eventually the answer came to me.

---

### Post by hakermania on 2012-06-06
Nice :)
I just want to add that the next version of Wallch will work in many different DEs, and the only thing you will have to do is to select your DE in a new dialog which we have added to the program.

---

