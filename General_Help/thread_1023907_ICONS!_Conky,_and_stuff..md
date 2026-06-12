---
title: "ICONS! Conky, and stuff."
date: 2008-12-28
forum: General Help
---

### Post by OinkOink2 on 2008-12-28
Hi all,

I'm at last beginning to figure out Compiz, GTK, Emerald, and Metacity...I think. I have a few problems still though.
[LIST]
[*]The theme I've installed called [COLOR="Purple"]Elegant Brit[/COLOR] isn't fully implemented due to lacking the **icons**
[*]I am also having some trouble with my Conky in that there seems to be a horrible looking border around it despite the option not to draw shades in the code set to "no."
[/LIST]
Firstly, here are two screenshots of the theme I have chose from gnome-look.org - it's called [COLOR="Indigo"]Elegant Brit[/COLOR].
[LIST]
[*][Elegant Brit 1]("http://www.gnome-look.org/content/preview.php?preview=1&id=74553&file1=74553-1.jpg&file2=74553-2.jpg&file3=74553-3.jpg&name=Elegant+Brit")
[*][Elegant Brit 2]("http://www.gnome-look.org/content/preview.php?preview=1&id=75983&file1=75983-1.jpg&file2=75983-2.jpg&file3=&name=Elegant+Brit+Emerald")
[/LIST]
It's running through Emerald and definitely quite aesthetically pleasing. 

Now click on the .PNG's of my dekstop in order (screenshot- to screenshot-2). 

SCREENSHOT-0:
[LIST]
[*]Underlined in [COLOR="Red"]RED[/COLOR] is my problem areas.
[*]-The Ubuntu start icon - how do I change that?
[*]-How do I change the date and time theme to match how it is implemented in the Elegant Brit 1 & 2 (links above)
[*]Conky: You should see that I have that horrible shaded looking border, how can I get rid of that? Interestingly, when I switch from the Compiz window manager to Openbox via Compiz Fusion toolbar icon this horrible looking border disappears...nonetheless I have provided a copy of my the code from my 'conkyrc' file at the _bottom_ of this post for you to look through.
[/LIST]
SCREENSHOT-1:
[LIST]
[*]On the left are the icons I want for AWN and on the right are examples of the *Eikon* icon pack that are used with *Elegant Brit* (see link 1 & 2) which I'd like implemented as well.
[*]-How do I install icons for AWN?
[*]-How do I install icons for "everywhere else"?
[/LIST]

SCREENSHOT-2:
[LIST]
[*]How can I get Snackr to run without it appearing in my taskbar?
[/LIST]

gconf-editor_customicon:
[LIST]
[*]When you go into the configuration editor to change the start icon (I was reading a post about this being the correct method...) how exactly do you change the path or whatever - basically what do you do here, because contrary to the post I was reading around this forum somewhere it doesn't just seem like a simple click'n'set option. Please advise.
[/LIST]

Final questions:
[LIST]
[*]How do I install fonts? I want to install the font [[COLOR="Blue"]**Iwona**[/COLOR]]("http://www.gnome-look.org/content/show.php/Kurier+%26+Iwona?content=75956") but don't know where to install it to nor how that procedure goes?
[*]I attempted to replace the default VLC player skin but in the process seemed to have totally buggered it up as it will no longer LOAD UP. How can I reset the installation of VLC back to default settings?
[/LIST]

