---
title: "Use Conky as Panel Replacement/Always on Top of Windows"
date: 2018-02-19
forum: Desktop Environments
---

### Post by jakfish on 2018-02-19
My goal is to have conky act as a Linux substitute for Serious Samurize. In MS Windows, Samurize will run itself across a maximized window, inside its title bar. So far, I can not effect this in Mate 18.3 (or Xubuntu 16.04). This is my conky script (which produces only weather at this point), and I run it alongside a Mate panel. The conky stays visible always, except when a window is maximized.

Is there a way to set conky at the top right screen, visible on any window, which would allow me to delete all other panels in any given Linux:

conky.config = {
    alignment = 'top_right',
    background = true,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'Robo Black:style=Bold:size=11',
    gap_x = 0,
    gap_y = 8,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    own_window = yes,
    own_window_class = 'Conky',
    own_window_type = 'override',
    own_window_transparent = true,
    own_window_hints = 'undecorated,below,skip_taskbar,sticky,skip_pager',
    own_window_transparent = true,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false
}


conky.text = [[
${color web maroon}${execi 300 /home/jake/Scripts_Icons/weather 20902}
]]

Thanks for any advice,
Jake

---

### Post by again? on 2018-02-20
Make use of the conky manual pages...
```
man conky
```
or for large manual pages I prefer an online version for easier searching...
[http://manpages.ubuntu.com/manpages/xenial/en/man1/conky.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/conky.1.html)

The key settings here are....
>  **own_window_type**
              if  own_window  is  yes,  you  may specify type normal, desktop,
              dock, panel or override (default: normal).  Desktop windows  are
              special  windows  that  have  no  window decorations; are always
              visible on your desktop; do not appear in your pager or taskbar;
              and  are  sticky  across  all  workspaces. Panel windows reserve
              space along a desktop  edge,  just  like  panels  and  taskbars,
              preventing  maximized windows from overlapping them. The edge is
              chosen based on the alignment option. [COLOR="#FF0000"]Override windows  are  not
              under the control of the window manager. Hints are ignored.[/COLOR] This
              type of window can be useful for certain situations.

**own_window_hints** undecorated,below,above,sticky,skip_taskbar,skip_pager
              If  own_window is yes, you may use these window manager hints to
              affect  the  way  Conky  displays.  Notes:  Use  own_window_type
              desktop  as  another  way  to  implement  many  of  these  hints
              implicitly. If you use own_window_type override, window  manager
              hints have no meaning and are ignored.


You are using **own_window_type = 'override',** which ignores **own_window_hints** so you cannot set the conky window "above".
If you use **own_window_type = 'normal',** you can set it above 
eg
```
own_window_type = 'normal',
own_window_hints = 'undecorated,above,skip_taskbar,sticky,skip_pager',
```

Alternatively you could reserve screen area by using 
```
own_window_type = 'panel',
```

How the conky window behaves can also depend on the window manager.

---

### Post by vasa1 on 2018-02-20
> **guber2 said:**
> ... How the conky window behaves can also depends on the window manager.
+1. I use the window manager to keep the conky window always on top.

---

### Post by jakfish on 2018-02-21
I very much appreciate the both of you weighing in. I had played with 'panel,' 'normal,' and other settings, including 'hints,' and 'override' was the most effective in keeping conky visible when returning to the desktop. But no setting worked for maximized windows.

So through conky itself, there appears to be no way to run its output across the titlebar of a maximized window.

Here is what I'd like to have:

[https://imgur.com/a/IMfBZ](https://imgur.com/a/IMfBZ)

That's Serious Samurize in Win10.

As for effecting this through a windows manager, I don't see a handle to jiggle in Linux Mate's Marco or the WM of Xubuntu 16.04. Could you point me in the right direction?

Again, I was very glad to see your responses.

Jake

---

### Post by again? on 2018-02-21
You won't find an option to show conky in the titlebar.

---

### Post by vasa1 on 2018-02-21
Mine is a weird set-up which no one else uses but my conky covers part of the title bar in a maximized window. This is in Kubuntu 16.04 and I set conky to be always on top using KWin's rules.

---

### Post by jakfish on 2018-02-21
@vasa1--that's as close to success as I've ever seen. Would you mind posting your conky script? I understand that your conky has to work in tandem with KWin, but I might try to switch over, or at least to a Kubuntu desktop.

Many thanks.

---

### Post by vasa1 on 2018-02-21
Here it is:```
-- vim: ts=4 sw=4 noet ai cindent syntax=lua
--[[
# Conky, a system monitor, based on torsmo
# left out ${memperc}
]]

conky.config = {
alignment = 'top_left',
background = true, --was false true seems to work
default_color = '888888',
double_buffer = true,
draw_shades = false,
extra_newline = false,
font = 'Cousine:size=11.6',
gap_x = 0,
gap_y = 11,
minimum_width = 400,
minimum_height = 17,
out_to_console = false,
out_to_stderr = false,
own_window_class = 'Conky',
own_window_hints = 'undecorated,above,sticky,skip_pager',--dont use below
own_window = true,
own_window_argb_visual = true,
own_window_argb_value = 254,
own_window_colour = '252525',
own_window_type = 'normal',
own_window_transparent = false,
short_units = true,
text_buffer_size = 256,
update_interval = 2.0,
uppercase = false,
use_spacer = 'right',
use_xft = true
}

conky.text = [[${time %a %d %b} ${color 058188}${time %H:%M}$color ${utime %H:%M} ${tztime America/New_York %H:%M} ${execpi 360 bash curl-aes}|${execpi 300 bash curl-neg} T${hwmon 2 temp 1}R${memperc} C${cpu cpu0}
]]

```The "0|0" is for checking my mail accounts.

---

### Post by jakfish on 2018-02-21
My gosh, that's it! You found the way! No matter where you put it, conky remains visible.
I'm able to get a visible conky without any jiggling of a windows manager, Mate Marco 18.3 or Xubuntu 16.04.

One question about your script: is it possible to stop conky from showing its window on the taskbar/panel, or is that part of the trade-off?

Thank you, thank you.

---

### Post by vasa1 on 2018-02-21
> **jakfish said:**
> ... is it possible to stop conky from showing its window on the taskbar/panel, or is that part of the trade-off?
...
I don't know what you mean. You can position a conky window wherever you want. In XFCE, I think you can reduce the width of the panel to accommodate the conky window ([https://ubuntuforums.org/showthread.php?t=2199804&p=12901688#post12901688](https://ubuntuforums.org/showthread.php?t=2199804&p=12901688#post12901688)).

---

### Post by jakfish on 2018-02-21
I was not clear, I apologize. What I was trying to say is: with your script, conky runs where it's supposed to, but it does have a minimized window on the taskbar. I was wondering if there was a way to remove that minimized window and simply have conky across any window. But conky may have to be its own window, hence its icon display in the bar along with the icons of any other minimized program.

---

### Post by jakfish on 2018-02-21
I think I solved that issue, along with the issue of losing conky with "show desktop" command--change "normal" to "dock"

Pic is worth a thousand words: [https://imgur.com/a/JxV3M](https://imgur.com/a/JxV3M)

Thanks again for your help.

---

### Post by again? on 2018-02-21
> **jakfish said:**
> I think I solved that issue, along with the issue of losing conky with "show desktop" command--change "normal" to "dock"

Pic is worth a thousand words: [https://imgur.com/a/JxV3M](https://imgur.com/a/JxV3M)

Thanks again for your help.
"own_window_type = **normal**" observes "own_window_hints" so if using vasa1's config you need to add
**skip_taskbar** to "own_window_hints"

Depending on your window manager "own_window_type = dock" may work just as effectively.

---

### Post by jakfish on 2018-02-22
Thanks, I hadn't known that. Will check the difference between "dock," "normal," and "skip_taskbar"

---

### Post by again? on 2018-02-22
> **jakfish said:**
> Thanks, I hadn't known that. Will check the difference between "dock," "normal," and "skip_taskbar"
If conky is running when you edit, after saving the config use this command in another terminal to reload.
```
killall -SIGUSR1 conky
```
The command reloads any currently running instances of conky.
You could also bind the command to a shortcut key while testing different config settings.

---

### Post by jakfish on 2018-02-22
I've never used the [FONT=Ubuntu Mono, monospace][COLOR=#000000]-SIGUSR1 [/COLOR][/FONT] command. Usually, conky will incorporate user changes simply after .conkyrc is saved, but now always. Good to know a more permanent approach.

---

