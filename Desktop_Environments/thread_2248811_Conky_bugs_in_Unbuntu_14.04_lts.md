---
title: "Conky bugs in Unbuntu 14.04 lts"
date: 2014-10-17
forum: Desktop Environments
---

### Post by Eric_Hsing on 2014-10-17
After I installed Conky for trusty and launched it with the config below,

```
# Conky Metro Clock - http://fav.me/d424h9d

# Conky settings
background no
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048

# Window specifications
own_window yes
own_window_class conky
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

alignment bl
gap_x 1200
gap_y 100

# Graphics settings
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings
use_xft yes
xftalpha 0
text_buffer_size 2048

uppercase no

default_color FFFFFF

TEXT
${voffset 10}${font Open Sans Light:size=50}${time %A}${font}${voffset -10}
${voffset 10}${font Open Sans Light:size=50}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Open Sans Light:size=100}${time %I:%M %p}${font}${voffset -10}
```

everything works well until I switch to the desktop with Alt+tab and clicked on it. Conky disappears!!!!
The problem were discussed many times if you check with Google, but all the possible solutions seem to fail.
It is generally suggested that adjusting the parameter of own_window_type may fix the problem, let's see,
however, what will happen if we apply other parameters like normal/override.

```
own_window_type normal
```
Conky disappears (minimizes) right after I switch to the desktop by Alt+Tab.

```
own_window_type override
```
Conky won't hide or minimize in any case, but something more fishy happens:
after refresh the new gragh will overlap directly on the previous one. What a mess.
[IMG]http://i.imgur.com/B9oQcyf.png[/IMG]


Does anyone here encounter the same problem?? Or is there already an ultimate solution for that?
I'm so frustrated, will be grateful for any help!!!

---

### Post by Frogs Hair on 2014-10-17
I had to tweak the window type which was originally desktop. ```
 own_window_type panel  #[COLOR=#00ff00] [/COLOR][COLOR=#0000ff]other options are: override/dock/desktop/panel/conky[/COLOR][COLOR=#00ff00][/COLOR]
```

---

### Post by CantankRus on 2014-10-18
The least problematic with compiz/unity is
```
own_window_type normal
```
and to stop conky hiding when you show the desktop, in the terminal run....
```
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hide-skip-taskbar-windows false
```

If you find conky draws an unwanted shadow as in 2nd pic, run...
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ inactive-shadow-color '#00000000'
```

These settings can also be changed using the compizconfig-settings-manager (ccsm) GUI.

---

### Post by peterfmutch on 2015-01-08
I was able to fix this by setting own_window_type normal, commenting out own_window_type transparent, and uncommenting own_window_type_argb_visual and own_window_argb_value 0.

Hope this helps!

---

