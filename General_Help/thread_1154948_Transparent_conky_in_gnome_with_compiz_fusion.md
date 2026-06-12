---
title: "Transparent conky in gnome with compiz fusion"
date: 2009-05-10
forum: General Help
---

### Post by paul555 on 2009-05-10
Hi all as the title says i want to make conky window transparent in gnome using compiz fusion.I have read some threads(like going in compizconfig manager in general options and in opacity settings tab but i didn't find it) but i didn't managed to achieve it.Does anyone have any suggestions?

---

### Post by gamblor01 on 2009-05-10
You can't control the way conky behaves by editing the options in compiz (especially if you make it windowless).  Conky is controlled by the ~/.conkyrc file, and you need to define options in there which tell conky to use a transparent window, with no borders, etc.  Here are the options in my .conkyrc file (the rest of the file is just defining what text and graphs show up on it):

> 
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
You probably want to pay particular attention to these options.  Try copying them in your .conkyrc file and then change options from "no" to "yes" to see how it affects your conky display:

> 
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
And here's what it looks like:

[http://slackbox.homelinux.org/may-desktop.png](http://slackbox.homelinux.org/may-desktop.png)

---

### Post by VCoolio on 2009-05-10
Some things you do need to set in compiz. E.g. a transparant window can still have shadows. In that case in compiz settings manager, window decoration plugin add to window shadows entry: any & !(class=conky)
Also when you do ctrl+d or click the show desktop button conky may disappear along with the other windows. In that case in compiz settings manager, general options uncheck the box at Hide Skip Taskbar Windows.

EDIT: I didn't want to bump this thread but the post below suggests specifying conky by class in compiz and then you need Conky with capital C, so: class=Conky.

---

### Post by devildoc5 on 2009-06-20
Ok I think there is some major confusion going on here as to what the deal is and what this guy is looking for. 

I for example set my window settings like so:

own_window yes
own_window_colour neon green with pink and purple polka dots and red blood
own_window_type normal
own_window_transparent no

The important part is to make sure that you keep the type as normal DO NOT put it on over ride or my trick will not work.

Now go into Compiz (the new compiz has it under an "Opacity, Brightness and saturation" tab on the main menu, click on this.

Now you need to go to the very bottom to "window specific settings" and click "new".  Now in the text box labeled "windows" type in: "name=conky" without the quotes or "class=conky" either one will work.  Now move the slider to your desired opacity setting and there you have it...

SEMI Transparent conky with the help of Compiz.

---

