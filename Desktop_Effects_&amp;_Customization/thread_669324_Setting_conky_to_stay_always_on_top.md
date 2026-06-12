---
title: "Setting conky to stay always on top"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by mik01aj on 2008-01-16
It's my first post here so hello everyone :)

I searched the forums and all I found was a topic with people asking how to set conky below all windows. And what I want to do is to set conky above everything, even above the panels.... is there a way to achieve this?

My wm is metacity. Here is the interesting part form my .conkyrc file:
```
# set to yes if you want Conky to be forked in the background
background no

use_xft yes
xftfont Terminus:size=7.5
xftalpha 1

update_interval 1.0
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type override
own_window_type desktop
own_window_transparent 1
own_window_hints undecorated,below,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
```

Thanks in advance ;)

---

### Post by firedrow on 2008-01-16
I don't know, but would the own_window_hints have to do with something like that?  It is the only line in your config that says "below".  I would have to check Conky documentation, but that would be the first thing I look at.  Or take what people are saying to make it lower than all windows, and find the opposite config options of what they say.

---

### Post by mik01aj on 2008-01-17
I found a solution (thanks to guys from the #conky channel), but it's not working the way I expected.
to have conky as a floating window I just needed to modify the following line of .conkyrc:
```
own_window_type normal
own_window_hints undecorated,skip_taskbar
```
And then I can set it always on top just like any other window in metacity.

The next problem is that I can't place it over a panel, because metacity treats the panels as space off the screen when moving windows, so there is always about 30px gap between the panel edge and the end of conky window (I can post a screenshot if you want).

P.S. Would [this](http://library.n0i.net/linux-unix/applications/x/gnome/panel/statusdocklet.html) be useful to embed conky in a panel?

---

### Post by firedrow on 2008-01-17
I would say that your PS would be a very good option for embedding it into a panel.  From the way that page reads, that is exactly what you are wanting it to do.

---

### Post by mik01aj on 2008-01-19
I read this page, and it says that> The status docklet will embed a 22 by 22 window inside the panel...so I suppose it won't be useful.

In fact, all I want to achieve is to don't get conky covered by maximized windows. I added a panel near conky, and now maximized windows don't cover it, but it just doesn't look too well (how to add a panel without handles?). My goal is to make my panoramic laptop display more usable - I'm trying to get rid of horizontal panels and replace them with vertical ones. And I use conky, because it shows a lot of useful information. If I just could use it like a panel, it would be great :)

I'm now thinking of another way to do that - is it possible to trick metacity to leave some space near the screen edges when maximizing windows?

---