My Conky code:```


background no 
font Monospace:size=7
#xftfont Monospace:size=7
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 166 100
maximum_width 1270
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color 86A2B2
default_shade_color 002200
default_outline_color 22ee99
alignment top_left
gap_x 20
gap_y 120
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase no 

TEXT
${font Monospace:size=7}${time %A}:${alignr 1150}${time %d/%m/%y}
${font Monospace:size=13}${time %H:%M}
${font Monospace:size=7}${voffset -9}Uptime:${alignr 1150}$uptime
${font Monospace:size=4}${voffset -4}----------------------------------------
${font Monospace:size=8}${execi 5000 cal}
${font Monospace:size=4}${voffset -18}----------------------------------------
${font Monospace:size=8}Gmail: ${alignr 1150}yourmail
${font Monospace:size=7}${alignr 1150}Inbox(${texeci 180 python ~/scripts/gmail.py})
${font Monospace:size=4}${voffset -4}----------------------------------------
${font Monospace:size=7}${time %b} Total: ${alignr 1150}${execi 600 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}
${font Monospace:size=4}${voffset -4}----------------------------------------
${font Monospace:size=7}${goto 383}${voffset -160}${cpubar 4, 500}
${goto 383}${voffset -4}${cpugraph 80, 500 F0F8FA 86A2B2}${goto 383}${voffset -70} CPU:${cpu cpu1}%
${goto 383}${voffset 8} Temp:${acpitemp}C
${goto 383} Root:${fs_free /} free
${goto 383} Windows:${fs_free /media/hda1} free
${goto 383}${voffset 9} RAM:${memperc}% of $memmax
${goto 383}${voffset 2}${membar 4,500}
${goto 383}${voffset -4}${downspeedgraph eth1 40,247 D9E9EF 86A2B2}  ${goto 636}${upspeedgraph eth1 40,247 E3F8FB 86A2B2}
${goto 383}${voffset -43} down: ${downspeed eth1}.0KB/s ${goto 636} up:   ${upspeed eth1}.0KB/s
${goto 383} today:${execi 300 vnstat | grep "today" | awk '{print $2 $3}'} ${goto 636} today:${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${goto 383} month:${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'} ${goto 636} month:${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${goto 383}${voffset 5}${wireless_link_bar 4,500 eth1}
${goto 530}${voffset -147}${top name 1}${alignr 578}${top cpu 1}${alignr 573}${top mem 1}
${color B4BCBF}${goto 530}${voffset -1}${top name 2}${alignr 578}${top cpu 2}${alignr 573}${top mem 2}
${goto 530}${voffset -1}${top name 3}${alignr 578}${top cpu 3}${alignr 573}${top mem 3}
${goto 530}${voffset -1}${top name 4}${alignr 578}${top cpu 4}${alignr 573}${top mem 4}
${color CDD1D2}${goto 530}${voffset -1}${top name 5}${alignr 578}${top cpu 5}${alignr 573}${top mem 5}
${goto 530}${voffset -1}${top name 6}${alignr 578}${top cpu 6}${alignr 573}${top mem 6}
${goto 530}${voffset -1}${top name 7}${alignr 578}${top cpu 7}${alignr 573}${top mem 7}
```

---

### Post by Wartender on 2008-12-28
for the conky thing, go to compizconfig settings manager and in the window decorations plugin in the shadow windows part, type in !title=Conky ,that'll take off the shadow (you might have to turn the decorations off and then on again for it to work)

---

### Post by Wartender on 2008-12-28
to change the ubuntu icon, go to your .icons directory, and in 128x128 (probably, maybe other size) in the places folder, replace the start-here.png icon with whatever icon you want

---

### Post by Wartender on 2008-12-28
i'm not sure asbout installing icons for AWN, i usually right-click something on the dock and select "change icon" and select an icon from my .icons directory (btw to get there you go to your home and press ctrl+h to see hidden folders and .icons is there.)to change icons for everything else dowanload a tarball icon theme and drag it onto the appearances window (system->preferences->appearance) and it'll install it for you
edit: that's all i know how to anser for now, for the not showing in the taskbar thing if there's any configuration files or anything an option that is something like "skip taskbar" or similar should be enabled, but i'm not sure where since i don't have snacker. sorry for being to lazy to include everything in a single post.

---

### Post by OinkOink2 on 2008-12-28
> **Wartender said:**
> to change the ubuntu icon, go to your .icons directory, and in 128x128 (probably, maybe other size) in the places folder, replace the start-here.png icon with whatever icon you want

Well I've put it there, and reloaded the window but it hasn't worked. So frustrating! You'd think that just dropping the tarball of the theme you want to install would do all of this for you - it seems nonsensical that it doesn't!

> **Wartender said:**
> i'm not sure asbout installing icons for AWN, i usually right-click something on the dock and select "change icon" and select an icon from my .icons directory (btw to get there you go to your home and press ctrl+h to see hidden folders and .icons is there.)to change icons for everything else dowanload a tarball icon theme and drag it onto the appearances window (system->preferences->appearance) and it'll install it for you
edit: that's all i know how to anser for now, for the not showing in the taskbar thing if there's any configuration files or anything an option that is something like "skip taskbar" or similar should be enabled, but i'm not sure where since i don't have snacker. sorry for being to lazy to include everything in a single post.

When I attempted to drag and drop my icon tarball (".tar.gz", yes?) over the 'Theme' tab of the Appearance window I get an alert saying that the installation failed and that it isn't possible to **"move directory over directory."**

.......ARGH!

Please advise.

---

### Post by OinkOink2 on 2008-12-28
> **Wartender said:**
> for the conky thing, go to compizconfig settings manager and in the window decorations plugin in the shadow windows part, type in !title=Conky ,that'll take off the shadow (you might have to turn the decorations off and then on again for it to work)

What you meant was "!(class=Conky)" ?

This worked. Cheers.

