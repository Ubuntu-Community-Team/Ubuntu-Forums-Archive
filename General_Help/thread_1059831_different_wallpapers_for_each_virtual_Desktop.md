---
title: "different wallpapers for each virtual Desktop"
date: 2009-02-04
forum: General Help
---

### Post by swpark on 2009-02-04
> **loomsen said:**
> Thanks for contributing everyone.

Guess it's time to give some back...

Here we go:

**How to set up different wallpapers for each virtual Desktop, still using conky, and gettin rid of gnome panels?**

First we gotta get rid of nautilus.

[COLOR="Red"]NOTE: You will lose your Desktop icons![/COLOR]

Which is actually a good news for me, I like it clean :) But you should consider for yourself whether you wanna live without it. If not, you basically should stop reading now, and activate the next tab in your favorite webbrowser.

Alright, lets go. 

First step is to enable and configure the wallpaper plugin in CCSM.
Open it up by hitting 

Alt + F2 (optional Super + Space if you have gnome do installed)
and type ccsm
navigate to utility, wallpaper. There, set up the wallpapers according to your needs.

[COLOR="#ff0000"]Note:[/COLOR] the order you specify here will be the order on your desktops.
So the first wallpaper will be drawn to your first desktop, the second one to desktop nr2 and so on.

Set up one for each desk, I got 4. U may also set up more than the number of your desks, but it wont have any effect.

Alright, now enable the plugin. If you are using Ubuntu, which obv most of us are, you wont notice any change yet. Still the same on every Desktop.

This is because nautilus, the default file manager shipped with gnome, draws our Desktop, as well as the icons lying on it and the right klick context. But don't worry, we'll be rid of it soon.

[COLOR="#ff0000"]Note:[/COLOR]You may as well find it useful taking a shot at some other file manager applications.
I like 
PCManFM 
the most. It completely replaced my nautilus, which, I'm sure saved me at least as much time as this post will take me to finish :) Ridiculously fast compared to nautilus. force --back-to-topic

Alright, so we enabled our prefered wallpapers, and they are actually there, but nautilus covers them.
I could describe it by using the gconf editor and the command line a lot, but I prefer 
gTweakUI - Nautilus
which does basically the same we would do by typing lines and lines of code.
It is available through the universe repos, open up a terminal and copy&paste this:
[/code]
sudo apt-get update
sudo apt-get install gtweakui [/code] 
[COLOR="Red"]Note:[/COLOR] You may want to use a prefix to install it into a given directory, up to you.

I prefer preventing nautilus from starting up at all, you may specify this however you like it through System --> Preferences --> Sessions. Tho gtweakui will be fine, if u wanna still use nautilus for file management purpose. However, if you decide to go with some other app, you should remove it from your startup now. Open up a terminal and do this:
```
 
cd ~/.config/autostart/
ls

```
As it is the first thing I did after I installed Hardy, I dont know what it is called, should be sth according to nautilus.desktop.
Taken it is actually called nautilus.desktop, which I cant guarantee, u may edit it by typing:
```

gedit nautilus.desktop
```
search line
```

X-GNOME-Autostart-enabled=true
```
and change it to
```
X-GNOME-Autostart-enabled=false
```
Save, and exit.

Now fire up gtweakui by typing:
```
gtweakui-nautilus
``` 
into your favorite terminal application.

Uncheck:
[ ] Use nautilus to draw desktop, close gtweakui, and hit 
Ctrl + Alt + Backspace

to restart your X-Session.
[COLOR="#ff0000"]This will not remove your nautilus! If you wanna get rid of it you gotta take further actions[/COLOR]

But it's enough for now, after logging back in, we should have that mission accomplished, and each of our desks should have his own wp now.

Next step is to get rid of your gnome panel if you want to. Many here using AWN as I saw, so have I been for a while. I switched to KiBa tho in the meanwhile. It is very customizable, and once set up, which can easily be done by modifying a .xml file, as stable as AWN. 
BUT: you may use more than one instance of it, unlike AWN. This was the main issue for me to take a shot at KiBa, and I dont regret anything :)

Alright, but configuring your desktops to fit your need should be up to every single one of you. If someone is interested in a HowTo I might set it up tomorrow or so, but now I'd like to continue with conky.

If you use it, you already might have noticed its fake transparency. And as this is due to the source code, theres nothing we could easily tweak about it, except of porting it to another language or recoding it or sth.

But as all of us are using Compiz anyway I guess, lets actually make use of it. Setting the 
own_window_transparency to "yes" wont work in this case, just because conky isn't, and actually never was transparent. It took a shot of the frame it was told to draw to, and used it as its background.

So we gotta go for a workaround, which should melt conky into our desktops, even if its not fully transparent. As I said, I like my Desktops clean, so I wrote a conky, which displays all my desired Information in just one line on top of my screen. Take a look at the screenshots... 

This way you should be able to set your conkys up as you like, if u prefer a lot of bars and colors and stuff. (Please ask google for further information of conky, if you need some, there are a lot of HowTos available all over the net)

