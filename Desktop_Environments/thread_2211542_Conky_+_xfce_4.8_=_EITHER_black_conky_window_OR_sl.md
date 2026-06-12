---
title: "Conky + xfce 4.8 = EITHER black conky window OR slow refresh"
date: 2014-03-16
forum: Desktop Environments
---

### Post by s-p-constantine on 2014-03-16
Bizarre,

Until a few days ago, conky ran perfectly on my netbook. Then I noticed that the conky window was now black, instead of transparent.

Tweaking: Settings > Settings Manager > Window Manager Tweaks > Compositor > ENABLE display compositing  DOES fix things - I now have a transparent conky window again.

BUT, the conky text now refreshes as if it's in slow motion...

Anyone come across this - and has an idea how to fix it.

Cheers - Steven.

---

### Post by deadflowr on 2014-03-17
What's the output of everything above the TEXT line?

---

### Post by s-p-constantine on 2014-03-18
background no
update_interval 1


cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius


double_buffer yes
no_buffers yes
text_buffer_size 2048


gap_x 40
gap_y 50
minimum_size 500 200
maximum_width 800
own_window yes
own_window_class conky
own_window_type normal
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment tr


draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=9
xftalpha 0.5
uppercase no


default_color FFFFFF
color1 ffffff
color2 ffffff
color3 ffffff


lua_load ~/.conky/conky_grey.lua
lua_draw_hook_post main

---

### Post by deadflowr on 2014-03-18
You should be able to add transparency with this line
```
own_window_argb_value 255
```
you already have the other line
```
own_window_argb_visual yes
```

the 255 will give it full transparency.
You should be able to adjust that value up or down, if you want.
(0= no transparency, 255=full transparency)
I would add that new line directly above or below the one that exists.
Not necessary, but the two lines go good together.
See if that helps out.

---

### Post by s-p-constantine on 2014-03-19
@deadflowr

Thanks for this - but still no good, with any value... :-(

[[IMG]http://i1009.photobucket.com/albums/af211/__spc__/xubuntu/Screenshot-190314-180857.png[/IMG]](http://s1009.photobucket.com/user/__spc__/media/xubuntu/Screenshot-190314-180857.png.html)

---

### Post by grumblebum2 on 2014-03-20
Your pic shows compositing not enabled.
You need compositing.
Just need to work out why the slow refresh.
Run conky in terminal to check for errors.

Test some other conky configs.
You can run any config with 
```
**conky -c** [COLOR="#696969"]/path/to/config[/COLOR]
```

---

### Post by deadflowr on 2014-03-20
I'd say do what the above stated, but probably go through the list of enabled effects and slowly disable stuff, like shadowing.
Most compositors, like compiz or kwin, will make the changes immediately, so no need to restart things like X.
So you should be able to see the changes made and whether they are good or bad rather quickly, giving you a chance to revert them if bad.

---

### Post by s-p-constantine on 2014-03-21
Right, thanks for the continued suggestions.

Starting conky from the command line, with conky -c ~/.conkyrc [& own_window_argb_visual yes (not own_window_argb_value 255)] works fine!

I usually start conky from Application Autostart (control panel).... with conky -c ~/.conkyrc &

Running conky from a .sh script fixes things, and the conky refresh is a it should be.

My script is:
  #!/bin/bash
  sleep 20
  conky -c ~/.conky/conkyrc
  exit 0

Thanks again for your help!

---

### Post by grumblebum2 on 2014-03-21
There are 2 ways to set transparency
[LIST=1]
[*]**own_window_transparent yes** 
[*]**own_window_argb_visual yes** with an **own_window_argb_value**
[/LIST]


The **own_window_argb_value** has a range of 0-255
0=fully transparent 
255=fully opaque
If you set **own_window_transparent no** you can then use a degree of transparency.
eg...
```
own_window_transparent **no**
own_window_argb_visual yes
own_window_argb_value 180
```

Perhaps conky is starting before compositing kicks in.
You could also try giving conky a start delay if you only experience problems at login
**conky -p 10**
Pauses start for 10 secs.

or in your case you could use
```
conky -p 10 -c ~/.conky/conkyrc
```

---

### Post by deadflowr on 2014-03-21
> **grumblebum2 said:**
> 

The **own_window_argb_value** has a range of 0-255
0=fully transparent 
255=fully opaque
If you set **own_window_transparent no** you can then use a degree of transparency.


I'm not sure about that, as setting it to zero makes the background black for me.

Edit: Didn't see the no settings for own_window transparent.
Interesting.

---

### Post by grumblebum2 on 2014-03-21
From man conky....
> **own_window_argb_visual **
 Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. This option will not work as desired (in most cases) in conjunction with 'own_window_type override'. 

**own_window_argb_value **
 When ARGB visuals are enabled, this use this to modify the alpha value used. Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity. 

**own_window_transparent **
 Boolean, set transparency? If ARGB visual is enabled, sets background opacity to 0%.

Yeah it's a bit confusing but if you **use own_window_transparent yes** the window remains transparent no matter the **own_window_argb_value**

---

### Post by s-p-constantine on 2014-05-02
Solved (and how to mark the thread as such?)

The issue was with two instances of conky running simultaneously, overlapping each and looking like a 'laggy' refresh...:oops:

---

### Post by deadflowr on 2014-05-02
> **s-p-constantine said:**
> Solved (and how to mark the thread as such?)


Go to the top of the page right above the first post.Click on Thread Tools.
Marked as Solved is at the bottom area.

---