Another thing I can't fathom is under Applications > Add/remove, when that loads up, i get the loadbar with "checking for installed applications" or whatever it says, but after NOTHING shows up. It just says **"There is no matching application."** Synaptic still works and I can add/remove applications from there but the point is that this used to display all my installed applications much simpler. Now - nothing?

---

### Post by Wartender on 2008-12-28
well ok. for the icon... did you install it in the folder of the theme you are using? if you did try going to appearance and clicking customize and in the icons tab click another icon theme (any of them works) and then click the one you were using, see if the icon you put loads, if not try moving it into a folder of another size (e.x. 16x16) remember that if you put it into the folder and it didn't say anything, it's the wrong folder, you have to replace and icon that was already there (the one in use) for it to work. 
next, if dragging it onto appearance didn't work (and yes .tar.gz=tarball) extract the folder into your .icons directory, then select the icon theme from appearance.
next, well if class=conky works for you, great, for some reason title=conky works for me so whatever.
and finally make sure there is nothing in the search bar. if there's nothing try hitting reload
edit: oh and in the search bar make sure it says "all open source applications"... or "all available applications"... or something... that's probably not it anyways.

---

### Post by OinkOink2 on 2008-12-28
Cheers, I have the icons sorted now.

Alas, the problem with Add/remove applications is still there.

I tried changing the skin of my VLC at some point yesterday as well and now it wont load up. I click VLC and a box loads at the top right of my screen headed "error". Then I'm asked to open a VLC skin file. I pointed to the default .vlt but this doesn't work. Pretty strange. Maybe I corrupted something.... 

I tried reinstalling VLC thru Synaptic but it hasn't worked. Maybe I should try uninstalling it and then reinstalling it however if you've any ideas about a faster solution...?

---

### Post by Wartender on 2008-12-28
i;m sure that solution is pretty fast ( irecommend marking it for complete removal if you do that) perhaps you could edit something in your vlcrc (home/.vlc/vlcrc) i'm pretty sure reinstalling would be the fastest thing to do though.

---

### Post by OinkOink2 on 2008-12-29
VLC doesn't have a folder in my home folder! (?)

I've also tried complete removal and then reinstalled it and I still get the same problem. Please see the screenshot of the errors returned upon attempting to run from command line.

---

### Post by levelup3 on 2008-12-30
is really useful for me, I am glad to read it here.

---

### Post by OinkOink2 on 2008-12-30
Levelup3, I'm happy that you found some solutions to any issues you had in my thread. It was frustrating but I think many of the problems came from myself not knowing the way files and directories are organised, and just the general difference of Linux from Windows.

Some pointers I'd like to share with you - check out:[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1024171](http://ubuntuforums.org/showthread.php?t=1024171)
[*][http://ubuntuforums.org/showthread.php?t=1025065](http://ubuntuforums.org/showthread.php?t=1025065)
[*][http://ubuntuforums.org/showthread.php?t=1024916](http://ubuntuforums.org/showthread.php?t=1024916)
[/LIST]

All are issues I've encountered recently and solved them through there.

The one issue I haven't solved yet is that my 'Add/Remove Applications' feature [COLOR="Red"]**_ALWAYS_**[/COLOR] shows no applications installed on my system and does _NOT_ operate the way it did on my default installation of ubuntu. Please see the screenshot to see what I'm talking about.

Anyone have any ideas on how to rectify that - I've asked plenty of times since being on the forum but unfortunately no one has had a proper solution.

Could it be anything to do with my sources.lst file? I dunno how these things operate yet. But Synaptics works fine...

Lastly, does anyone know how I can change the date and time theme to reflect that shown in the [COLOR="Purple"]Elegant Brit[/COLOR] screenshot from [COLOR="Blue"][gnome-look.org]("http://www.gnome-look.org/content/preview.php?preview=1&id=74553&file1=74553-1.jpg&file2=74553-2.jpg&file3=74553-3.jpg&name=Elegant+Brit")[/COLOR].

?

Cheers

---

### Post by jipke on 2008-12-31
> **OinkOink2 said:**
> Lastly, does anyone know how I can change the date and time theme to reflect that shown in the [COLOR="Purple"]Elegant Brit[/COLOR] screenshot from [COLOR="Blue"][gnome-look.org]("http://www.gnome-look.org/content/preview.php?preview=1&id=74553&file1=74553-1.jpg&file2=74553-2.jpg&file3=74553-3.jpg&name=Elegant+Brit")[/COLOR].

?

Cheers

I could be mistaken, but I think that's XFCE running. You can't change the date and color that way in GNOME.

---

### Post by Denestria on 2008-12-31
Look for the vlc configuration file in .config/vlc/vlcrc
The line for the theme starts with **skins2-last**.  You can try commenting it out or just delete the config and start over.

---

