---
title: "Conky glitchy background"
date: 2014-08-13
forum: Desktop Environments
---

### Post by connorschwing on 2014-08-13
I'm at the point where I want to reinstall windows. Then shoot my computer, blow it up, pee on it, then become amish.


I'm running Ubuntu 14.04, the Gnome version (GNOME 3.12.2
Conky on almost any setting, looks like this
[http://i.imgur.com/LSz91q1.jpg](http://i.imgur.com/LSz91q1.jpg)
Or some variation of that glitchy, distorted background.



I try setting the thing to override, and conky doesn't even show up. I want it so there's no border. Just the grey and orange window.
Here's the relevant parts of the config

# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 100
gap_y 70
minimum_size 268 620
maximum_width 268
own_window yes
own_window_type normal # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment middle_middle
#own_window_argb_visual yes
#own_window_argb_value 0

---

### Post by CantankRus on 2014-08-13
Using gedit, save this config to your home folder as **democonky**
```
# Conky settings #
use_xft yes
xftfont ubuntu:size=10

background no
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 10
gap_y 40
alignment tr
minimum_size 268 620
maximum_width 268
own_window yes
own_window_type normal # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment middle_middle
#own_window_argb_visual yes
#own_window_argb_value 0

TEXT
${font ubuntu:bold:size=18}${alignc}This is a test
```

Then in the terminal run
```
conky -c ~/democonky
```

You should see similar to attachment in the top right of your desktop

---

### Post by connorschwing on 2014-08-14
It says "this is a test" with a large rectangle filled with distorted white bars (similar to the ones in my original image)

---

### Post by CantankRus on 2014-08-14
Then it appears to be a gfx or window manager issue not a conky config problem.

What gfx drivers are you using?
Are you using Ubuntu GNOME or unity?

Could be a problem with transparency.
Does your original conky need to be transparent?
Try using...
```
own_window_transparent **no**
```

---

### Post by connorschwing on 2014-08-14
I'm using Gnome 3.12.2, and I am on a laptop using an A6 APU with Radeon HD 6520G graphics. I haven't downloaded any drivers for it, as I have no idea how to on ubuntu

---

### Post by CantankRus on 2014-08-14
Install wmctrl to easily determine your window manager.
```
sudo apt-get install wmctrl
```

Then what's your output from
```
echo $DESKTOP_SESSION && wmctrl -m
```

---

### Post by connorschwing on 2014-08-14
I just installed all my GPU drivers and it works great, but theres this giant black bezel around the conky box. I change the window to override, and the whole conky disappears.

---

### Post by CantankRus on 2014-08-14
Check the gfx driver in use
```
lspci -nnk | grep -iA2 vga
```

and try the democonky config again.
```
conky -c ~/democonky
```

Also would like to know what window manager is running...
```
wmctrl -m
```

---

### Post by connorschwing on 2014-08-14
cschwing@PC:~$ lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647]
    Subsystem: Hewlett-Packard Company Device [103c:169b]
    Kernel driver in use: fglrx_pci

cschwing@PC:~$ wmctrl -m
Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
cschwing@PC:~$

---

### Post by connorschwing on 2014-08-14
I DID IT!!!!!!!!!!!!!
IT'S BEEN 8 HOURS. FINALLY, ALL I HAD TO DO WAS GO INTO TWEAK TOOL > DESKTOP, THEN ENABLE ICONS FOR DESKTOP AND THE BLACK BOX IS GONE.

Thank you to CantankRus for helping me through the driver install

---

### Post by CantankRus on 2014-08-14
Your original conky looks like it uses images to draw the conky box within 
a transparent conky window.
Due to your current window manager settings or your gfx driver not handling the transparency properly you're seeing glitches.
So one test would be to try a session with a different window manager.
 
I don't have gnome-shell installed to test how conky behaves.
What you can do is install gnome-session-flashback and the at the login screen choose **Gnome Flashback(Metacity)**.
See if you have the same transparency glitches when in this session and metacity is the window manager.

---

### Post by CantankRus on 2014-08-14
> **connorschwing said:**
> I DID IT!!!!!!!!!!!!!
IT'S BEEN 8 HOURS. FINALLY, ALL I HAD TO DO WAS GO INTO TWEAK TOOL > DESKTOP, THEN ENABLE ICONS FOR DESKTOP AND THE BLACK BOX IS GONE.

Thank you to CantankRus for helping me through the driver install

Good. :KS
Hope you gained a bit of info for any further trouble shooting.
I would say the open source drivers were ok ... just needed the file manager to handle the desktop.

---

