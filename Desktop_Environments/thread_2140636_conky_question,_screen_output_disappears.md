---
title: "conky question, screen output disappears"
date: 2013-04-30
forum: Desktop Environments
---

### Post by emueyes on 2013-04-30
I hope it's OK to ask a question about conky here, there seem to be a few already. I have a couple of scripts set up and working nicely, but have a persistent problem. Clicking on the backdrop makes the conky output disappear. I've tried various suggestions, most commonly leading to no output at all on the screen. I want to have the output on the backdrop, behind any windows ie appearing as part of the backdrop, with no borders are any other decoration that I don't draw myself. The setup is the same for each script 

```


alignment top_right
background no
border_width 0


minimum_size 300 170


color1 FFFFFF
color2 DAA520


own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
imlib_cache_size 0


default_color white


draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftalpha 0.5


xftfont Ubuntu Light


double_buffer yes
out_to_console no
out_to_stderr no
extra_newline no
stippled_borders 0
update_interval 5.0
uppercase no
use_spacer none



```

I removed a lot of commented attempts at fixing this. I imagine the problem is with the 'window' type statements, but as I mentioned, changing things here just leads to no output at all. I'd be really grateful if someone could give me a point in the right direction.

---

### Post by stinkeye on 2013-04-30
Replace
```
own_window_type desktop
```
with
```
own_window_type normal
``` 
and add
```
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```

If you're using compiz, you may want to exclude conky windows from having a shadow drawn by compiz if you don't like the effect.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2076882&p=12584657&viewfull=1#post12584657")

---

### Post by emueyes on 2013-04-30
Mate that works perfectly! Thank you so much for your help. The images stay put, as part of the backdrop it seems, exactly what I wanted. I thought I'd show the images, they're on flickr so I guess should work

[IMG]http://www.flickr.com/photos/emueyes/8695908517/in/photostream[/IMG] [IMG]http://www.flickr.com/photos/emueyes/8695909837/in/photostream[/IMG]

Not that grand or complex, I guess, but now they work properly. Thanks again :)

---