However, your conky options should look like this:
```

own_window yes
own_window_hints undecorated  #,sticky,below,skip_taskbar,skip_pager
own_window_type normal
own_window_transparent no
background black

```

As you may notice I commented out the window_hints in my conky, and also specified to draw a background. I've chosen a black one, u may specify it to fit to your desks however you like.

Anyway, once you set up your conky, open up CCSM once again, and go to 
Window Management --> Window rules.

Mine looks like this:
[[img=http://img523.imageshack.us/img523/503/conkygrabpw0.th.png]](http://img523.imageshack.us/my.php?image=conkygrabpw0.png)
You may type it in or use the green plus to open the little helper u might notice.

However, again, set it up to fit your needs.

Last thing to do to make conky suitable is setting some transparency.

[COLOR="Red"]NOTE: Linux is case sensitive![/COLOR]
So if you type "conky" instead of "Conky" exactly nothing will change.

Alright then, once done, hit back, and navigate 
to general options, still in CCSM.

The last tab is called Opacity Settings, activate it, click on window opacities to drop it down if it isn't open yet, and hit new.

Once again enter class=Conky and consider how opaque you would like your conky to be. Sth in between 33%-66% should be finde, just toy around, it is actually applied instantly. 

Alright, I guess thats about it, some shots how this could look like once you are finished attached.

I hope you have been able to follow, I'm german, and as the shots reveal, it's pretty l8 over here by now :) However, enjoy :)

Oh, btw, my Conky:
```

use_xft yes
xftfont Sans:size=8
alignment top_right
xftalpha 0.8
update_interval 3.0
own_window yes
own_window_hints undecorated  #,sticky,below,skip_taskbar,skip_pager
own_window_type normal
own_window_transparent no
background black
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 0
border_margin 0
border_width 1
default_shade_color black
default_outline_color white
default_color white 
override_utf8_locale yes
# Minimum size of text area
minimum_size 1440 2
maximum_width 1440

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 1


use_spacer none
uppercase no
# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

TEXT
Core1${goto 40} ${cpu cpu1}%${goto 78}${hwmon 0 temp 1}°C |Core2${goto 171} ${cpu cpu2}%${goto 209}${hwmon 1 temp 1}°C |GPU   ${execi 30 nvclock -T | perl -ne 'print $1 if /temperature.*?: (\d+)./;'}°C |HDD: ${execi 30 hddtemp /dev/sda  | perl -ne 'print $1 if /250JI.*?: (\d+)./;'}°C   ${color red}|${color} Proc: $running_processes | $memperc% RAM used   ${color red}|${color} /root: ${fs_free_perc /}% | /home: ${fs_free_perc /home}% | /sto: ${if_mounted /media/DRIVE-N-GO}${fs_free_perc /media/DRIVE-N-GO}%${else}${color dark grey}absent${color}${endif}   ${color red}|${color} ${color dark grey}${texeci 300 perl ~/configs/conk/conky_scripts/check_gmail.sh n}${color} new @ gmail     $alignr${nodename} ${color red}|${color} ${kernel}-${sysname}-${machine} ${color red}|${color} ${time %A %d %B}${font OpenLogos}${color red}u${font}${color}    
```

And another one covering two lines, same options as above
```

TEXT
 Core1${goto 55} ${cpu cpu2}%${goto 84} ${hwmon 0 temp 1}°C${goto 126}${color red}||${color} GPU   ${execi 30 nvclock -T | perl -ne 'print $1 if /temperature.*?: (\d+)./;'}°C ${color red}|${color} mem   $memperc% | @: ${texeci 300 perl ~/configs/conk/conky_scripts/check_gmail.sh n} new${alignr 520}${color green}${downspeed eth0} Kb/s${color}${alignr 480}${color red}${upspeed eth0}Kb/s${color}    $alignr${nodename} ${color red}|${color} ${kernel}-${sysname}-${machine} ${color red}|${color} ${time %A %d %B}${font OpenLogos}${color red}u${font}${color}    
 Core2${goto 55} ${cpu cpu1}%${goto 84} ${hwmon 1 temp 1}°C${goto 126}${color red}||${color} hdd:  ${execi 30 hddtemp /dev/sda  | perl -ne 'print $1 if /250JI.*?: (\d+)./;'}°C ${color red}|${color} /root:  ${fs_free_perc /}% | /home:  ${fs_free_perc /home}% | /sto:  ${if_mounted /media/DRIVE-N-GO}${fs_free_perc /media/DRIVE-N-GO}%${else}absent ${endif} ${alignr 515}${color green}${totaldown eth0}${color}${alignr 490}${color red} ${totalup eth0}${color}  $alignr${execi 600 cat ~/.metar-status}  
```

Aight, enjoy.

L8rs.

How to enable the wallpaper? I couldn't find the wallpaper in Utility at CCSM.:(

---

### Post by overdrank on 2009-02-04
Hi and welcome, swpark The Great Desktop Effects FAQ of 2009 is not for support questions so I have move your post to its own thread. Good luck :)

---

