---
title: "conky loads over taskbar"
date: 2010-01-09
forum: Desktop Environments
---

### Post by 3948ctyj on 2010-01-09
dont want conky over my bottom taskbar...here is the code... how to make it load UNDER the taskbar..??


on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer ye

---

### Post by JECHO on 2010-01-09
> **3948ctyj said:**
> dont want conky over my bottom taskbar...here is the code... how to make it load UNDER the taskbar..??


on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer ye

Try this:

```

# Create own window instead of using desktop (requigold in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (golduces flicker, may not work for everyone)
double_buffer yes

```

Or just change the height/width of your config file from the edges of the screen with this:

```
# Gap between borders of screen and text
gap_x 15
gap_y 30
```

---

### Post by 3948ctyj on 2010-01-09
the code didnt do anything but the height did.... its loading UNDER the bottom bar now but the bottom of the conky is out of sight... I suppose I could raise it more....  man, conky is a pain...no wonder I never messed with it... but still looking for a conky that shows volt/amps ... maybe Toshibas dont do that ...but I remeber
some app that did in 8.04.... now I am 9.04

---

