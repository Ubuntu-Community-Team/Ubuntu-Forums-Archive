---
title: "Conky works but terminal shows errors"
date: 2017-11-26
forum: Desktop Environments
---

### Post by forneus2 on 2017-11-26
I want to keep my conky display minimal. Showing only the info I need. This is how I edited the config file:

[https://i.imgur.com/pO48bbO.png](https://i.imgur.com/pO48bbO.png)

And this is what's displayed when I start it in the terminal:

[https://i.imgur.com/P5dWzjql.png](https://i.imgur.com/P5dWzjql.png)

What is the "invalid setting of type number"? What did I edit wrong? It works, but apparently something is not right.

---

### Post by ajgreeny on 2017-11-26
Please copy the text of your .conkyrc or whatever config file you use, and the errors you see in terminal back here rather those screenshots which are unreadable to me.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by forneus2 on 2017-11-26
```
conky.config = {
    alignment = 'top_right',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,
    draw_graph_borders = false,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'Ubuntu:size=11',
    gap_x = 20,
    gap_y = 20,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'normal',
    own_window_hints = 'below','sticky','skip_taskbar','skip_pager',
    own_window_transparent = true,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false
}

conky.text = [[
${color grey}CPU:$color $cpu%
${color grey}RAM:$color $mem
${color grey}swap:$color $swap
]]

```

```
user@edge:~$ conky
conky: desktop window (160012f) is subwindow of root window (c8)
conky: window type - normal
conky: drawing to created window (0x3000001)
conky: invalid setting of type 'number'
conky: invalid setting of type 'number'
conky: invalid setting of type 'number'

```

---

### Post by ajgreeny on 2017-11-26
Edit your lines about the window type to read
```
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    own_window_transparent = true,
```
That will do it, assuming you want the conky display to be transparent and with no window decorations (titlebar and window borders, etc) showing.

It showed the conky display on my machine when I ran it with your code, but showed the same warnings in terminal; my edit made it run fine with no warnings.

---

### Post by forneus2 on 2017-11-26
> **ajgreeny said:**
> Edit your lines about the window type to read
```
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    own_window_transparent = true,
```
That will do it, assuming you want the conky display to be transparent and with no window decorations (titlebar and window borders, etc) showing.

It showed the conky display on my machine when I ran it with your code, but showed the same warnings in terminal; my edit made it run fine with no warnings.

ajgreeny, changing type to desktop causes another unpleasant effect - clicking anywhere on the screen outside of conky area makes it(conky area) disappear. I had it as desktop initially, ran into this problem, googled it, found couple of similar discussions on the issue - and the suggestion that users gave was changing type either to dock or to normal. Dock type messed up my desktop icons, so I chose normal. Im fine with it being decorated, it's just these terminal warnings...

---

### Post by again? on 2017-11-26
The main problem is this line in your original config:
```
own_window_hints = 'below','sticky','skip_taskbar','skip_pager',
```
You were quoting each individual hint, where as shown by ajgreeny, you quote as a block.
ie
```
own_window_hints = 'below,sticky,skip_taskbar,skip_pager',
```

Use the following(may as well make it undecorated):
```
own_window_type = 'normal',
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
```
What you use for "own_window_type" depends on your window manager.
In Unity/compiz I used "normal".
In gnome-shell "desktop" works best.

From "man conky"
> **own_window_type**
if own_window is yes, you may specify type normal, desktop, dock, panel or override (default: normal). 
Desktop windows are special windows that have no window decorations; are always visible on your desktop; 
do not appear in your pager or taskbar; and are sticky across all workspaces. 
Panel windows reserve space along a desktop edge, just like panels and taskbars, preventing maximized windows from overlapping them. 
The edge is chosen based on the alignment option. Override windows are not under the control of the window manager. Hints are ignored. 
This type of window can be useful for certain situations.

**own_window_hints** undecorated,below,above,sticky,skip_taskbar,skip_pager
If own_window is yes, you may use these window manager hints to affect the way Conky displays. 
Notes: Use own_window_type desktop as another way to implement many of these hints implicitly. 
If you use own_window_type override, window manager hints have no meaning and are ignored.




You should also add to your config the following setting to eliminate flickering.
```
double_buffer = true,
```

***Note the bottom section of your config.
```
    show_graph_range = false
}

conky.text = [[
${color grey}CPU:$color $cpu%
${color grey}RAM:$color $mem
${color grey}swap:$color $swap
]]

```

If you add a setting to the end of the conky.config section make sure to add a comma to the preceding line.
eg
```
    show_graph_range = false[COLOR="#FF0000"],[/COLOR]
    double_buffer = true,
}

conky.text = [[
${color grey}CPU:$color $cpu%
${color grey}RAM:$color $mem
${color grey}swap:$color $swap
]]

```

---

### Post by forneus2 on 2017-11-27
> **guber2 said:**
> The main problem is this line in your original config:
```
own_window_hints = 'below','sticky','skip_taskbar','skip_pager',
```
You were quoting each individual hint, where as shown by ajgreeny, you quote as a block.
ie
```
own_window_hints = 'below,sticky,skip_taskbar,skip_pager',
```

Use the following(may as well make it undecorated):
```
own_window_type = 'normal',
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
```
What you use for "own_window_type" depends on your window manager.
In Unity/compiz I used "normal".
In gnome-shell "desktop" works best.

From "man conky"




You should also add to your config the following setting to eliminate flickering.
```
double_buffer = true,
```

***Note the bottom section of your config.
```
    show_graph_range = false
}

conky.text = [[
${color grey}CPU:$color $cpu%
${color grey}RAM:$color $mem
${color grey}swap:$color $swap
]]

```

If you add a setting to the end of the conky.config section make sure to add a comma to the preceding line.
eg
```
    show_graph_range = false[COLOR=#FF0000],[/COLOR]
    double_buffer = true,
}

conky.text = [[
${color grey}CPU:$color $cpu%
${color grey}RAM:$color $mem
${color grey}swap:$color $swap
]]

```

The error warnings are gone. Conky looks great. Thanks for the tips, guber2!

---

