---
title: "Conky Loading Issue"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by tshearman on 2008-02-25
Hey everyone,  I just installed conky, and love what it can be! haha

Currently I'm just using someone else's sample.  I haven't edited to because i cant get any elses examples to work properly yet.

Basically, my issue is that when I log in, and conky auto-starts, it looks like the ss.
It's always on top of everything, no way to move it etc...

If it killall and start it manually, then it moves to the correct position, below and everything is beautiful.

Anyone seen this before?  Know a fix?
Thanks so much! And, I cant wait to get this working properly

---

### Post by uberlube on 2008-02-25
you can tell it where to launch to by pressing alt+F2 and typing in:

conky -a top_left

or whatever.

---

### Post by tshearman on 2008-02-25
Whoops... my conkyrc came from this website:
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html#more-89]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html#more-89")

---

### Post by tshearman on 2008-02-25
Well, the ideal case is that when I login, it's in the right place, and I don't have to do anything to it... know what i mean?

---

### Post by uberlube on 2008-02-25
Did you get it to work the way you want it? Also, if you are auto launching conky make sure you specify the alignment in sessions.

---

### Post by tshearman on 2008-02-25
So, i just added the '-a top_left' and it shifted it to the proper location... however it still loads in front of everything.  And, i cant access anything behind it.

---

### Post by uberlube on 2008-02-25
> -a ALIGNMENT
    Text alignment on screen, {top,bottom}_{left,right} or none


That is from the manual, so try different ways of doing it so it is not over your panels. Or if your question is about using icons underneath it, you wont be able to.

---

### Post by tshearman on 2008-02-25
WAIT... thought it worked
Just it just jumped to the front again... blah - this thing
I'm gonna tinker some more.  If you have ideas-they are welcomed

[INDENT]
I think i got it... had to add 

```
-own_window_hints below
```

to the sessions command line.  Before it was above all my windows, including firefox and anything (not just icons).  Thanks for the help.  I wouldnt have thought to add anything to the sessions command line.[/INDENT]

---

### Post by uberlube on 2008-02-25
Hey no prob and feel free to click the ribbon with the star :) Heres mine:
```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

# Update interval in seconds
update_interval 1.0

TEXT
${color blue}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

${color blue}CPU ${hr 1}${color}
${freq} MHz
Load: ${loadavg}   ${alignr}Temp: ${acpitemp}
$cpubar
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color blue}FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
Windows: ${alignr}${fs_used /media/sda3} / ${fs_size /media/sda3}
${fs_bar 4 /}


${color blue}NETWORK ${addr eth0} ${hr 1}$color

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 000000 ff0000} ${alignr}${upspeedgraph eth0 25,107 000000 ff0000}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color blue}AMAROK ${hr 1}$color

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conkyamarok artist}
${alignc}${execi 10 ~/.conkyamarok title}
${execibar 1 ~/.conkyamarok progress}
${alignc}"${execi 10 ~/.conkyamarok album}"
${alignc}${execi 10 ~/.conkyamarok year} - ${color white}${alignc}${execi 10 ~/.conkyamarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conkyamarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conkyamarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conkyamarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conkyamarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conkyamarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conkyamarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conkyamarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conkyamarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conkyamarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conkyamarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conkyamarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conkyamarok most_albums_during_year_n}${color})$endif

${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}


```

---

### Post by tshearman on 2008-02-25
Looks like this may have been the culprit.

```
own_window_type normal
```

Mine was set to 'override' - we'll see if it lasts haha.
thanks again

---

### Post by kainos on 2008-02-25
> **tshearman said:**
> Looks like this may have been the culprit.

```
own_window_type normal
```

Mine was set to 'override' - we'll see if it lasts haha.
thanks again

That worked for me. Thanks!

---

